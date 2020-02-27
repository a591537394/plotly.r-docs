---
description: How to create carpet plots in R with Plotly.
display_as: scientific
language: r
layout: base
name: Carpet Scatter Plot
order: 9
output:
  html_document:
    keep_md: true
permalink: r/carpet-scatter/
thumbnail: thumbnail/scattercarpet.jpg
---


### Basic Carpet Plot


```r
library(plotly)

fig <- plot_ly(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
      ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
      )
    )

fig
```

<div id="htmlwidget-866d86c8148308485088" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-866d86c8148308485088">{"x":{"visdat":{"29d4d95ebed":["function () ","plotlyVisDat"]},"cur_data":"29d4d95ebed","attrs":{"29d4d95ebed":{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"carpet","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Add Carpet Scatter Trace


```r
library(plotly)

fig <- plot_ly(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
      ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
      )
    )
fig <- fig %>% add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(2.5, 2.5, 2.5, 2.5),
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = 'blue'
    ),
    marker = list(color = "blue")
  )

fig
```

<div id="htmlwidget-6ee7333b88889db88ce1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6ee7333b88889db88ce1">{"x":{"visdat":{"29d448d4e990":["function () ","plotlyVisDat"]},"cur_data":"29d448d4e990","attrs":{"29d448d4e990":{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet"},"29d448d4e990.1":{"a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","line":{"shape":"spline","smoothing":1,"color":"blue"},"marker":{"color":"blue"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"carpet","xaxis":"x","yaxis":"y","frame":null},{"a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"scattercarpet","line":{"color":"blue","shape":"spline","smoothing":1},"marker":{"color":"blue","line":{"color":"rgba(255,127,14,1)"}},"mode":"markers+lines","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Adding Multiple Traces


```r
library(plotly)

fig <- plot_ly()
fig <- fig %>% add_trace(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
    ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
    )
  )
fig <- fig %>% add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(2.5, 2.5, 2.5, 2.5),
    mode = 'markers+lines',
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = "blue"
    ),
    marker = list(color = "blue")
  )
fig <- fig %>% add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(1.5, 1.5, 1.5, 1.5),
    mode = 'lines',
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = "green"
    )
  )
fig <- fig %>% add_trace(
    type = 'scattercarpet',
    a = c(5, 5, 5, 5),
    b = c(1, 1.5, 2, 3),
    mode = 'markers',
    marker = list(
      color = "red",
      size = c(0,0,20,0)
    )
  )
fig <- fig %>% add_trace(
    type = 'scattercarpet',
    a = c(4.5, 4.5, 4.5, 4.5),
    b = c(1, 1.5, 2, 3),
    mode = 'markers',
    marker = list(
      color = "black",
      size = c(0,0,30,0)
    )
  )

fig
```

<div id="htmlwidget-53e5ba851c03810fee39" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-53e5ba851c03810fee39">{"x":{"visdat":{"29d44d91fc70":["function () ","plotlyVisDat"]},"cur_data":"29d44d91fc70","attrs":{"29d44d91fc70":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet","a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"inherit":true},"29d44d91fc70.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"mode":"markers+lines","line":{"shape":"spline","smoothing":1,"color":"blue"},"marker":{"color":"blue"},"inherit":true},"29d44d91fc70.2":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4,4.5,5,6],"b":[1.5,1.5,1.5,1.5],"mode":"lines","line":{"shape":"spline","smoothing":1,"color":"green"},"inherit":true},"29d44d91fc70.3":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[5,5,5,5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"red","size":[0,0,20,0]},"inherit":true},"29d44d91fc70.4":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4.5,4.5,4.5,4.5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"black","size":[0,0,30,0]},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"carpet","a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"mode":"markers+lines","line":{"color":"blue","shape":"spline","smoothing":1},"marker":{"color":"blue","line":{"color":"rgba(255,127,14,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4,4.5,5,6],"b":[1.5,1.5,1.5,1.5],"mode":"lines","line":{"color":"green","shape":"spline","smoothing":1},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[5,5,5,5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"red","size":[0,0,20,0],"line":{"color":"rgba(214,39,40,1)"}},"line":{"color":"rgba(214,39,40,1)"},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4.5,4.5,4.5,4.5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"black","size":[0,0,30,0],"line":{"color":"rgba(148,103,189,1)"}},"line":{"color":"rgba(148,103,189,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scattercarpet](https://plot.ly/r/reference/#scattercarpet) for more information and options!
