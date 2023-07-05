---
title: Formas Pokenormales
date: 2023-07-05T21:21:39.454Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Al diseñar las relaciones que deben formar parte de un esquema relacional de bases de datos hay ciertos aspectos que se deben considerar de forma que se asegure que al agregar los datos en el esquema estos no presenten anomalías. En este artículo, voy a discutir distintas anomalías que pueden presentarse en esquemas relacionales y cómo pueden ser erradicados utilizando formas normales. Las formas normales son condiciones
que todas las tablas de un esquema deben cumplir para así garantizar ciertas propiedades deseables. Las formas normales fueron propuestas principalmente por Edgar F. Codd durante los 70s.

Para entender de mejor forma las condiciones que se requieren en cada forma normal, es recomendable que conozcas lo que es una llave y una dependencia funcional en el modelo relacional. En <a href="/post/llaves-dependencias-funcionales/">este post</a> puedes encontrar definiciones y ejemplos también.

Vamos a guiar la explicación a través de una base de datos que mantiene el registro de los Pokémon que son capturados por los distintos entrenadores. En la Tabla 1, se muestra una forma sobre cómo organizar nuestros datos. La tabla contiene una columna con el identificador del entrenador y la segunda contiene una lista con las criaturas capturadas por dicho entrenador. La llave de la tabla es el nombre del entrenador por lo que se muestra en negrita y cursiva.

<center>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th>Pokemon</th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>\[Pikachu, Caterpie, Charmander, &hellip;]</td>
</tr>
<tr>
<td>Misty</td>
<td>\[Staryu, Goldeen, Starmie, &hellip;]</td>
</tr>
<tr>
<td>Gary</td>
<td>\[Krabby, Nidoking, Arcanine, &hellip;]</td>
</tr>
</tbody>
</table>
</center>
<center><b>Tabla 1</b>: Entrenadores y sus Pokémon </center>

Como se puede adivinar, es al menos extraño el manejar listas de elementos en una base de datos relacional. El utilizar ese tipo de estructuras en un atributo de una tabla puede producir dificultades al momento de implementar la base de datos. ¿Las colecciones pueden tener un tamaño máximo? ¿Cómo busco, agrego, ordeno o elimino eficientemente un elemento de la colección?

¿Cómo se puede solucionar? La solución más ingenua, podría ser agregar más columnas, una para cada Pokémon atrapado. Esto supone nuevos problemas: ¿Cuántas columnas son suficientes? ¿Qué pasa con las columnas que no son utilizadas? ¿Cómo saber en cuál columna agregar la captura?

Por lo general, la solución a este tipo de problemas es utilizar las llaves de ambas entidades relacionadas. En el caso del ejemplo, serían tanto el nombre del entrenador como el del Pokémon. El resultado puede apreciarse en la Tabla 2. Como un entrenador puede tener varios Pokémon tanto el nombre del entrenador como el nombre del Pokémon son la llave de la tabla. (Efectivamente esto restringe que un mismo entrenador capture dos pokémon del mismo nombre. ¿Cómo solucionar esto?)

<center>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th><em><strong>Pokemon</strong></em></th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>Pikachu</td>
</tr>
<tr>
<td>Ash</td>
<td>Caterpie</td>
</tr>
<tr>
<td>Ash</td>
<td>Charmander</td>
</tr>
<tr>
<td>Misty</td>
<td>Staryu</td>
</tr>
<tr>
<td>&hellip;</td>
<td>&hellip;</td>
</tr>
</tbody>
</table>
</center>
<center><b>Tabla 2:</b> Entrenadores y sus Pokémon, un valor por celda </center>

Cuando tenemos una relación como la de la Tabla 2, decimos que cada atributo tiene valores atómicos, es decir, valores que no son colecciones (conjuntos, listas, etc.). Este tipo de relaciones están en **Primera Forma Normal**.

