---
title: "Graph Querying or Similarity Search? Both!"

event: "24th International Semantic Web Conference (ISWC 2025), Research Track"
event_url: "https://iswc2025.semanticweb.org/"

location: "Nara, Japan"

abstract: "Extracting information from knowledge graphs is a significant algorithmic challenge, especially when dealing with multimodal knowledge graphs that integrate images, text, and/or videos. While current graph management systems can efficiently evaluate graph queries, they struggle with multimedia data. To address this, systems rely on metadata, such as vector embeddings, for similarity search. While both graph pattern evaluation and similarity search work well independently, real-world applications often require their combination to retrieve media based on both the graph structure and specific similarity criteria. This paper studies the problem of querying multimodal knowledge graphs by combining graph patterns with similarity constraints. We formalize this as an extraction task where some nodes in the graph pattern are filtered by similarity, and then the results must be ordered by a similarity score. While a straightforward approach is to evaluate the graph pattern first and then sort by similarity, we introduce alternative algorithms that evaluate both tasks jointly, leveraging indices for efficient similarity computation. Our implementation employs an approximate version of these indices, and our experiments show that graph database systems can efficiently integrate semantic similarity constraints into their queries. "

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: '2025-11-05T00:00:00Z'
#date_end: ''
all_day: true

# Schedule page publish date (NOT talk date).
publishDate: '2025-11-05T00:00:00Z'

authors: [admin]
tags: ['Similarity Search', 'Multimodal Knowledge Graphs', 'MillenniumDB']

# Is this a featured talk? (true/false)
featured: false

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/ferradest
  - name: Paper
    url: publication/2025-iswc-calisto-gq+sim/
#url_code: ''
#url_pdf: ''
url_slides: 'pptx/GraphSimSearch-ISWC2025.pptx'
url_video: ''

slides: ""
---
