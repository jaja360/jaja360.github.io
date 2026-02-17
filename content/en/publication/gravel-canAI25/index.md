---
title: Topology-Driven Solver Selection for Stochastic Shortest Path MDPs via Explainable Machine Learning
subtitle: ""
authors:
  - Mathieu Gravel
  - me
author_notes: []
tags:
  - MDP
  - Probabilistic Planning
  - Benchmarks
  - Explainable AI
  - Machine Learning
  - Classifiers
categories: []
projects:
  - MDP
date: 2025-05-12
lastmod: 2025-07-26T16:44:02-04:00
publishDate: 2026-02-04T16:44:02.264969Z
featured: false
draft: false
publication_types:
  - paper-conference
publication: Proceedings of the Canadian Conference on Artificial Intelligence
publication_short: Canadian AI 2025
hugoblox:
  ids:
    doi: 10.21428/594757db.f73769f4
summary: ""
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
links:
  - type: pdf
    url: https://assets.pubpub.org/1b6hfklo/paper4-01746725442153.pdf
  - type: code
    url: https://github.com/MathGravel/sspmdp-classifier
  - type: slides
    url: slides.pdf
  - type: official
    url: https://caiac.pubpub.org/pub/5zlwwdas/release/1
image:
  caption: ""
  focal_point: Smart
  preview_only: false
---

