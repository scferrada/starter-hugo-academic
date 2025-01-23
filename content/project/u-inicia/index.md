---
title: Desarrollo de Procesos de Inteligencia Artificial en Bases de Datos de Grafos
summary: Proyecto U-Inicia, financiado por la Vicerrectoría de Investigación y Desarrollo de la U. de Chile.
tags:
  - Machine Learning
  - Graph Databases
date: '2024-10-27T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

#links:
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---

El objetivo de este proyecto es definir procesos de IA como operadores de las bases de datos de grafo, tanto de manera lógica como física. La definición de operadores lógicos implica agregar procesos de IA al álgebra de los lenguajes de consulta, definir su semántica, sus propiedades algebraicas y su interacción con los otros operadores del lenguaje para su compatibilidad y optimización. La definición de operares físicos implica el diseño y análisis de los algoritmos que implementan las operaciones lógicas, de manera que se ejecuten de forma eficiente y efectiva sobre datos masivos que se encuentran almacenados en memoria secundaria (disco).

De este proyecto se desprenden los siguientes temas de tesis y memoria, que cuentan con financiamiento, tanto mensual, como financiamiento de viaje en caso de que la tesis culmine con una publicación de conferencia.

- [Tesis] **Cálculo de Embeddings de Grafos dentro de un Sistema Gestor de Bases de Datos**: Esta tesis busca definir el proceso de entrenamiento de una red neuronal de grafos (GNN) en función de operaciones de bases de datos, con el objetivo de lograr calcular embeddings de grafo sobre datos masivos almacenados en memoria secundaria. Este proceso de cálculo y entrenamiento posibilitará a los usuarios de un sistema gestor de bases de datos de grafos, definir de manera simple y declarativa, a través de una consulta, cómo desea entrenar/calcular embeddings sobre un grafo dado (o parte de él, a definir en la consulta.

- [Memoria] **Implementación de un módulo de entrenamiento de message-passing neural networks en un gestor de bases de datos de grafo**: Para apoyar la tesis anterior, se requiere la ejecución de una memoria en donde se implemente un módulo de entrenamiento de MPNNs optimizada para funcionar en disco duro. Esta implementación se realizará en un sistema gestor de bases de datos de grafo de código abierto.

- [Tesis] **Definición e Implementación de Operaciones por Similitud en Sistemas Gestores de Grafos de Propiedades**: De este tema se pueden extraer dos sub-temas, los cuales puede ser cada uno una tesis distinta. La idea general es extender el estándar GQL con operaciones por similitud, tal como se hizo previamente para SPARQL. Hay que definir las operaciones lógicas, indicar cómo se comportan con las operaciones ya existentes y posibles propiedades interesantes desde el punto de vista de la optimización. Luego se deben implementar operadores físicos que ejecuten la operación lógica de manera eficiente. El sub-tema que aparece aquí es la evaluación combinada de la búsqueda de patrones de grafos con la búsqueda por similitud. En este segundo tema, se espera que el estudiante diseñe y proponga algoritmos y/o estructuras de datos para mejorar la ejecución de este tipo de consultas, las cuales son cruciales para grafos multimedia (con embeddings de contenido) y para sistemas RAG basados en grafos.

- [Memoria] **Implementación de algortimos de operaciones por similitud en sistemas gestores de bases de datos**: Esta memoria busca extender algún sistema gestor de bases de datos de código abierto (e.g., PostgreSQL) para soportar operaciones de búsqueda y agrupamiento por similitud y evaluar su comportamiento, detectando potenciales avenidas de optimización.

- [Memoria] **Desarrollo de una Tensor-store para Apache Jena**: En trabajo previo definimos operaciones de búsqueda por similitud y clústering de vectores en Apache Jena. En esa ocasión, los vectores se generaban *on the fly* con datos extraídos por la propia consulta. Sin embargo, hay grafos de conocimiento multimedia que desean publicar vectores/embeddings pre-calculados y actualmente no existen muchas alternativas de GDBMS con Tensor stores para RDF. Esta tesis busca extender Apache Jena con una Tensor store para poder ejecutar nativamente consultas que contengan criterios de similitud y para facilitar el proceso de publicación de grafos multimedia.