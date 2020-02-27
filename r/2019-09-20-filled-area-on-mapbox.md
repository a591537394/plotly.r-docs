---
description: How to make an area on Map in R with plotly.
display_as: maps
language: r
layout: base
name: Filled Area in Mapbox
order: 9
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/filled-area-on-mapbox/
thumbnail: thumbnail/area.jpg
---


### Mapbox Access Token

To plot on Mapbox maps with Plotly you *may* need a Mapbox account and a public [Mapbox Access Token](https://www.mapbox.com/studio). See our [Mapbox Map Layers](/r/mapbox-layers/) documentation for more information. If you're using a Chart Studio Enterprise server, please see additional instructions [here](https://help.plot.ly/mapbox-atlas).

### How to Show an Area on a Map

There are three different ways to show an area in a mapbox:
<ol>
    <li> Use [Scattermapbox](https://plot.ly/r/reference/#scattermapbox) trace and set [fill](https://plot.ly/r/reference/#scattermapbox-fill) attribute to 'toself'</li>
    <li> Use [Scattermapbox](https://plot.ly/r/reference/#scattermapbox) trace and define the corresponding geojson</li>
    <li> Use the new trace type: [Choroplethmapbox](https://plot.ly/r/mapbox-county-choropleth/) for mapbox cases, or [Choropleth](https://plot.ly/r/choropleth-maps/) trace for non-mapbox ones.</li>
</ol>

The following example uses the `Scattermapbox` trace and sets `fill = 'toself'`


```r
library(plotly)

fig <- plot_ly(
  fill = "toself",
  lon = c(-74, -70, -70, -74),
  lat = c(47, 47, 45, 45),
  type = 'scattermapbox',
  marker = list(size = 10, color = 'orange'),
  fillcolor = 'color') 
fig <- fig %>%
  layout(
    mapbox = list(
      style = "stamen-terrain",
      center = list(lon = -73, lat = 46),
      zoom = 5),
    showlegend = FALSE)

fig
```

<div id="htmlwidget-2b5b53cefc4af18bd685" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-2b5b53cefc4af18bd685">{"x":{"visdat":{"341a243b1ca8":["function () ","plotlyVisDat"]},"cur_data":"341a243b1ca8","attrs":{"341a243b1ca8":{"fill":"toself","lon":[-74,-70,-70,-74],"lat":[47,47,45,45],"marker":{"size":10,"color":"orange"},"fillcolor":"color","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapbox":{"style":"stamen-terrain","center":{"lon":-73,"lat":46},"zoom":5},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"fillcolor":"color","fill":"toself","lon":[-74,-70,-70,-74],"lat":[47,47,45,45],"marker":{"color":"orange","size":10,"line":{"color":"rgba(31,119,180,1)"}},"type":"scattermapbox","mode":"markers","name":"color","line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Provide Gaps on Map

The following example shows how to use missing values in your data to provide gap in your graph. To ignore the gap on your plot, take benefit of [connectorgaps](https://plot.ly/r/reference/#scattermapbox-connectgaps) attribute.


```r
library(plotly)

fig <- plot_ly(
  mode = "lines",
  fill = "toself",
  type = 'scattermapbox',
  lon = c(-10, -10, 8, 8, NaN, 30, 30, 50, 50, NaN, 100, 100, 80, 80),
  lat = c(30, 6, 6, 30, NaN, 20, 30, 30, 20, NaN, 40, 50, 50, 40)) 
fig <- fig %>%
layout(
  mapbox = list(
    style = "stamen-terrain",
    center = list(lon = 30, lat = 30),
    zoom = 2),
  showlegend = FALSE)

fig
```

<div id="htmlwidget-aa0aaf05d06aebba4f6a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-aa0aaf05d06aebba4f6a">{"x":{"visdat":{"341af1864d9":["function () ","plotlyVisDat"]},"cur_data":"341af1864d9","attrs":{"341af1864d9":{"mode":"lines","fill":"toself","lon":[-10,-10,8,8,null,30,30,50,50,null,100,100,80,80],"lat":[30,6,6,30,null,20,30,30,20,null,40,50,50,40],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapbox":{"style":"stamen-terrain","center":{"lon":30,"lat":30},"zoom":2},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"fillcolor":"rgba(31,119,180,0.5)","mode":"lines","fill":"toself","lon":[-10,-10,8,8,null,30,30,50,50,null,100,100,80,80],"lat":[30,6,6,30,null,20,30,30,20,null,40,50,50,40],"type":"scattermapbox","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Use the Corresponding Geojson

The second way is using the `scattermapbox` trace with the corresponding geojson.


```r
library(plotly)

fig <- plot_ly(
  type = 'scattermapbox',
  mode = "markers",
  lon = c(-73.605), lat = c(45.51),
  marker = list(size = 20, color = c("cyan"))) 
fig <- fig %>%
  layout(
    mapbox = list(
    style = "stamen-terrain",
    center = list(lon = -73.6, lat = 45.5),
    zoom = 12,
    layers = list(list(
    source = list(
      type = "FeatureCollection",
      features = list(list(
        type = "Feature",
        geometry = list(
          type = "MultiPolygon",
          coordinates = list(list(list(
            c(-73.606352888, 45.507489991), c(-73.606133883, 45.50687600),
            c(-73.605905904, 45.506773980), c(-73.603533905, 45.505698946),
            c(-73.602475870, 45.506856969), c(-73.600031904, 45.505696003),
            c(-73.599379992, 45.505389066), c(-73.599119902, 45.505632008),
            c(-73.598896977, 45.505514039), c(-73.598783894, 45.505617001),
            c(-73.591308727, 45.516246185), c(-73.591380782, 45.516280145),
            c(-73.596778656, 45.518690062), c(-73.602796770, 45.521348046),
            c(-73.612239983, 45.525564037), c(-73.612422919, 45.525642061),
            c(-73.617229085, 45.527751983), c(-73.617279234, 45.527774160),
            c(-73.617304713, 45.527741334), c(-73.617492052, 45.527498362),
            c(-73.617533258, 45.527512253), c(-73.618074188, 45.526759105),
            c(-73.618271651, 45.526500673), c(-73.618446320, 45.526287943),
            c(-73.618968507, 45.525698560), c(-73.619388002, 45.525216750),
            c(-73.619532966, 45.525064183), c(-73.619686662, 45.524889290),
            c(-73.619787038, 45.524770086), c(-73.619925742, 45.524584939),
            c(-73.619954486, 45.524557690), c(-73.620122362, 45.524377961),
            c(-73.620201713, 45.524298907), c(-73.620775593, 45.523650879)
            )))
            )
          ))
        ),
      type = "fill", below = "traces", color = "royalblue"))))

fig
```

<div id="htmlwidget-3830f9fd85c9d8f5a2ed" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3830f9fd85c9d8f5a2ed">{"x":{"visdat":{"341a6efd11d5":["function () ","plotlyVisDat"]},"cur_data":"341a6efd11d5","attrs":{"341a6efd11d5":{"mode":"markers","lon":-73.605,"lat":45.51,"marker":{"size":20,"color":"cyan"},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapbox":{"style":"stamen-terrain","center":{"lon":-73.6,"lat":45.5},"zoom":12,"layers":[{"source":{"type":"FeatureCollection","features":[{"type":"Feature","geometry":{"type":"MultiPolygon","coordinates":[[[[-73.606352888,45.507489991],[-73.606133883,45.506876],[-73.605905904,45.50677398],[-73.603533905,45.505698946],[-73.60247587,45.506856969],[-73.600031904,45.505696003],[-73.599379992,45.505389066],[-73.599119902,45.505632008],[-73.598896977,45.505514039],[-73.598783894,45.505617001],[-73.591308727,45.516246185],[-73.591380782,45.516280145],[-73.596778656,45.518690062],[-73.60279677,45.521348046],[-73.612239983,45.525564037],[-73.612422919,45.525642061],[-73.617229085,45.527751983],[-73.617279234,45.52777416],[-73.617304713,45.527741334],[-73.617492052,45.527498362],[-73.617533258,45.527512253],[-73.618074188,45.526759105],[-73.618271651,45.526500673],[-73.61844632,45.526287943],[-73.618968507,45.52569856],[-73.619388002,45.52521675],[-73.619532966,45.525064183],[-73.619686662,45.52488929],[-73.619787038,45.524770086],[-73.619925742,45.524584939],[-73.619954486,45.52455769],[-73.620122362,45.524377961],[-73.620201713,45.524298907],[-73.620775593,45.523650879]]]]}}]},"type":"fill","below":"traces","color":"royalblue"}]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"markers","lon":[-73.605],"lat":[45.51],"marker":{"color":"cyan","size":20,"line":{"color":"rgba(31,119,180,1)"}},"type":"scattermapbox","line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scattermapbox](https://plot.ly/r/reference/#scattermapbox) for more information and options!
