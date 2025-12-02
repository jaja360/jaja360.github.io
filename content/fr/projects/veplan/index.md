---
title: Planification d'itinéraires pour véhicules électriques
summary: Ce projet visait à créer un planification pour VÉs qui considère à la fois le temps de déplacement, le temps de recharge, et le temps d'attente aux bornes.
tags: [Electric Vehicles, Deterministic Planning]
date: "2019-09-01T00:00:00Z"

image:
  caption: Des véhicules électriques en train de se charger à Montréal
  focal_point: Smart

links:
  - type: code
    url: 'https://gitlab.info.uqam.ca/champagne_gareau.jael/veplan'

---

Un planificateur automatique étant capable de donner aisément et rapidement des
itinéraires pour véhicules électriques s'avère nécessaire considérant le nombre
croissant de ces véhicules en circulation et le peu de bornes de recharge
disponibles. Ce planificateur devrait être en mesure de tenir compte de
plusieurs facteurs, tels que l'emplacement des bornes de recharge et leur
probabilité d'occupation, le modèle stochastique de charge-décharge de la
batterie ou encore, la topographie ou même la température. En plus de considérer
les facteurs précédents, la rapidité de calcul et la simplicité d'utilisation
sont primordiales pour un planificateur digne de ce nom.

Ce projet a mené à deux contributions scientifiques. La première est une
technique de regroupement de bornes permettant de diminuer le temps de calcul de
chaque requête par le planificateur. Cette technique a permis de diviser par 8
le nombre de noeuds considérés dans le graphe des bornes et de diviser par 35
le temps de calcul de la recherche de chemins dans ce graphe. La seconde
technique permet de considérer le temps espéré d'attente à chaque borne dans le
planificateur, alors que les planificateurs existants ne prenaient en compte que
le temps de déplacement et le temps de recharge. La considération du temps
d'attente par le planificateur a permis de diminuer de 17,3 minutes en moyenne
le temps total d'exécution des itinéraires retournés. Cette technique utilise
un modèle probabiliste permettant d'estimer l'occupation des bornes et le temps
espéré d'attente, qui a été généré à partir de données réelles du circuit
électrique, le réseau public de bornes de recharges au Québec.

{{< figure src="./veplan_site.png" caption="Interface du site veplan.uqam.ca" >}}

Dans ce projet, nous avons développé un [Planificateur d'itinéraires pour VÉ en
C++](https://gitlab.info.uqam.ca/champagne_gareau.jael/veplan) ainsi qu'une
[interface web permettant d'utiliser le planificateur](https://veplan.jaelgareau.com)
qui considère le temps de déplacement, le temps de charge et le temps d'attente
aux bornes lors du calcul des itinéraires.
