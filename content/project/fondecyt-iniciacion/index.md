---
title: Knowledge Graph Extraction from Tabular Sources
summary: Fondecyt Iniciación 2025, financiado por ANID.
tags:
  - Graph Databases
  - Database Interoperability
  - Relational Databases
date: "2025-01-01T00:00:00Z"

# Optional external URL for project (replaces project detail page).
#external_link: https://example.org

image:
  caption: ''
  focal_point: Smart
---

En este proyecto Fondecyt se sentarán las bases para interpretar y explotar datos que están alojados en bases de datos relacionales como si fueran grafos de conocimiento. El proyecto no solo tiene como objetivo generar un mapeo físico y virtual de una base de datos relacional hacia un grafo de conocimiento, sino que también incluye estudiar cómo optimizar los sistemas gestores de bases de datos relacionales para que puedan, de manera eficiente, ejecutar consultas analíticas de manera nativa, como lo son el cálculo de caminos, conectividad, comunidades y centralidad.

El proyecto estará vigente hasta marzo de 2028 y contempla el desarrollo de las siguientes tesis de magister, las cuales contarán con financiamiento a acordar con cada estudiante. Todas las tesis pueden desembocar en una o más publicaciones, en donde la estudiante tendrá el apoyo financiero para viajar a presentar su propio trabajo.

Los temas a ejecutar son los siguientes:

- **Definición e implementación de operadores de similitud sobre GQL**: Esta tesis busca integrar operaciones basadas en similitud en el nuevo lenguaje estandar de consulta de grafos GQL. Se requiere extender la sintaxis y semántica del lenguaje para definir operadores físicos y lógicos de búsqueda por similitud, similarity join y clustering. Además se espera desarrollar heurísticas de optimización para consultas que utilicen dichos operadores.

- **Traducción Automática de Consultas GQL a SQL**:  Dada una función de mapeo de bases de datos relacionales a grafos de propiedades, este tema de tesis busca desarrollar un algoritmo correcto de traducción de consultas GQL intencionadas para el grafo de propiedades a consultas SQL equivalentes que se ejecuten directamente sobre la base de datos relacional. El algoritmo de traducción se espera que reconozca todas las posibilidades de optimizar la consulta de salida, tanto en términos de tiempo de ejecución, como de verbosidad. Primeramente, se espera traducir consultas que contengan patrones de grafos y algunos operadores relacionales.

- **Ejecución Eficiente de Consultas Navegacionales en SQL**: Una componente crucial que distingue las bases de datos de grafo de las relacionales, es la posibilidad de realizar consultas navegacionales sobre los datos (RPQs). Esta tesis busca recopilar la literatura actual e implementar y evaluar métodos para la evaluación eficiente de este tipo de consultas sobre un sistema gestor de bases de datos relacional de código libre.

- **Ejecución Eficiente de Consultas Analíticas de Grafos en SQL**: Esta tesis busca diseñar e implementar algoritmos eficientes para evaluar consultas analíticas de grafos en sistemas gestores de bases de datos relacionales. Las consultas analíticas incluyen la detección de comunidades, el cálculo de medidas de similitud, entre otras.

- **Diseño de Algoritmos Eficientes para Evaluar Consultas Recursivas en SQL y GQL**: La gran mayoría de las consultas de grafos requieren utilizar los operadores físicos que implementan la recursión en SQL. La recursión es reconocidamente ineficiente en todos los sistemas gestores de bases de datos. Esta tesis busca producir un benchmark de diferentes alternativas para ejecutar consultas recursivas y determinar en qué casos es más conveniente utilizar una u otra. También se busca identificar los cuellos de botella existentes y encontrar formas innovadoras de removerlos.