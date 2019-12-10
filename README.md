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
EL paquete highcharter es un paquete de Rstudio para crear gráficos dinámicos, dentro de estos gráficos existen algunos ejemplos de mapas:
http://jkunst.com/highcharter/index.html

Por otro lado https://code.highcharts.com/mapdata/ nos muestra la colección de mapas que existen dentro del repositorio en distintos formatos, en base a estos mapas podemos crear mapas dinámicos.

Al llamar a la función hcmap "custom/world-robinson", deber incluir la ruta del mapa que quieres extraer de la página web. 

```
mapas <- map %>%
  select(pais =`hc-a2`) %>% 
  mutate(X=map$media)


hcmap("custom/world-robinson", data = mapas, value = "X",
      joinBy = c("hc-a2", "pais"), name = "IVA",
      dataLabels = list(enabled = TRUE, format = '{point.name}'),
      borderColor = "#FAFAFA", borderWidth = 0.5,
      tooltip = list(valueDecimals = 0, valueSuffix = "%")) %>%
  hc_mapNavigation(enabled = TRUE) %>%
  hc_colorAxis(minColor = "#CCCCCC", maxColor = "#009999")%>%
  hc_title(text = "Mapa dinámico IVA Países (media de 2008 - 2018)",
           align = "center", style = list(color = "#000000", fontWeight = "bold"))
 ```
