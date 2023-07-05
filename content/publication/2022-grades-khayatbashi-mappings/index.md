---
title: 'Converting Property Graphs to RDF: A Preliminary Study of the Practical Impact of Different Mappings'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Shahrzad Khayatbashi
  - admin
  - Olaf HArtig

# Author notes (optional)
#author_notes:
#  - 'Equal contribution'
#  - 'Equal contribution'

date: '2022-04-01T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['0']

# Publication name and optional abbreviated publication name.
publication: In *Joint Workshop on Graph Data Management Experiences & Systems (GRADES) and Network Data Analytics (NDA)*
publication_short: In *(GRADES-NDA'22)*

abstract: Today's space of graph database solutions is characterized by two main technology stacks that have evolved separate from one another: on one hand, there are systems that focus on supporting the RDF family of standards; on the other hand, there is the Property Graph category of systems. As a basis for bringing these stacks together and, in particular, to facilitate data exchange between the different types of systems, different direct mappings between the underlying graph data models have been introduced in the literature. While fundamental properties are well-documented for most of these mappings, the same cannot be said about the practical implications of choosing one mapping over another. Our research aims to contribute towards closing this gap. In this paper we report on a preliminary study for which we have selected two direct mappings from (Labeled) Property Graphs to RDF, where one of them uses features of the RDF-star extension to RDF. We compare these mappings in terms of the query performance achieved by two popular commercial RDF stores, GraphDB and Stardog, in which the converted data is imported. While we find that, for both of these systems, none of the mappings is a clear winner in terms of guaranteeing better query performance, we also identify types of queries that are problematic for the systems when using one mapping but not the other.

# Summary. An optional shortened abstract.
# summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags: 
  - Property Graphs
  - RDF
  - RDF-star
  - Mappings
  - Interoperability

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/LiUSemWeb/GRADES2022-paper'
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
