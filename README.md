
---
title: "Light vehicle charging infrastructure - Renault network (or a map created  with leaflet R package)" 
author: "Olivier Cazin"
date: "28 juin 2017"
output:
  html_document:
    fig_caption: yes
    keep_md: yes
  pdf_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
setwd("~/PRIVE - DOSSIERS/MOOC/MOOC - 9 - Developing Data Products - COURSERA")
```

In the context of Data Products Course Assignment 1 of Coursera, a map is created with leaflet R package from a list of GPS coordinates of charging stations for light electric vehicles accessible outside the concessions. These Open Data can be downloaded here : <https://www.data.gouv.fr/storage/f/2014-09-15T11-59-56/d-localdata-a186081-desktop-infra-recharge-reseau-renault-france.csv>

```{r,warning=FALSE}

# packages loaded
library(leaflet)
library(utils)

# file downloaded and read (open data)
data_lyon <- read.csv2("https://www.data.gouv.fr/storage/f/2014-09-15T11-59-56/d-localdata-a186081-desktop-infra-recharge-reseau-renault-france.csv")

# leaflet package used
m <- leaflet(data=data_lyon) 
m <- addTiles(m) 
m <- addCircleMarkers(m,lng=~latitude_WSG84,lat=~longitude_WSG84,color = "black", weight = 1, stroke = T, fillColor = 'purple', fillOpacity = 0.5, radius =5,popup=~as.character(nom_station),label=~as.character(nom_station))
m
```
