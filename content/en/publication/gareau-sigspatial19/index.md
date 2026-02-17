---
title: An Efficient Electric Vehicle Path-Planner That Considers the Waiting Time
subtitle: ""
authors:
  - me
  - Éric Beaudry
  - Vladimir Makarenkov
author_notes: []
tags:
  - Electric Vehicles
  - Contingency Planning
  - Deterministic Planning
  - Graph Relabeling
categories: []
projects:
  - veplan
date: 2019-11-05
lastmod: 2022-04-16T16:44:02-04:00
publishDate: 2022-04-16T20:44:02.661609Z
featured: false
draft: false
publication_types:
  - paper-conference
publication: Proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems
publication_short: ACM SIGSPATIAL 2019
hugoblox:
  ids:
    doi: 10.1145/3347146.3359064
abstract: |
  In the last few years, several studies have considered different variants of
  the Electric Vehicle Journey Planning (EVJP) problem that consists in finding
  the shortest path (according to time) between two given points, passing by
  several charging stations and respecting the range of the vehicle. The total
  time taken by the vehicle is the sum of the driving time, the charging time
  and the waiting time. Unfortunately, the consideration of the waiting time has
  been neglected by previous studies. This study aims to fill this gap by
  introducing: (1) a graph relabeling technique using a probabilistic model of
  charging station occupancy generated using real EV stations data; (2) an
  alternative paths generation technique which accounts for worse than expected
  waiting time at various charging stations. Our empirical results indicate that
  the a priori consideration of charging station occupancy by graph relabeling
  can reduce the waiting time by more than 75%, while having a negligible impact
  on the driving time, and that the generation of alternative paths helps reduce
  the waiting (and total) time even more. For our public station network dataset
  and the current station occupancy (for now quite low), the mean total journey
  time (computed over 1000 requests) decreased by 17.3 minutes when our new
  technique was used.
links:
  - type: slides
    url: slides.pdf
image:
  caption: An EV charging at a public station in Montréal
  focal_point: Smart
  preview_only: false
---

