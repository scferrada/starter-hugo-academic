---
title: 'A Simple, Efficient, Parallelizable Algorithm for Approximated Nearest Neighbors'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - admin
  - Benjamin Bustos
  - Nora Reyes

# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2018-05-01T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['0']

# Publication name and optional abbreviated publication name.
publication: In *12th Alberto Mendelzon International Workshop on Foundations of Data Management and the Web*
publication_short: In *AMW 2018*

abstract: The use of the join operator in metric spaces leads to what is known as a similarity join, where objects of two datasets are paired if they are somehow similar. We propose an heuristic that solves the 1-NN selfsimilarity join, that is, a similarity join of a dataset with itself, that brings together each element with its nearest neighbor within the same dataset. Solving the problem using a simple brute-force algorithm requires O(n 2 ) distance calculations, since it requires to compare every element against all others. We propose a simple divide-and-conquer algorithm that gives an approximated solution for the self-similarity join that computes only O(n 3 2 ) distances. We show how the algorithm can be easily modified in order to improve the precision up to 31% (i.e., the percentage of correctly found 1-NNs) and such that 79% of the results are within the 10-NN, with no significant extra distance computations. We present how the algorithm can be executed in parallel and prove that using Θ( √ n) processors, the total execution takes linear time. We end discussing ways in which the algorithm can be improved in the future.

# Summary. An optional shortened abstract.
#summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: [Similarity Joins, Approximated Algorithms]

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/scferrada/simjoins'
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
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---
