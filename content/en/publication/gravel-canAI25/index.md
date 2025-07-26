---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: Topology-Driven Solver Selection for Stochastic Shortest Path MDPs via Explainable Machine Learning
subtitle: ''
authors:
- Mathieu Gravel
- admin
author_notes: []
tags: [MDP, Probabilistic Planning, Benchmarks, Explainable AI, Machine Learning, Classifiers]
categories: []
projects: [MDP]
date: '2025-05-12'
lastmod: 2025-07-26T16:44:02-04:00
publishDate: '2025-05-12T16:44:02.264969Z'
featured: false
draft: false

publication: 'Proceedings of the Canadian Conference on Artificial Intelligence'
publication_short: 'Canadian AI 2025'
doi: ''

publication_types:
- paper-conference

summary: ''
abstract: |
  Selecting optimal solvers for complex AI tasks grows increasingly difficult as
  algorithmic options expand. We address this challenge for Stochastic Shortest
  Path Markov Decision Processes (SSP-MDPs) --- a core model for robotics
  navigation, autonomous system planning, and stochastic scheduling --- by
  introducing a topology-driven solver selection framework. First, we identify
  and empirically validate topological features --- including strongly connected
  components, goal-state ratio, goal eccentricity (i.e., maximal distance to a
  goal), and average actions per state --- that critically influence solver
  performance across synthetic and real-world SSP-MDPs. Using these insights, we
  propose the first classifier able to predict the fastest MDP solver for a
  given instance, achieving over 64% accuracy on diverse benchmarks.
  Counterfactual explainability analysis further clarifies how these features
  govern solver efficiency. By directly linking topological structures to
  algorithmic performance, our work streamlines solver selection while enhancing
  computational efficiency, offering a principled approach to MDP optimization.

# Links
url_pdf: 'https://assets.pubpub.org/1b6hfklo/paper4-01746725442153.pdf'
url_code: 'https://github.com/MathGravel/sspmdp-classifier'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: 'slides.pdf'
url_source: ''
url_video: ''

links:
  - name: Official Page
    url: https://caiac.pubpub.org/pub/5zlwwdas/release/1
    icon_pack: fas
    icon: link

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---
