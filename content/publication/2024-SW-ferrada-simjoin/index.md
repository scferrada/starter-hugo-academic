---
title: "Similarity joins and clustering for SPARQL"
authors:
- admin
- Aidan Hogan
- Benjamin Bustos
#author_notes:
#- "Equal contribution"
#- "Equal contribution"
date: "2024-03-01T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2017-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: "*Semantic Web Journal*"
publication_short: ""

abstract: The SPARQL standard provides operators to retrieve exact matches on data, such as graph patterns, filters and grouping. This work proposes and evaluates two new algebraic operators for SPARQL 1.1 that return similarity-based results instead of exact results. First, a similarity join operator is presented, which brings together similar mappings from two sets of solution mappings. Second, a clustering solution modifier is introduced, which instead of grouping solution mappings according to exact values, brings them together by using similarity criteria. For both cases, a variety of algorithms are proposed and analysed, and use-case queries that showcase the relevance and usefulness of the novel operators are presented. For similarity joins, experimental results are provided by comparing different physical operators over a set of real world queries, as well as comparing our implementation to the closest work found in the literature, DBSimJoin, a PostgreSQL extension that supports similarity joins. For clustering, synthetic queries are designed in order to measure the performance of the different algorithms implemented.

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags:
- Similarity Joins in Databases
- Clustering in Databases
- SPARQL
featured: false

# links:
# - name: ""
#   url: ""
url_pdf: 
url_code: 'https://github.com/scferrada/jena'
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