Supongamos que ahora que tenemos más información sobre el entrenador, sobre el Pokémon capturado y sobre la captura en sí. Por ejemplo, queremos almacenar la ciudad de la que el entrenador proviene, la salud y tipo del Pokémon capturado y la fecha y hora de la captura. Si seguimos con lo que veníamos haciendo en la Tabla 2, podríamos proponer un esquema como el que se ve en la Tabla 3. Podemos ver que la llave sigue siendo el nombre del entrenador y el del pokémon, sin embargo, al agregar también la fecha de captura a la llave podemos admitir que un entrenador capture más de un pokémon de la misma especie en momentos diferentes.

<center>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th>Origen</th>
<th><em><strong>Pokemon</strong></em></th>
<th>Tipo</th>
<th>HP</th>
<th><em><strong>Fecha Captura</strong></em></th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>Pueblo Paleta</td>
<td>Pikachu</td>
<td>Eléctico</td>
<td>35</td>
<td>01-04-1997 10:20</td>
</tr>
<tr>
<td>Ash</td>
<td>Pueblo Paleta</td>
<td>Caterpie</td>
<td>Insecto</td>
<td>45</td>
<td>02-04-1997 11:34</td>
</tr>
<tr>
<td>Ash</td>
<td>Pueblo Paleta</td>
<td>Charmander</td>
<td>Fuego</td>
<td>39</td>
<td>05-04-1997 19:12</td>
</tr>
<tr>
<td>Misty</td>
<td>Ciudad Celeste</td>
<td>Staryu</td>
<td>Agua</td>
<td>30</td>
<td>22-03-1995 09:44</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 3:</strong> Entrenadores y sus Pokémon, con datos del entrenador, Pokémon y captura</p>
</center>

En el modelo de la Tabla 3, podemos encontrar varios problemas. Primero notamos que hay redundancia, pues cada vez que un entrenador capture un nuevo pokémon debemos repetir su ciudad de origen. Esto conlleva varias anomalías consigo, las cuales vamos a enumerar:

- **Anomalía de Actualización:** Si quisieramos modificar la ciudad de origen de un entrenador debemos asegurarnos de cambiarla correctamente en todas las filas que se refieren al entrenador. El no hacerlo, lleva a un estado inconsistente de la base de datos.
- **Anomalía de Inserción:** No podemos agregar un nuevo entrenadoral sistema si es que no ha capturado ningún pokémon aún. Esto pues la columna pokémon es parte de la llave y por lo tanto no admite valores nulos. Lo mismo con un pokémon, no tendremos registro de la especie o el tipo si nadie lo ha capturado.
- **Anomalía de Borrado:** Si un entrenador decide liberar a todos sus pokémon capturados, ¿qué hacemos con él? ¿Borramos todos sus datos?

¿Cuál es el origen de estas anomalías? En este caso se debe a que hay atributos cuyo valor depende solo del entrenador. En este caso, la ciudad de origen depende del entrenador. Por otro lado, hay atributos que dependen solo del pokémon en cuestión, como el tipo. La salud del pokémon es un caso distinto, pues al contrario del tipo, no depende solo del pokemon del que se trata, sino que también depende del entrenador y de cuándo fue capturado<sup id="fnref:1"><a href="#fn:1" class="footnote-ref" role="doc-noteref">1</a></sup>.
Cuando se define una llave en una tabla, se espera que todos los atributos no-primos dependan de todos los atributos de la llave en conjunto, no solo de una parte de ésta. Eso es lo que en este caso produce las anomalías: hay atributos no primos que no dependen funcionalmente de la llave completa, sino que de un subconjunto (propio<sup id="fnref:2"><a href="#fn:2" class="footnote-ref" role="doc-noteref">2</a></sup>) de ésta.</p>

Entonces, la **Segunda Forma Normal** (2NF) indica que un esquema está en primera forma normal y además, ningún atributo no primo depende funcionalmente de algún subconjunto propio de alguna de las llaves candidatas. También puede leerse como que todos los atributos no primos deben depender funcionalmente de todas las llaves candidatas **completas**.

