---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: 'pcTVI: Parallel MDP Solver Using a Decomposition Into Independent Chains'
subtitle: ''
authors:
- admin
- Éric Beaudry
- Vladimir Makarenkov
author_notes: []
tags: [MDP, Probabilistic Planning, Parallelism]
categories: []
projects: [MDP]
date: '2022-01-01'
lastmod: 2022-04-16T16:44:02-04:00
publishDate: '2022-04-16T20:44:02.366267Z'
featured: false
draft: false

publication: 'Proceedings of the International Federation of Classification Societies Conference'
publication_short: 'IFCS 2022'
doi: '10.1007/978-3-031-09034-9_12'

publication_types:
- paper-conference

summary: ''
abstract: |
  Markov Decision Processes (MDPs) are useful to solve real-world probabilistic
  planning problems. However, finding an optimal solution in an MDP can take an
  unreasonable amount of time when the number of states in the MDP is large. In
  this paper, we present a way to decompose an MDP into Strongly Connected
  Components (SCCs) and to find dependency chains for these SCCs. We then
  propose a variant of the Topological Value Iteration (TVI) algorithm, called
  parallel chained TVI (pcTVI), which is able to solve independent chains of
  SCCs in parallel leveraging modern multicore computer architectures. The
  performance of our algorithm was measured by comparing it to the baseline TVI
  algorithm on a new probabilistic planning domain introduced in this study. Our
  pcTVI algorithm led to a speedup factor of 20, compared to traditional TVI (on
  a computer having 32 cores).

# Links
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: 'slides.pdf'
url_source: ''
url_video: ''

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---
