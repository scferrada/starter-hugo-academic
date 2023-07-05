---
title: "An efficient algorithm for approximated self-similarity joins in metric spaces"
authors:
- admin
- Benjamin Bustos
- Nora Reyes
#author_notes:
#- "Equal contribution"
#- "Equal contribution"
date: "2020-02-01T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2017-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: "*Information Systems*"
publication_short: ""

abstract: Similarity join is a key operation in metric databases. It retrieves all pairs of elements that are similar. Solving such a problem usually requires comparing every pair of objects of the datasets, even when indexing and ad hoc algorithms are used. We propose a simple and efficient algorithm for the computation of the approximated k nearest neighbor self-similarity join. This algorithm computes Θ(n3∕2) distances and it is empirically shown that it reaches an empirical precision of 46% in real-world datasets. We provide a comparison to other common techniques such as Quickjoin and Locality-Sensitive Hashing and argue that our proposal has a better execution time and average precision.

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags:
- Approximated Nearest Neighbors
- Similarity Joins
featured: true

# links:
# - name: ""
#   url: ""
url_pdf: 
url_code: 'https://github.com/scferrada/self-sim-join'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/jdD8gXaTZsc)'
  focal_point: ""
  preview_only: false

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