Nuestro esquema de Tabla 3 no cumple con la segunda forma normal. La única llave candidata (y por lo tanto la llave primaria) es *{Entrenador, Pokemon, Fecha}*
y tenemos las dependencias funcionales *Entrenador* $\rightarrow$ *Origen* y *Pokémon* $\rightarrow$ *Tipo* que violan 2NF pues *Entrenador* y *Pokemon* son subconjuntos propios de la llave primaria.

¿Cómo podemos lograr 2NF? En este caso en particular basta con tener una tabla para los entrenadores, otra para las especies de pokémon y otra para las capturas. En las tablas 4, 5 y 6 podemos encontrar el resultado de la normalización. Bastó en este caso con tomar las dependencias funcionales <em>Entrenador</em> $\rightarrow$ <em>Origen</em> y *Pokémon* $\rightarrow$ <em>Tipo</em> y extraerlas en tablas aparte. Finalmente,
se agrega la tabla de capturas.

<center>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th>Origen</th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>Pueblo Paleta</td>
</tr>
<tr>
<td>Misty</td>
<td>Ciudad Celeste</td>
</tr>
<tr>
<td>Gary</td>
<td>Pueblo Paleta</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 4:</strong> Entrenadores y sus ciudades de origen</p>
<table>
<thead>
<tr>
<th><em><strong>Pokemon</strong></em></th>
<th>tipo</th>
</tr>
</thead>
<tbody>
<tr>
<td>Pikachu</td>
<td>Eléctrico</td>
</tr>
<tr>
<td>Caterpie</td>
<td>Insecto</td>
</tr>
<tr>
<td>Staryu</td>
<td>Agua</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 5:</strong> Especies de pokémon y sus tipos</p>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th><em><strong>Pokemon</strong></em></th>
<th>HP</th>
<th><em><strong>Fecha Captura</strong></em></th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>Pikachu</td>
<td>35</td>
<td>01-04-1997 10:20</td>
</tr>
<tr>
<td>Ash</td>
<td>Caterpie</td>
<td>45</td>
<td>02-04-1997 11:34</td>
</tr>
<tr>
<td>Ash</td>
<td>Charmander</td>
<td>39</td>
<td>05-04-1997 19:12</td>
</tr>
<tr>
<td>Misty</td>
<td>Staryu</td>
<td>30</td>
<td>22-03-1995 09:44</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 6:</strong> Entrenadores y sus pokémon</p>
</center>

El conjunto de las tablas 4, 5 y 6 cumple ahora con 2NF. Supongamos ahora que además del pueblo de origen del entrenador, queremos también saber la región de la que provienen, como se ve en la Tabla 7. En dicha tabla, es fácil notar que se cumple la dependencia funcional
<em>Origen</em> $\rightarrow$ <em>Región</em>. La existencia de esta dependencia facilita la aparición de las anomalías que discutimos anteriormente. Por ejemplo, si queremos modificar el pueblo de origen, tenemos que tomar en cuenta que la región tal vez también debería cambiar. La naturaleza del problema es distinta a la anterior. Acá no hay una dependencia parcial a una llave, sino que hay atributos no primos determinando funcionalmente a otros.

<center>
<table>
<thead>
<tr>
<th><em><strong>Entrenador</strong></em></th>
<th>Origen</th>
<th>Región</th>
</tr>
</thead>
<tbody>
<tr>
<td>Ash</td>
<td>Pueblo Paleta</td>
<td>Kanto</td>
</tr>
<tr>
<td>Misty</td>
<td>Ciudad Celeste</td>
<td>Kanto</td>
</tr>
<tr>
<td>Gary</td>
<td>Pueblo Paleta</td>
<td>Kanto</td>
</tr>
<tr>
<td>Professor Kukui</td>
<td>Hau&rsquo;oli</td>
<td>Alola</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 7:</strong> Entrenadores y sus ciudades y regiones de origen</p>
</center>

