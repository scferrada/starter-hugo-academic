---
title: "The Property Graph Data Format (PGDF)"
authors:
- Renzo Angles
- admin
- Ignacio Burgos
#author_notes:
#- "Equal contribution"
#- "Equal contribution"
date: "2024-03-01T00:00:00Z"
doi: "10.1109/ACCESS.2024.3485685"

# Schedule page publish date (NOT publication's date).
publishDate: "2017-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: "*IEEE Access*"
publication_short: ""

abstract: Property graphs are popular in both industry and academia due to their versatility in modeling complex data across diverse application domains, ranging from social networks to knowledge graphs. Despite their popularity, there is no standardized data format for storing and exchanging property graphs. This paper introduces PGDF, a text-based data format for property graphs, designed to be both simple and flexible, while remaining expressive and efficient. The simplicity of PGDF comes from its tabular-like structure, where each line in a PGDF file contains a single schema or data declaration. PGDF offers great flexibility by allowing schema and data declarations to be combined in any order. This means that nodes and edges can each have their own distinct properties, providing greater adaptability and customization. The expressiveness of PGDF is defined by its ability to represent a wide range of property graph features. In this article, we describe the syntax and semantics of PGDF, outline methods for converting property graphs stored in multiple CSV files to PGDF and other graph data formats, and present an experimental evaluation comparing PGDF, YARS-PG, GraphML, and JSON-Neo4j. The experiments show that PGDF enables the production of smaller files more quickly compared to other graph data formats.

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags:
- Graph Databases
- Property Graphs
- Graph Data Formats
- PGDF
featured: false

# links:
# - name: ""
#   url: ""
url_pdf: 
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/jdD8gXaTZsc)'
#  focal_point: ""
#  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---
