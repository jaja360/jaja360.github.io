---
# Documentation: https://docs.hugoblox.com/reference/content-types/#publications

title: Planification d'itinéraires pour véhicule électrique avec disponibilité incertaine des bornes de recharge
subtitle: ''
authors:
- admin
author_notes: []
tags: [Electric Vehicles, Contingency Planning, Deterministic Planning, Graph Relabeling]
categories: []
projects: [veplan]
date: '2019-12-01'
lastmod: 2022-07-16T19:44:02-04:00
publishDate: '2022-04-16T20:44:02.661609Z'
featured: false
draft: false

publication: "Université du Québec à Montréal"

publication_types:
- thesis
genre: Master

summary: ''
abstract: "Un planificateur automatique étant capable de donner aisément et
rapidement des itinéraires pour véhicule électrique s'avère nécessaire
considérant le nombre croissant de ces véhicules en circulation et le peu de
bornes de recharge disponibles. Ce planificateur devrait être en mesure de tenir
compte de plusieurs facteurs, tels que l'emplacement des bornes de recharge et
leur probabilité d'occupation, le modèle stochastique de charge-décharge de la
batterie ou encore, la topographie ou même la température. En plus de considérer
les facteurs précédents, la rapidité de calcul et la simplicité d'utilisation
sont primordiales pour un planificateur digne de ce nom. Ce mémoire vise dans un
premier temps à présenter les caractéristiques du problème et les difficultés
reliées à ce problème. Dans un second temps, il vise à présenter les forces et
les faiblesses des planificateurs existants pour véhicule électrique et à
présenter en détail les algorithmes utilisés par ceux-ci. Dans un troisième
temps, il présente deux contributions nouvelles. La première est une technique
de regroupement de bornes permettant de diminuer le temps de calcul de chaque
requête par le planificateur. Cette technique a permis de diviser par 8 le
nombre de noeuds considérés dans le graphe des bornes et de diviser par 35 le
temps de calcul de la recherche de chemins dans ce graphe. La seconde technique
permet de considérer le temps espéré d'attente à chaque borne dans le
planificateur, alors que les planificateurs existants ne prenaient en compte que
le temps de déplacement et le temps de recharge. La considération du temps
d'attente par le planificateur a permis de diminuer de 17,3 minutes en moyenne
le temps total d'exécution des itinéraires retournés. Cette technique utilise
un modèle probabiliste permettant d'estimer l'occupation des bornes et le temps
espéré d'attente, qui a été généré à partir de données réelles du circuit
électrique, le réseau public de bornes de recharges au Québec."

# Links
url_pdf: 'https://archipel.uqam.ca/13780'
url_code: ''
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
