---
title: "froGQL: Worst-Case Optimal Joins and Type-Driven Optimization for Lightweight GQL"

event: "25th International Semantic Web Conference (ISWC 2026), Resources Track"
event_url: "https://iswc2026.semanticweb.org/"

location: "Bari, Italy"

abstract: "We present froGQL, an open-source graph database that keeps a property graph, its schema, and its indexes in a single file and runs inside the host application, in the manner of SQLite, while implementing the ISO GQL standard. froGQL makes two contributions. First, its engine evaluates multi-pattern queries with Leapfrog Triejoin, a worst-case optimal algorithm whose cost is bounded by the largest result the query could produce, applied directly over a sorted-adjacency layout so that no intermediate results are built. On queries that start from one node identified by an indexed property and then follow several edges, froGQL is the fastest of the three systems we measure on the LDBC Social Network Benchmark: 13 ms on IC2 against 19 ms for Kùzu and 21 ms for GraphQLite, and 1.1 ms on IC11 against Kùzu's 4.8 ms. Resolving the equality filter on the starting node before the search begins earns that margin: without it, IC11 takes 4.6 s. Second, a static type system rejects queries that cannot return a result before any part of the graph is read. The check costs 0.1 ms on a four-hop query the engine would otherwise spend 132 s enumerating, and stays below 1% of query time in 26 of the 36 valid cases measured; it does not depend on froGQL's runtime and can be placed in front of any conforming GQL engine. froGQL is MIT-licensed and available at https://github.com/pleiad/frogql, with packages for Rust, Python, Node.js, and the browser."

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: '2026-10-25T00:00:00Z'
#date_end: ''
all_day: true

# Schedule page publish date (NOT talk date).
publishDate: '2026-09-29T00:00:00Z'

authors: [admin]
tags: ['froGQL', 'GQL', 'Graph Databases']

# Is this a featured talk? (true/false)
featured: false

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/ferradest
#url_code: ''
#url_pdf: ''
url_slides: ''
url_video: ''

slides: ""
---
