# Mapas Dinámicos: Rstudio

Este documento es una guía para crear mapas dinámicos de distintos países. El ejemplo presente usa como ejemplo el IVA promedio en 10 años.

## Cómo empezar

Para poder aplicar el código deber tomar en cuenta que los nombres de los países o de las regiones, deben estar homologadas con el formáto **ISO 3166-1 alfa-3** http://utils.mucattu.com/iso_3166-1.html. Dentro del proyecto puedes encontrar un excel con los valores que homologan los nombres en castellano con sus códigos correspondientes. 

```
packages <- c(
  "rvest",
  "reshape2",
  "DT",
  "highcharter",
  "dplyr",
  "plyr",
  "plotly")

install.packages(packages)
```

