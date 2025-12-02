---
title: Electric Vehicles Planning
summary: This project aimed at creating an EV planner that considers not only the travel time and charging time, but also the waiting time at the charging stations.
tags: [Electric Vehicles, Deterministic Planning]
date: "2019-09-01T00:00:00Z"

image:
  caption: EVs charging at a public station in Montréal
  focal_point: Smart

links:
  - type: code
    url: 'https://gitlab.info.uqam.ca/champagne_gareau.jael/veplan'

---

Electric vehicles (EVs) are an attractive alternative to fossil-fuel vehicles to
reduce greenhouse gas emissions. However, their limited range and their high
charging time represent a major obstacle to their massive adoption. Moreover,
long journeys require careful planning to determine the charging stations to be
used in order to avoid running out of energy. For example, today (year 2019),
affordable EVs have an average range of around 250 km. This limited range
implies the need to make recharging stops many times on long journeys.

EV journey planning (EVJP) is a complex problem which cannot be effectively
solved by conventional approaches. Indeed, EV planners need to take into account
not only various driving factors applicable to conventional vehicles (the wind,
the energy needed to fight the air resistance relative to the speed, the
traffic, eventual detours, etc.), but also factors specific to EVs, such as the
level of charging stations (which influences the charging speed), the
non-linearity of the charging curve of the battery, the topography of the map
(EVs can recover some energy when moving downhill), the probability of the
stations' occupancy as well as the expected waiting time at the charging
stations.

While many of these factors have been addressed by previous studies, very few of
them have considered the waiting time in the objective function to minimize.
This factor is increasingly important because in many countries, the number of
EVs on the road increases faster than the number of charging
stations. The waiting time will thus probably continue to increase at the
majority of the stations for some time.

{{< figure src="./veplan_site.png" caption="User Interface of veplan.uqam.ca" >}}

In this project, we developed a [C++ EV
planner](https://gitlab.info.uqam.ca/champagne_gareau.jael/veplan) and a [web
frontend](https://veplan.jaelgareau.com) that considers the travel time, the
waiting time and the charging time when computing an EV journey.
