---
title: Planification de chemins couvrants
summary: Ce projet visait à développer des planificateurs optimaux de chemins-couvrants. Dans le futur, il est également prévu de développer un planificateur considérant des contraintes énergétiques, de l'incertitude, ainsi que fonctionnant dans des environnements dynamiques.
tags: [Deterministic Planning, Heuristic Search, Branch-and-Bound]
date: "2023-04-29T00:00:00Z"

image:
  caption: Exemple d'une grille 9x14 résolue grâce à l'algorithme du front d'onde.
  focal_point: Smart

links:
  - type: code
    url: 'https://gitlab.info.uqam.ca/champagne_gareau.jael/cpp'

---

Un problème étudié en planification est le **problème de planification de
chemins couvrants** (*Coverage Path Planning*, CPP). Ce problème consiste à
trouver un chemin qui permet d'explorer l'entièreté d'une région en respectant
des contraintes (ex.: éviter des obstacles fixes, utiliser des mouvements
simples, etc.), et ce, en minimisant le temps de parcours (ou le nombre de
mouvements). Ce problème apparaît dans plusieurs contextes, comme la recherche
et sauvetage (*search and rescue*), le déminage, la reconstitution en 3D de
régions survolées par un drone, l'exploration sous-marine avec des véhicules
sous-marins autonomes (*Autonomous Underwater Vehicles*, AUV), le nettoyage de
planchers ou de fenêtres, et l'impression 3D.

Malheureusement, aucun planificateur optimal n'existe dans la littérature (autre
que la solution naïve). De plus, aucun planificateur de chemins couvrants ne
considère l'incertitude, la gestion de ressources et les environnements
dynamiques. Dans ce projet, nous avons développé une [Librairie C++ de
CPP](https://gitlab.info.uqam.ca/champagne_gareau.jael/cpp) qui contient des
algorithmes classiques, tel que l'algorithme du front d'onde, de même que notre
planificateur optimal qui utilise la recherche heuristique ainsi que des
méthodes séparation-évaluation (*branch-and-bound*).
