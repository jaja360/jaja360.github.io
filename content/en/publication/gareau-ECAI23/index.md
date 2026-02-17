---
title: Cache-Efficient Dynamic Programming MDP Solver
subtitle: ""
authors:
  - me
  - Guillaume Gosset
  - Éric Beaudry
  - Vladimir Makarenkov
author_notes: []
tags:
  - MDP
  - Cache Memory
  - Algorithms
categories: []
projects:
  - MDP
date: 2023-09-30
lastmod: 2022-04-16T16:44:02-04:00
publishDate: 2022-04-16T20:44:02.264969Z
featured: false
draft: false
publication_types:
  - paper-conference
publication: Proceedings of the 26th European Conference on Artificial Intelligence
publication_short: ECAI 2023
hugoblox:
  ids:
    doi: 10.3233/FAIA230293
summary: ""
abstract: |
  Automated planning research often focuses on developing new algorithms to
  improve the computational performance of planners, but effective
  implementation can also play a significant role. Hardware features such as
  memory hierarchy can yield substantial running time improvements when
  optimized. In this paper, we propose two state-reordering techniques for the
  Topological Value Iteration (TVI) algorithm. Our first technique organizes
  states in memory so that those belonging to the same Strongly Connected
  Component (SCC) are contiguous, while our second technique optimizes state
  value propagation by reordering states within each SCC. We analyze existing
  planning algorithms with respect to their cache efficiency and describe domain
  characteristics which can provide an advantage to each of them. Empirical
  results show that, in many instances, our new algorithms, called eTVI and
  eiTVI, run several times faster than traditional VI, TVI, LRTDP and ILAO*
  techniques.
links:
  - type: code
    url: code.zip
  - type: slides
    url: slides.pdf
  - type: poster
    url: poster.pdf
  - type: supplementary
    url: supp.pdf
image:
  caption: ""
  focal_point: Smart
  preview_only: false
---

