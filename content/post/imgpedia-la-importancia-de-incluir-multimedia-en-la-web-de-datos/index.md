---
title: IMGpedia, la importancia de incluir multimedia en la Web de Datos
date: 2023-07-05T21:34:58.892Z
draft: false
featured: false
authors:
  - admin
tags:
  - IMGpedia
projects:
  - IMGpedia
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---
IMGpedia es una base de datos enlazados que extrae características visuales a las imágenes de Wikimedia Commons y que provee enlaces a DBpedia al contexto de la imagen, permitiendo así realizar consultas visuo-semánticas. IMGpedia fue mi tesis de magíster guiada por Benjamin Bustos y Aidan Hogan. Muy probablemente será mi tesis de doctorado también.
En este post les voy a contar de qué se trata IMGpedia y mi experiencia compartiendo este trabajo en <a href="https://iswc2017.semanticweb.org" target="_blank" rel="noopener">ISWC 2017</a> en Viena, Austria.

La idea que motiva el trabajo es incluir fuertemente el análisis de contenido multimedia en la Web de Datos, tomando en cuenta que la información multimedia es parte fundamental para la experiencia de los usuarios en la Web. IMGpedia nos permitiría poder hacer consultas de similitud visual entre imágenes, obtener imágenes que cumplan un cierto predicado
y mezclar ambos enfoques, lo que llamamos una consulta <em>visuo-semántica</em>. Por ejemplo, nos permitiría responder la siguiente consulta: <em>dada una imagen de la catedral de Cusco, obtener imágenes similares de catedrales europeas</em>.

Para lograr el objetivo, debemos seguir la siguiente metodología:
- Obtener las imágenes para procesarlas localmente.
- Calcular los descriptores visuales (vectores de características) de las imágenes.
- Obtener estáticamente relaciones de similitud entre las imágenes.
- Enlazar las imágenes con otras fuentes de información (<a href="http://dbpedia.org" target="_blank" rel="noopener">DBpedia</a>, <a href="https://www.wikidata.org" target="_blank" rel="noopener">Wikidata</a>, <a href="http://freebase.com" target="_blank" rel="noopener">Freebase</a>).
- Publicar todo como RDF, a través de un terminal SPARQL.

Descargar los 14,7 millones de imágenes nos tomó 40 días con múltiples conexiones. El tamaño total de las imágenes es de 22 Terabytes. Una vez descargadas, calculamos los descriptores visuales, en particular calculamos histogramas de grises, histogramas de la orientación de los bordes y un descriptor basado en color. Puedes encontrar más detalles sobre los descriptores y código visitando el <a href="https://github.com/scferrada/imgpedia" target="_blank" rel="noopener">GitHub</a> del proyecto (en inglés).

Como se puede ver en la Figura 1, nuestro objetivo es enlazar las imágenes que sean visualmente similares. Para hacer esto, tomamos un descriptor y encontramos sus 10 vecinos más cercanos, pues asumimos que si dos vectores están cerca, es por que son similares. Esta decisión de tomar los <em>k</em> vecinos más cercanos ha generado mucha discusión, pero si están interesados, hay una reflexión al respecto al final del post.

<img src="/img/similarity.PNG" alt="Figura 1: Similitud entre imágenes" width="90%"/>
<center><strong>Figura 1:</strong> Similitud entre imágenes</center>

Luego, necesitamos obtener contexto de la imagen: saber qué es, cómo se llama lo que aparece en ella o con qué está relacionada. Para esto, usamos un <a href="https://dumps.wikimedia.org/" target="_blank" rel="noopener">dump</a> de la Wikipedia en inglés para reunir los pares <code>(nombre_img, nombre_wiki)</code> de modo que la imagen aparece en la wiki. Entonces enlazamos la imagen con el recurso de DBpedia relacionado al articulo de Wikipedia correspondiente. Por ahora, nada nos asegura que la imagen realmente contenga a la entidad con la que está relacionada, pero sí podemos decir que la imagen está asociada a la entidad de alguna forma u otra. En la Figura 2 se muestra lo que se pretende hacer, por ejemplo si una imagen aparece en la <a href="http://en.wikipedia.org/wiki/Quentin_Tarantino" target="_blank" rel="noopener">wiki de Quentin Tarantino</a>, entonces enlazamos la imagen con el <a href="http://dbpedia.org/resource/Quentin_Tarantino" target="_blank" rel="noopener">recurso de Tarantino en DBpedia</a>.

