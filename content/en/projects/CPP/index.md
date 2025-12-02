---
title: Coverage Path-Planning
summary: This project aimed at developping optimal coverage path-planning algorithms. As futur work, we also plan on developping a CPP planner that considers energetic constraints, uncertainties, as well as dynamic environments.
tags: [Deterministic Planning, Heuristic Search, Branch-and-Bound]
date: "2023-04-29T00:00:00Z"

image:
  caption: An example of a 9x14 CPP grid solved by the Wavefront algorithm.
  focal_point: Smart

links:
  - type: code
    url: 'https://gitlab.info.uqam.ca/champagne_gareau.jael/cpp'

---

A problem studied in the field of AI planning is the **coverage path-planning
problem** (CPP). This problem consists in finding a path that covers a given
region entirely while respecting some constraints (e.g., avoid obstacles, use
only simple movements, etc.), and minimizing the time of plan execution (or,
e.g., the number of movements). This problem appears in several contexts, such
as search and rescue, minesweeping, 3D reconstruction of regions flown over by a
drone, submarine exploration using autonomous underwater vehicles (AUVs), floor
or window cleaning, and 3D printing.

Unfortunately, no *optimal* CPP planner exist in literature (apart from the
naïve exhaustive search solution). Furthermore, no CPP planner considers
uncertainties, energetic constraints as well as dynamic environments. In this
project, we developed a [C++ CPP
Library](https://gitlab.info.uqam.ca/champagne_gareau.jael/cpp) that supports
classical algorithms (e.g., the wavefront algorithm) as well as our proposed new
planning algorithms that uses heuristic search and branch-and-bound techniques.
