---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: Résolution efficace de processus décisionnels de Markov par l'exploitation d'approches structurelles et algorithmiques tirant parti de l'architecture moderne des ordinateurs
subtitle: ''
authors:
- admin
author_notes: []
tags: [MDP, Probabilistic Planning, Parallelism, Data Structures, Cache Memory, Algorithms, Benchmarks]
categories: []
projects: [MDP]
date: '2024-12-01'
lastmod: 2024-12-04T19:44:02-04:00
publishDate: '2024-12-04T20:44:02.661609Z'
featured: false
draft: false

publication: "Université du Québec à Montréal"
publication_types:
  - thesis
genre: PhD

summary: ''
abstract: |
  Cette thèse présente des contributions en planification automatique sous
  incertitude, un domaine de l'intelligence artificielle. Ce domaine s'intéresse
  principalement au calcul de politiques optimales permettant à un agent
  d'atteindre un objectif lorsque de l'incertitude, due à l'agent lui-même ou à
  l'environnement, est présente. Les travaux présentés dans cette thèse portent
  plus précisément sur les processus décisionnels de Markov (PDM) qui permettent
  de modéliser les problèmes de planification probabiliste, c'est-à-dire les
  problèmes de planification pour lesquels de l'incertitude est présente, mais
  que cette dernière peut être exprimée par un modèle probabiliste connu.

  Plusieurs algorithmes de planification, ayant des stratégies variées,
  permettent de calculer une politique optimale d'un PDM. Cependant, vu les
  instances de problèmes de planification de plus en plus grandes que l'on
  souhaite pouvoir résoudre, les méthodes actuelles ne suffisent pas: elles ne
  sont pas assez rapides. Une façon d'accélérer les calculs passe par une
  meilleure exploitation de l'architecture des processeurs modernes lors de la
  conception et de l'implémentation des algorithmes. En effet, tirer profit
  d'éléments tels que les différents niveaux de parallélisme accessibles (comme
  le parallélisme d'instructions et le parallélisme de fils d'exécution) ou
  encore la hiérarchie de mémoire a mené à des gains de performance
  significatifs dans plusieurs branches de l'informatique. Par exemple, les
  processeurs de type GPU, autrefois spécifiquement optimisés pour des tâches
  hautement parallélisables pour des rendus graphiques, sont maintenant
  largement utilisés pour réduire significativement le temps d'apprentissage des
  réseaux de neurones artificiels.

  Cette stratégie reste cependant quasi inédite en planification. Cette thèse
  présente des contributions visant à combler ce manque dans la littérature en
  améliorant l'implémentation des algorithmes de planification de MDPs de sorte à
  exploiter les caractéristiques des processeurs modernes.

  La première contribution est une représentation mémoire, appelée CSR-MDP,
  indépendante du choix de l'algorithme de résolution utilisé pour trouver la
  politique optimale du PDM. Cette structure vise à minimiser la consommation en
  mémoire et le nombre de défauts de cache lors du calcul d'une politique
  optimale. Cette méthode a permis des gains d'un facteur allant de 2.8 à 8.6,
  selon l'algorithme utilisé.

  La seconde contribution est un algorithme basé sur l'algorithme Topological
  Value Iteration (TVI), que nous appelons pcTVI (pour parallel-chained TVI).
  Cet algorithme permet d'exploiter plusieurs coeurs d'un CPU en parallélisant
  les calculs lors de la recherche d'une politique optimale. Les planificateurs
  parallèles existants ont pour désavantage de soit nécessiter une décomposition
  manuelle de l'espace d'états dépendante de chaque domaine de planification, ou
  de nécessiter beaucoup de communications inter fils d'exécution, ce qui réduit
  le gain de vitesse possible. L'algorithme proposé, pcTVI, a comme principal
  atout de n'avoir aucun de ces deux désavantages. Il a permis un facteur $20$
  d'accélération sur un ordinateur ayant 32 coeurs de calcul sur le domaine de
  planification testé.

  La troisième contribution consiste en deux algorithmes, eTVI et eiTVI,
  permettant d'exploiter au maximum la représentation mémoire CSR-MDP en
  réordonnant les états du PDM de sorte que les états qui doivent souvent être
  accédés consécutivement soient le plus près possible les uns des autres en
  mémoire. Ce faisant, le pourcentage de données utiles aux calculs actuels lors
  du chargement d'une ligne de cache augmente et le nombre de défauts de cache
  diminue, ce qui réduit également le temps de calcul. Ces algorithmes seuls ont
  permis des gains de vitesses d'un facteur 2.1 en moyenne sur les domaines testés.

  Ces trois contributions peuvent être combinées. Le planificateur en résultant
  a permis de diminuer le temps de calcul de plusieurs ordres de grandeur sur
  les instances des domaines de planification testés.

  Les domaines de planifications probabilistes standardisés --- par exemple,
  ceux utilisés lors de la compétition internationale de planification, l'IPC,
  ayant lieu à la conférence ICAPS --- ne couvrent pas toutes les propriétés
  topologiques possibles des PDM, ce qui peut rendre difficile la comparaison
  des algorithmes existants dans des contextes variés. Pour pallier ce problème,
  une quatrième contribution est proposée: un algorithme de génération de PDM
  synthétiques, pouvant générer des instances couvrant un vaste éventail de
  propriétés topologiques.

links:
  - type: pdf
    url: 'https://archipel.uqam.ca/18692/1/D4822.pdf'
  - type: slides
    url: 'slides.pdf'
  - name: Archipel
    url: https://archipel.uqam.ca/18692

# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: 'Smart'
  preview_only: false

---
