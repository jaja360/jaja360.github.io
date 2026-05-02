---
title: "Converting an Integer to a Decimal String in Under Two Nanoseconds"
subtitle: ""
authors:
  - me
  - Daniel Lemire
author_notes: []
tags:
  - Integer
  - Decimal
  - Binary
  - Shortest String
  - Conversion
  - SIMD
  - AVX-512
categories: []
projects:
  - Float
date: 2026-04-28
featured: false
draft: false
publication_types:
  - article-journal
publication: "Software: Practice and Experience"
hugoblox:
  ids:
    # doi:
    arxiv: 2604.26019
summary: ""
abstract: |
  Converting binary integers to variable-length decimal strings is a fundamental
  operation in computing. Conventional fast approaches rely on recursive division
  and small lookup tables. We propose a SIMD-based algorithm that leverages
  AVX-512 IFMA instructions available on recent AMD and Intel processors. Our
  method eliminates lookup tables entirely and computes multiple quotients and
  remainders in parallel.
  Additionally, we introduce a dual-variant design with dynamic
  selection that adapts to input characteristics: a branch-heavy variant optimized
  for homogeneous digit-length distributions and a branch-light variant for
  heterogeneous datasets. Our single-core algorithm consistently outperforms all
  ten competing methods across the full range of integer sizes, running
  1.4--2$\times$ faster than the closest competitor and 2--4$\times$ faster than
  the C++ standard library function `std::to_chars` across tested workloads.
links:
  - type: code
    url: https://github.com/fastfloat/int_serialization_benchmark
  - type: benchmark
    url: results.zip
image:
  caption: ""
  focal_point: Smart
  preview_only: false
---
This paper has been accepted for publication in *Software: Practice and Experience*. The accepted author version is available on arXiv while the journal version is not yet available online.
