---
title: "froGQL: Worst-Case Optimal Joins and Type-Driven Optimization for Lightweight GQL"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Felipe Avendaño
  - Jean Paul Duchens
  - admin
  - Matías Toro
  
# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2026-08-03T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['1']

# Publication name and optional abbreviated publication name.
publication: "In *25th International Semantic Web Conference*"
publication_short: "In *ISWC 2026*"

abstract: "We present froGQL, an open-source graph database that keeps a property graph, its schema, and its indexes in a single file and runs inside the host application, in the manner of SQLite, while implementing the ISO GQL standard. froGQL makes two contributions. First, its engine evaluates multi-pattern queries with Leapfrog Triejoin, a worst-case optimal algorithm whose cost is bounded by the largest result the query could produce, applied directly over a sorted-adjacency layout so that no intermediate results are built. On queries that start from one node identified by an indexed property and then follow several edges, froGQL is the fastest of the three systems we measure on the LDBC Social Network Benchmark: 13 ms on IC2 against 19 ms for Kùzu and 21 ms for GraphQLite, and 1.1 ms on IC11 against Kùzu's 4.8 ms. Resolving the equality filter on the starting node before the search begins earns that margin: without it, IC11 takes 4.6 s. Second, a static type system rejects queries that cannot return a result before any part of the graph is read. The check costs 0.1 ms on a four-hop query the engine would otherwise spend 132 s enumerating, and stays below 1% of query time in 26 of the 36 valid cases measured; it does not depend on froGQL's runtime and can be placed in front of any conforming GQL engine. froGQL is MIT-licensed and available at https://github.com/pleiad/frogql, with packages for Rust, Python, Node.js, and the browser."

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - GQL
  - Worst-case optimal joins
  - Type-checker optimization

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/pleiad/frogql'
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
projects: [u-inicia]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---
