---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: Cache-Efficient Memory Representation of Markov Decision Processes
subtitle: ''
authors:
- admin
- Éric Beaudry
- Vladimir Makarenkov
author_notes: []
tags: [MDP, Cache Memory, Data Structures]
categories: []
projects: [MDP]
date: '2022-01-01'
lastmod: 2022-04-16T16:44:02-04:00
publishDate: '2022-04-16T20:44:02.264969Z'
featured: false
draft: false

publication_types:
  - paper-conference

publication: 'Proceedings of the Canadian Conference on Artificial Intelligence'
publication_short: 'Canadian AI 2022'

hugoblox:
  ids:
    doi: '10.21428/594757db.0e910d58'

summary: ''
abstract: |
  Research in automated planning typically focuses on the development of new or
  improved algorithms. Yet, an equally important but often overlooked topic is
  that of how to actually implement these algorithms efficiently. In this study,
  we are making an attempt to close this gap in the context of optimal Markov
  Decision Process (MDP) planning. Precisely, we present a novel cache-efficient
  memory representation of MDPs, which we call CSR-MDP, that takes advantage of
  low-level hardware features such as memory hierarchy. We evaluate the speed
  improvement provided by our memory representation by comparing the performance
  of CSR-MDP with the performance obtained by traditional MDP representation. We
  show that by using our CSR-MDP memory representation, existing MDP solvers,
  including VI, LRTDP and TVI, are able to find an optimal policy an order of
  magnitude faster.

links:
  - type: slides
    url: 'slides.pdf'

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---
