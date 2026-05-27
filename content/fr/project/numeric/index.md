---
title: Conversion de nombres en chaînes décimales
summary: Ce projet étudie des algorithmes rapides et exacts pour convertir des nombres binaires, flottants ou entiers, vers leurs représentations décimales textuelles.
tags: [Floating-Point, Integer, Decimal, Conversion, SIMD]
date: "2026-05-06"
image:
  caption: Illustration de la conversion de données numériques binaires vers des chaînes décimales.
  focal_point: Smart

links:
  - type: code
    label: Code flottants-chaînes
    url: 'https://github.com/fastfloat/float_serialization_benchmark'
  - type: code
    label: Code entiers-chaînes
    url: 'https://github.com/fastfloat/int_serialization_benchmark'
---

La conversion de nombres en chaînes décimales est une opération fondamentale,
mais souvent sous-estimée. Elle intervient dès que des données numériques sont
affichées, enregistrées dans des journaux, exportées vers des formats textuels
comme JSON ou CSV, ou échangées entre systèmes. Même lorsqu'un calcul est fait en
binaire, il faut généralement produire une représentation décimale lisible,
compacte et exacte.

Ce projet rassemble des travaux sur deux familles complémentaires de conversions.
La première concerne les **nombres à virgule flottante binaires**, où l'objectif
est de produire une chaîne décimale courte qui permet de retrouver exactement la
valeur initiale lors d'une lecture ultérieure. Nous y comparons empiriquement des
algorithmes modernes, comme Schubfach et Dragonbox, à des approches plus
classiques comme Dragon4, sur plusieurs architectures matérielles.

La seconde concerne les **entiers binaires**, où le défi principal est la vitesse
de conversion. Nous étudions des méthodes exploitant le parallélisme SIMD,
notamment les instructions AVX-512 IFMA, afin de convertir des entiers en chaînes
décimales en moins de deux nanosecondes dans certains scénarios. Ces techniques
évitent les grandes tables de correspondance et calculent plusieurs chiffres en
parallèle.

Dans les deux cas, l'objectif est de mieux comprendre les compromis entre
exactitude, longueur des chaînes produites, portabilité et performance. Ces
travaux visent à guider l'optimisation de bibliothèques numériques, de langages
de programmation et de systèmes où la sérialisation de nombres est critique.
