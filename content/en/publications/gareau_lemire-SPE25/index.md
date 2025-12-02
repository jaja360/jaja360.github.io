---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: 'Converting Binary Floating-Point Numbers to Shortest Decimal Strings: An Experimental Review'
subtitle: ''
authors:
- admin
- Daniel Lemire
author_notes: []
tags: [Floating-Point, Decimal, Binary, Shortest String, Conversion]
categories: []
projects: [Float]
date: '2025-07-19'
lastmod: '2025-07-19T16:44:02-04:00'
publishDate: '2025-07-19T16:44:02-04:00'
featured: false
draft: false

publication_types:
  - preprint

publication: 'Software: Practice and Experience'

# hugoblox:
#   ids:
#     doi: ''

summary: ''
abstract: |
  When sharing or logging numerical data, we must convert binary floating-point
  numbers into their decimal string representations. For example, the number $\pi$
  might become 3.1415927. Engineers have perfected many algorithms for producing
  such accurate, short strings. We present an empirical comparison across
  diverse hardware architectures and datasets. Cutting-edge techniques like
  Schubfach and Dragonbox achieve up to a tenfold speedup over Steele and
  White’s Dragon4, executing as few as 210 instructions per conversion compared
  to Dragon4’s 1500–5000 instructions. Maybe surprisingly, none of the
  implementations we surveyed consistently produced the shortest possible
  strings—some generate outputs up to 30% longer than optimal. We find that
  standard library implementations in languages such as C++ and Swift execute
  significantly more instructions than the fastest methods, with performance
  gaps varying across CPU architectures and compilers. We suggest some
  optimization targets for future research.

links:
  - type: code
    url: 'https://github.com/fastfloat/float_serialization_benchmark'
  - name: Benchmark Data
    url: results.zip

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---

This paper has been submitted for peer review. Data are shared here for reviewer access.