La <strong>Tercera Forma Normal</strong> (3NF) nos permite eliminar este tipo de anomalías. Un esquema está en 3NF sí está en segunda forma normal y ningún atributo no primo depende transitivamente de una llave candidata. La última condición también puede expresarse como que todos los atributos están determidados funcionalmente solo por las llaves candidatas y no por atributos no primos. En el caso de la Tabla 7 tenemos la Región depende transitivamente de la llave: <em>Entrenador</em> $\rightarrow$ <em>Origen</em> $\rightarrow$ <em>Región</em>, por lo tanto nuestra tabla no está en 3NF.</p>
<p>Para normalizar una tabla que no está en 3NF, se puede utilizar el siguiente algoritmo (aunque en la mayoría de los casos solo basta usar el sentido común):</p>

<pre tabindex="0"><code>INPUT: (R, F) R un esquema y F un conjunto de relaciones funcionales
OUTPUT: El esquema normalizado
F` := reducir(F)
por cada X-&gt;A en F`:
	Crear esquema (X U A, X-&gt;A)
Si en los esquemas creados no está la llave de (R, F), agregarla	
</code></pre>

En reducir, lo que se hace es eliminar dependencias funcionales redundantes y dejarlas de la forma $X \rightarrow A$ donde A es el conjunto de todos los atributos que dependen funcionalmente de X. Finalmente, se agrega la llave en caso de ser necesario. En nuestro ejemplo, las dependencias funcionales son (1) <em>Entrenador</em> $\rightarrow$ <em>Origen</em>, (2) <em>Entrenador</em> $\rightarrow$ <em>Región</em> y (3) <em>Origen</em> $\rightarrow$ <em>Región</em>, entonces las tablas resultantes van a ser (Entrenador, Origen) y (Origen, Región) pues la (2), al ser transitiva de (1) y (3) se elimina. No es necesario agregar una tabla para la llave pues es simplemente Entrenador. La primera tabla puede apreciarse en Tabla 4 y la segunda en Tabla 8.

<center>
<table>
<thead>
<tr>
<th><em><strong>Pueblo</strong></em></th>
<th>Región</th>
</tr>
</thead>
<tbody>
<tr>
<td>Pueblo Paleta</td>
<td>Kanto</td>
</tr>
<tr>
<td>Ciudad Celeste</td>
<td>Kanto</td>
</tr>
<tr>
<td>Hau&rsquo;oli</td>
<td>Alola</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 8:</strong> Pueblos y las regiones a las que pertenecen</p>
</center>

¿Estamos listos entonces? Falta un poco, aunque muchas veces se considera que un esquema en 3NF está lo suficientemente normalizado, aún hay ciertas cosas que pueden surgir.

Supongamos ahora una tabla para guardar los duelos contra líderes de gimnasio. Vamos a suponer que un gimnasio puede tener solo un líder y que ese líder pertenece solo a un gimnasio. Podemos ver datos de ejemplo en la Tabla 9.

<center>
<table>
<thead>
<tr>
<th>Lider</th>
<th>Entrenador</th>
<th>Gimnasio</th>
<th>Fecha</th>
<th>Ganador</th>
</tr>
</thead>
<tbody>
<tr>
<td>Brock</td>
<td>Ash</td>
<td>Ciudad Plateada</td>
<td>03-04-1997</td>
<td>Brock</td>
</tr>
<tr>
<td>Brock</td>
<td>Ash</td>
<td>Ciudad Plateada</td>
<td>04-04-1997</td>
<td>Nadie</td>
</tr>
<tr>
<td>Misty</td>
<td>Ash</td>
<td>Ciudad Celeste</td>
<td>18-04-1997</td>
<td>Empate</td>
</tr>
</tbody>
</table>
<p><strong>Tabla 9:</strong> Registro de duelos en gimnasios</p>
</center>

