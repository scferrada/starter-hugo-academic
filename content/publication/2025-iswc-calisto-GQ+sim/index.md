---
title: "Graph Querying or Similarity Search? Both!"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Vicente Calisto
  - admin
  - Gonzalo Navarro
  - Juan L. Reutter
  - Juan Pablo Sánchez
  - Domagoj Vrgoč

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

abstract: "Extracting information from knowledge graphs is a significant algorithmic challenge, especially when dealing with multimodal knowledge graphs that integrate images, text, and/or videos. While current graph management systems can efficiently evaluate graph queries, they struggle with multimedia data. To address this, systems rely on metadata, such as vector embeddings, for similarity search. While both graph pattern evaluation and similarity search work well independently, real-world applications often require their combination to retrieve media based on both the graph structure and specific similarity criteria. This paper studies the problem of querying multimodal knowledge graphs by combining graph patterns with similarity constraints. We formalize this as an extraction task where some nodes in the graph pattern are filtered by similarity, and then the results must be ordered by a similarity score. While a straightforward approach is to evaluate the graph pattern first and then sort by similarity, we introduce alternative algorithms that evaluate both tasks jointly, leveraging indices for efficient similarity computation. Our implementation employs an approximate version of these indices, and our experiments show that graph database systems can efficiently integrate semantic similarity constraints into their queries. "

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - Similarity Search
  - Graph Querying
  - SPARQL 

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
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