<img src="/img/context.PNG" alt="Figura 2: Obtener contexto de la imagen" width="90%"/>
<center><strong>Figura 2:</strong> Obtener contexto de la imagen</center>

Finalmente, publicamos todo en formato <a href="https://www.w3.org/2001/sw/wiki/RDF" target="_blank" rel="noopener">RDF</a> que puede ser consultado a través de un terminal público de <a href="https://www.w3.org/TR/sparql11-query/" target="_blank" rel="noopener">SPARQL</a>. Los datos tienen un cierto esquema para modelar clases y atributos que puede ser encontrado <a href="http://imgpedia.dcc.uchile.cl/ontology" target="_blank" rel="noopener">aquí</a>. En <a href="http://imgpedia.dcc.uchile.cl/sparql" target="_blank" rel="noopener">este terminal</a>, podemos hacer por ejemplo las siguientes consultas:

- Obtener todas las imágenes similares a la foto de Hopsten Marktplatz:

<pre tabindex="0"><code>SELECT DISTINCT ?Target
WHERE {
    im:Hopsten_Marktplatz_3.jpg imo:similar ?Target .
}
</code></pre>
<img src="/img/q1.PNG" alt="Figura 3: Resultados de la consulta a" width="90%"/>
<center><strong>Figura 3:</strong> Resultados de la consulta a</center>

- Obtener imágenes de las pinturas hechas el siglo XVI, que están en exposición en el Louvre (ojo que también podemos obtener otros datos como el nombre de la pintura, quién la pintó, etc.):

<pre tabindex="0"><code>SELECT DISTINCT ?url ?label
WHERE {
  SERVICE &lt;https://dbpedia.org/sparql&gt; {
    ?res a yago:Wikicat16th-centuryPaintings ;
      dcterms:subject dbc:Paintings_of_the_Louvre ;
      rdfs:label ?label .
    FILTER(LANG(?label)=&#34;en&#34;)  }
  ?img imo:associatedWith ?res ;
      imo:fileURL ?url .  
}
</code></pre>
<img src="/img/q2.PNG" alt="Figura 4: Resultados de la consulta b" width="90%"/>
<center><strong>Figura 4:</strong> Resultados de la consulta b</center>

- Finalmente podemos combinar ambos tipos de preguntas en una consulta que llamamos <em>visuo-semántica</em>, por ejemplo entre todas las imágenes de catedrales europeas, obtener imágenes similares que sean museos:

<pre tabindex="0"><code>SELECT DISTINCT ?source ?target
WHERE {
  SERVICE &lt;https://dbpedia.org/sparql&gt; {
    ?sres dcterms:subject/skos:broader* dbc:Roman_Catholic_cathedrals_in_Europe } 
  ?source imo:associatedWith ?sres ;
          imo:similar ?target .
  ?target imo:associatedWith ?tres ;
          imo:fileURL ?urlt .
  SERVICE &lt;https://dbpedia.org/sparql&gt; {
    ?tres dcterms:subject ?subject .
    FILTER(CONTAINS(STR(?sub), “Museum”))} 
}
</code></pre>
<img src="/img/q3.PNG" alt="Figura 5: Resultados de la consulta c" width="90%"/>
<center><strong>Figura 5:</strong> Resultados de la consulta c</center>

Tras mi defensa del Magister, este trabajo fue aceptado en el track de recursos de la 16ta Conferencia Internacional de la Web Semántica (ISWC) y viajé a Viena a presentarlo, puedes encontrar las diapositivas <a href="/pptx/iswc2017.pptx">aquí</a>. También participamos en la sesión de pósters, donde recibimos feedback y preguntas muy interesantes, puedes ver el póster <a href="/pdf/imgpediaISWCposter.pdf">aquí</a>. Tanto la presentación como la sesión de pósters fueron una gran oportunidad para validar nuestro trabajo, para saber cómo mejorarlo y para saber qué cree la comunidad que sería útil agregar. En resumen, dejo algunos puntos:

