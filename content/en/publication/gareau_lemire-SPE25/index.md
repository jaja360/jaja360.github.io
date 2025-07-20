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

publication: 'Software: Practice and Experience'
doi: ''

publication_types:
- preprint

summary: ''
abstract: |
  When sharing or logging numerical data, we must convert binary floating-point
  numbers into their decimal string representations. For example, $\pi$ as a
  32-bit number becomes 3.1415927. Engineers have perfected many algorithms for
  producing such accurate, short strings. To our knowledge, no up-to-date
  comparison of these methods has appeared in the literature. We present an
  empirical comparison. Cutting-edge techniques like Schubfach and Dragonbox
  achieve up to a tenfold speedup over Steele and White's Dragon4. Maybe
  surprisingly, none of the implementations we surveyed consistently produced
  the shortest possible string. We find that standard library implementations in
  languages such as C++ and Swift can execute up to 50% more instructions than
  the fastest methods.

# Links
url_pdf: ''
url_code: 'https://github.com/fastfloat/float_serialization_benchmark'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

links:
- name: Benchmark Data
  url: results.zip

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---

This paper has been submitted for peer review. Data are shared here for reviewer access.
