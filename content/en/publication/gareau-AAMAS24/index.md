---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: Cooperative Electric Vehicles Planning
subtitle: ''
authors:
- admin
- Marc-André Lavoie
- Guillaume Gosset
- Éric Beaudry
author_notes: []
tags: [Electric Vehicles, Cooperative, Multi-Agent, Contingency Planning, Deterministic Planning]
categories: []
projects: [veplan]
date: '2024-05-09'
lastmod: 2024-04-26T16:44:02-04:00
publishDate: '2024-04-26T20:44:02.264969Z'
featured: false
draft: false

publication: 'Proceedings of the 23rd International Conference on Autonomous Agents and Multi-Agent Systems'
publication_short: 'AAMAS 2024'
doi: ''

publication_types:
- paper-conference

summary: ''
abstract: "This paper introduces the Cooperative Electric Vehicles Planning
Problem (CEVPP), which consists in finding a path for each vehicle of a fleet of
electric vehicles, such that the global plan execution time (including travel
time, charging time and waiting time) is minimal (e.g., by limiting the number
of vehicles who need to charge simultaneously at the same charging station,
which leads to waiting time). We show that the strategy which consists in
planning each possible permutation of EVs and keeping the one providing the best
solution is not only time intractable, but also not optimal. We propose
different centralized planning algorithms to solve CEVPP instances: (1) a
baseline non-cooperative CEVPP planner, (2) an optimal cooperative planner that
finds a solution inside a carefully designed state space, and (3) multiple
variants of an approximate cooperative planner based on the Cooperative-A*
algorithm. We compare the solutions' quality and computation times obtained by
these CEVPP planners. Our empirical results show that our best approximate
cooperative EV planner found solutions with a reasonably small computational
overhead compared to the baseline algorithm. The solutions found by our
cooperative planners had significantly lower plan execution time globally,
including travel time, waiting time and charging time, than the solution found
by our baseline non-cooperative planner. On average, our empirical results show
that our cooperative algorithms decreased the global (including each EVs)
waiting time by more than 90%, while having a negligible impact on the charging
and driving time."

# Links
url_pdf: ''
url_code: 'code.zip'
url_dataset: ''
url_poster: 'poster.pdf'
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