- Redes Neuronales: el 90% de las personas que pasaron por mi póster me dijeron que no podían faltar. Ya sea para clasificar el contenido, como para obtener otros descriptores visuales o incluso para predecir triples con hechos sobre las imágenes.
- Consultas por rango: muchos, al igual que yo, notan que el tener <em>k</em> vecinos más cercanos por imagen es bastante restrictivo: hay relaciones interesantes que se pierden y forzamos a otras imágenes a ser similares a <em>k</em> otras. Sin embargo, hacerlo de esta forma en la primera versión nos ayudó a comprender cómo se comporta la distribución de distancias entre imágenes similares, por lo que podemos proponer un umbral más ajustado en una próxima versión.
- Enlazar a otas bases de conocimiento: DBpedia es una fuente de información muy útil, pero ha resultado ser poco flexible para nuestros propósitos. Muchos piensan que enlazar con otras bases de conocimiento como Wikidata o Yago, puede enriquecer y darle mayor expresividad a las consultas de IMGpedia.

¡Gracias a todos los que nos fueron a ver al stand!

<img src="/img/posteriswc17.jpg" alt="Figura 6: Sesión de pósters" width="90%"/>
<center><strong>Figura 6:</strong> Sesión de pósters</center>

Para terminar con esta historia, el último día de conferencia anuncian a los ganadores de los mejores papers publicados en la conferencia. ¡<a href="https://iswc2017.semanticweb.org/program/awards/" target="_blank" rel="noopener">IMGpedia ganó dos premios</a>! Ganamos el premio al mejor póster y el premio al mejor paper de estudiante en el track de recursos (junto con BiOnIC). Este reconocimiento significa mucho para mi y para mi carrera de científico, ¡vaya forma de comenzar! Y más aún, porque los otros nominados son varios estudiantes de doctorado de centros y universidades reconocidos a nivel mundial, como la Universidad de Standford. Más aún cuando mi trabajo es una tesis de magíster, es increíble que haya competido contra otros trabajos de tan alto nivel. Además este premio, como el <a href="https://iswc2017.semanticweb.org/paper-359/" target="_blank" rel="noopener">mejor paper de estudiantes del track de investigación de ISWC</a> es un claro mensaje de que
tenemos que seguir trabajando en multimedia, no podemos seguir dejando estos datos de lado.
Ahora queda seguir trabajando y mejorando IMGpedia, para que se convierta en la base de conocimiento estándar para las imágenes de la Web.

Quiero destacar también el nivel de ciencia que se desarrolla en los institutos y centros de investigación chilenos financiados por la <a href="http://www.iniciativamilenio.cl/en/home/" target="_blank" rel="noopener">Iniciativa Científica Milenio</a>, en particular en el Núcleo Milenio <a href="http://ciws.cl" target="_blank" rel="noopener">Centro
de investigación de la Web Semántica</a>, que en total nos llevamos 3 premios en ISWC (los dos de IMGpedia y el premio a mejor paper de investigación para Jorge Pérez).

<img src="/img/awards.jpg" alt="Figura 7: Aidan y yo recibiendo el premio a mejor paper de estudiante" width="90%"/>
<center><strong>Figura 7:</strong> Aidan y yo recibiendo el premio a mejor paper de estudiante</center>

Solo me falta agradecer a todos los que hicieron este (arduo) trabajo posible, en especial a mis profesores guía, Benjamin y Aidan; a Sergio Aguilera por ayudarme tanto con la mantención del servidor; a Camila Faúndez por el trabajo enlazando las imágenes a sus respectivos artículos; al Núcleo Milenio <a href="http://ciws.cl" target="_blank" rel="noopener">Centro de Investigación de la Web Semántica</a>, por su apoyo financiero y académico; y a toda mi familia y amigos por su constante apoyo, motivación y cariño.
<hr>
<em>Sobre los 10 vecinos más cercanos</em>: Es cierto que al tomar esta decisión suceden dos cosas indeseables. Primero, es posible que se pierdan relaciones de similitud relevantes, es decir que el 11mo, 12mo, etc. sean muy similares también. Segundo,
estamos forzando que si hay imágenes que no se parecen a nada, se parezcan a al menos 10. La justificación detrás de esta decisión tiene dos partes. Por un lado lo que pretendemos es mantener una cantidad acotada de triples RDF, después de todo, esta es la primera versión de IMGpedia y necesitábamos probar el concepto primero. Por otro lado, tener estas relaciones de los 10 vecinos más cercanos y sus distancias en los diferentes espacios vectoriales nos dan una visión más amplia sobre la distribuciónde las distancias, permitiéndonos en el futuro utilizar una consulta por rango, utilizando estrategias de indexamiento y un umbral de distancia apropiado para cada descriptor.