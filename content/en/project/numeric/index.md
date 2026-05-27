---
title: Number to Decimal String Conversion
summary: This project studies fast and exact algorithms for converting binary numbers, floating-point or integer, to their decimal string representations.
tags: [Floating-Point, Integer, Decimal, Conversion, SIMD]
date: "2026-05-06"
image:
  caption: Illustration of the conversion of binary numerical data to decimal strings.
  focal_point: Smart

links:
  - type: code
    label: Float-to-string code
    url: 'https://github.com/fastfloat/float_serialization_benchmark'
  - type: code
    label: Int-to-string code
    url: 'https://github.com/fastfloat/int_serialization_benchmark'

---

Converting numbers to decimal strings is a fundamental yet often overlooked
operation. It occurs whenever numerical data is displayed, logged, exported to
text formats such as JSON or CSV, or exchanged between systems. Even when
computations are performed in binary, we typically need to produce a readable,
compact, and exact decimal representation.

This project brings together work on two complementary families of conversions.
The first concerns **binary floating-point numbers**, where the goal is to
produce a short decimal string that recovers the exact original value when read
back. We empirically compare modern algorithms such as Schubfach and Dragonbox
against more classical approaches such as Dragon4 across several hardware
architectures.

The second concerns **binary integers**, where the main challenge is conversion
speed. We study methods that exploit SIMD parallelism, especially AVX-512 IFMA
instructions, to convert integers to decimal strings in under two nanoseconds in
some scenarios. These techniques avoid large lookup tables and compute several
digits in parallel.

In both cases, the goal is to better understand the trade-offs between accuracy,
the length of the produced strings, portability, and performance. This work aims
to guide the optimization of numerical libraries, programming languages, and
systems where number serialization is performance-critical.
