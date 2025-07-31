---
title: "COTTAS: Columnas Triple Table Storage for Efficient and Compressed RDF Management"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Julián Arenas-Guerrero
  - admin

# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2025-07-30T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['1']

# Publication name and optional abbreviated publication name.
publication: "In *24th International Semantic Web Conference*"
publication_short: "In *ISWC 2025*"

abstract: "One of the main challenges in working with RDF data is its verbosity, as repeated IRIs and IRI prefixes lead to large files that are costly to store and process. HDT, a binary RDF format, addresses this by compressing data while supporting efficient triple pattern evaluation without decompression. However, its performance is highly dependent on index alignment with query patterns. In this paper, we introduce COTTAS, a storage model that encodes RDF graphs directly into the open-source Apache Parquet columnar format. COTTAS represents RDF as a triple table and leverages block range indexes (zone maps) to achieve high compression ratios and fast query execution over compressed data. We also provide pycottas, an open-source Python library that enables compression of RDF data into COTTAS format and supports efficient querying by translating triple patterns into SQL queries over COTTAS files. This implementation facilitates the adoption of COTTAS for managing RDF graphs. Experiments on the WDBench and DBpedia benchmarks show that COTTAS reduces storage requirements by around 50% with respect to HDT and exhibits competitive triple pattern evaluation, with less performance volatility across pattern types."

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - Compression
  - RDF Management

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/arenas-guerrero-julian/pycottas'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
#  focal_point: ''
#  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: [fondecyt-iniciacion]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---
