---
title: "Using Graph Neural Networks and the Internet Graph Topology to Learn Autonomous System Relationships"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Valentina Esteban
  - admin
  - Ivana Bachmann

# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2026-11-11T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2026-10-30T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['1']

# Publication name and optional abbreviated publication name.
publication: "In *17th Alberto Mendelzon International Workshop on Foundations of Data Management*"
publication_short: "In *AMW 2026*"

abstract: "The Internet is built upon thousands of interconnected Autonomous Systems (ASes) that exchange routing information through the Border Gateway Protocol (BGP). The commercial relationships between ASes classified as peer-to-peer (P2P), customer-to-provider (C2P), or provider-to-customer (P2C), shape the paths that packets follow across the network. However, this information is rarely disclosed publicly and must be inferred from indirect sources. Accurate inference of AS relationships is essential for analyzing the Internet structure, understanding routing policies, and detecting anomalies. In this work, we propose using Graph Neural Networks (GNNs) as a novel approach to this inference task. We construct an AS-level Internet graph with 79K nodes and 438K edges from BGP Routing Information Bases (RIBs) collected via RouteViews and RIPE RIS, enriching node representations with attributes from PeeringDB and one-hot encoding. We present a GNN approach that evaluates two GNN architectures (GCN and GraphSAGE) end-to-end, with the GNN and an MLP decoder jointly trained for relationship classification. We compare against established graph embedding baselines, DeepWalk and BGP2Vec. The best model, a GCN + MLP architecture with PeeringDB attributes, achieves 0.952 accuracy and 0.950 macro-F1, surpassing BGP2Vec in macro-F1 (0.946) while requiring half the training time (10 vs 20 min), suggesting that GNNs offer a scalable and structurally motivated alternative for AS relationship inference."

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - Graph Neural Networks
  - BGP
  - Autonomous Systems
  - Internet Topology

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/valesteban/gnn-as-relationships'
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