Podemos inferir que una llave es esta tabla es $\set{Lider, Entrenador, Fecha}$, pero dadas las dependencias funcionales {Lider}$\rightarrow${Gimnasio} y {Gimnasio}$\rightarrow${Lider} tenemos que otra llave candidata es {Entrenador, Gimnasio, Fecha}. Dadas las definiciones anteriores, la Tabla 9 está en 3FN. Sin embargo, aún
pueden surgir anomalías de edición: ¿Qué pasa si queremos cambiar el nombre del gimnasio? Es requerido cambiarlo en todas partes. ¿Entonces normalizar hasta 3NF no es suficiente? Pues hay una forma de normalización superior a 3NF que evita este tipo de problemas.</p>
<p>Un esquema está en <strong>Forma Normal de Boyce-Codd</strong> (FNBC) si para cada una de sus dependencias funcionales $X\rightarrow Y$, $X$ es una superllave. Así de simple. En la Tabla 9, vemos que las dependencias funcionales entre Lider y Gimnasio violan el principio de Boyce-Codd y esto es lo que produce las anomalías. En general es extraño encontrar tablas que estén en 3FN y no en FNBC. Esto sucede cuando en una tabla 3FN
existen llaves candidatas que se traslapan, es decir, que comparten atributos.

El algoritmo que se sigue para normalizar es el siguiente:

<pre tabindex="0"><code>Input: C ={(R0, F0)} # Esquema y dependencias iniciales
Output: N # Esquema normalizado en FNBC

for (R, F) in C:
	if (R, F) no está en FNBC:
		tomar X -&gt; Y en F que viola FNBC
		C = C U (R-X, F1) # F1 son las df sobre los atributos en R-X
		C = C U (XY, F2)  # F2 son las df sobre los atributos en XY
</code></pre>

Entonces en el caso de la Tabla 9, tomamos una de las dependencias que viola FNBC, {lider}$\rightarrow${gimnasio} y separamos el esquema en dos el primero con los atributos {lider, entrenador, fecha, ganador} y el otro con {lider, gimnasio}. Como ambas tablas resultantes quedaron en FNBC, el esquema ya está completamente normalizado.

Para cerrar, quiero mencionar dos cosas. La primera, es que existen la cuarta, quinta y sexta formas normales, las cuales tratan de reparar anomalías cada vez más difíciles de encontrar en el mundo real. La segunda, es que la existencia de estas reglas y definiciones para mejorar el diseño relacional se sugieren principalmente para evitar las anomalías, sin embargo, es posible que se esté desarrollando una aplicación donde hayan otros elementos que sean más críticos que la normalización de las tablas, por lo que no hay que ser puristas, sino que tomar en cuenta el dominio y requisitos de lo que se está haciendo antes de llegar y dejar todo en sexta forma normal. Hay escenarios en los que se prefiere tener redundancia para aumentar la eficiencia antes que tener que realizar joins entre miles de tablas. Hay escenarios en los que se prefiere lo contrario.

###Referencias
1. Codd, Edgar F. &ldquo;A relational model of data for large shared data banks.&rdquo; Communications of the ACM 13.6 (1970): 377-387.
2. Codd, Edgar F. &ldquo;Recent Investigations into Relational Data Base Systems.&rdquo; IBM Research Report RJ1385 (April 23, 1974).
3. Ramakrishnan, Raghu, and Johannes Gehrke. Database management systems. McGraw Hill, 2000.

<div class="footnotes" role="doc-endnotes">
<hr>
<ol>
<li id="fn:1">
<p>Esta diferencia ocurre pues un pokémon es una especie y una instancia a la vez: todos los Pikachu son eléctricos, pero cada uno tiene un HP distinto. La forma de diferenciar dos Pikachu distintos, es por el entrenador que los capturó.&#160;<a href="#fnref:1" class="footnote-backref" role="doc-backlink">&#x21a9;&#xfe0e;</a></p>
</li>
<li id="fn:2">
<p>Un subconjunto propio es un subconjunto con cardinalidad estrictamente menor que el conjunto original, es decir $R\subsetneq S$&#160;<a href="#fnref:2" class="footnote-backref" role="doc-backlink">&#x21a9;&#xfe0e;</a></p>
</li>
</ol>
</div>