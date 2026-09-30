---
title: "Native Graph Neural Network Training in MillenniumDB"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Benito Fuentes
  - Sebastián Vergara
  - admin

# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2026-11-11T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2026-09-30T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['1']

# Publication name and optional abbreviated publication name.
publication: "In *17th Alberto Mendelzon International Workshop on Foundations of Data Management*"
publication_short: "In *AMW 2026*"

abstract: "Training Graph Neural Networks on graphs that exceed main memory often requires exporting data from graph database systems to external machine learning frameworks. We present a database-native, out-of-core GraphSAGE training pipeline integrated into MillenniumDB and exposed through four GQL procedures. The pipeline materializes reusable mini-batches, distributes features across GPU memory, pinned host memory, and NVMe storage based on access frequency, applies frequency-based tiering to the graph topology as well, and writes the learned embeddings back to MillenniumDB for graph pattern and similarity queries. We evaluate on Cora, ogbn-arxiv, ogbn-products, and ogbn-papers100M (111M nodes, 1.6B directed edges). On a commodity desktop (32 GiB RAM, 16 GB GPU), PyG, DGL, and Neo4j GDS run out of memory on ogbn-papers100M. MillenniumDB completes 50 training epochs in 41.2 minutes after a one-time 95.7-minute preparation, matching the accuracy of the state-of-the-art out-of-core system DiskGNN. An ablation shows that topology tiering speeds up offline sampling by 3.81× without altering the sampled mini-batches."

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - Graph Neural Networks
  - Graph Databases
  - Out-of-core Training
  - MillenniumDB

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
projects: [u-inicia, fondecyt-iniciacion]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---
