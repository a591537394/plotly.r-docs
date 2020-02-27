---
description: How to create Ternary Contour Plots in R with Plotly.
display_as: scientific
language: r
layout: base
name: Ternary Contour Plot
order: 6
output:
  html_document:
    keep_md: true
permalink: r/ternary-contour/
thumbnail: thumbnail/ternary-contour.jpg
---


### Basic Terary Contour Plot


```r
library(plotly)
library(rjson)

df <- fromJSON(file="https://gist.githubusercontent.com/davenquinn/988167471993bc2ece29/raw/f38d9cb3dd86e315e237fde5d65e185c39c931c2/data.json") 

colors = c('#8dd3c7','#ffffb3','#bebada',
          '#fb8072','#80b1d3','#fdb462',
          '#b3de69','#fccde5','#d9d9d9',
          '#bc80bd','#ccebc5','#ffed6f');

fig <- plot_ly()

for (i in 1:length(df)) {
  l = c()
  m = c()
  n = c()
  
  for (j in 1:length(df[[i]])) {
    l[[j]] <- df[[i]][[j]]$clay
    m[[j]] <- df[[i]][[j]]$sand
    n[[j]] <- df[[i]][[j]]$silt
  }
  
 fig <- add_trace(
    fig,
    type = 'scatterternary',
    a = l,
    b = m,
    c = n,
    name = names(df[i]),
    mode = 'lines',
    line = list(
      color='#444'
    ),
    fill = 'toself',
    fillcolor = colors[i],
    showlegend = F
    )
}

fig <- layout(
  fig,
  title = "Simple Ternary Contour Plot in R",
  ternary = list(
    sum = 100,
    aaxis = list(
      title = "clay",
      ticksuffix = "%",
      min = 0.01,
      linewidth = 2,
      ticks = "outside"
    ),
    baxis = list(
      title = "sand",
      ticksuffix = "%",
      min = 0.01,
      linewidth = 2,
      ticks = "outside"
    ),
    caxis = list(
      title = "silt",
      ticksuffix = "%",
      min = 0.01,
      linewidth = 2,
      ticks = "outside"
    )
  )
)

fig
```

<div id="htmlwidget-bd81fe37d0b53aadf223" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-bd81fe37d0b53aadf223">{"x":{"visdat":{"2aaf3f8b49ef":["function () ","plotlyVisDat"]},"cur_data":"2aaf3f8b49ef","attrs":{"2aaf3f8b49ef":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[0,10,0],"b":[100,90,90],"c":[0,0,10],"name":"sand","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#8dd3c7","showlegend":false,"inherit":true},"2aaf3f8b49ef.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[0,10,15,0],"b":[90,90,85,70],"c":[10,0,0,30],"name":"loamy sand","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#ffffb3","showlegend":false,"inherit":true},"2aaf3f8b49ef.2":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[0,15,20,20,5,5,0],"b":[70,85,80,53,53,45,50],"c":[30,0,0,32,42,50,50],"name":"sandy loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#bebada","showlegend":false,"inherit":true},"2aaf3f8b49ef.3":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[20,35,35,28,20],"b":[80,65,45,45,53],"c":[0,0,20,27,32],"name":"sandy clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#fb8072","showlegend":false,"inherit":true},"2aaf3f8b49ef.4":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[35,35,55],"b":[65,45,45],"c":[0,20,0],"name":"sandy clay","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#80b1d3","showlegend":false,"inherit":true},"2aaf3f8b49ef.5":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[55,100,60,40,40],"b":[45,0,0,20,45],"c":[0,0,40,40,15],"name":"clay","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#fdb462","showlegend":false,"inherit":true},"2aaf3f8b49ef.6":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[40,40,28,28],"b":[45,20,20,45],"c":[15,40,52,27],"name":"clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#b3de69","showlegend":false,"inherit":true},"2aaf3f8b49ef.7":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[60,40,40],"b":[0,0,20],"c":[40,60,40],"name":"silty clay","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#fccde5","showlegend":false,"inherit":true},"2aaf3f8b49ef.8":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[28,28,40,40],"b":[0,20,20,0],"c":[72,52,40,60],"name":"silty clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#d9d9d9","showlegend":false,"inherit":true},"2aaf3f8b49ef.9":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[0,28,28,12,12,0],"b":[50,22,0,0,8,20],"c":[50,50,72,88,80,80],"name":"silty loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#bc80bd","showlegend":false,"inherit":true},"2aaf3f8b49ef.10":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[0,0,12,12],"b":[0,20,8,0],"c":[100,80,80,88],"name":"silt","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#ccebc5","showlegend":false,"inherit":true},"2aaf3f8b49ef.11":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","a":[28,28,5,5,20],"b":[45,22,45,53,53],"c":[27,50,50,42,32],"name":"loam","mode":"lines","line":{"color":"#444"},"fill":"toself","fillcolor":"#ffed6f","showlegend":false,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Simple Ternary Contour Plot in R","ternary":{"sum":100,"aaxis":{"title":"clay","ticksuffix":"%","min":0.01,"linewidth":2,"ticks":"outside"},"baxis":{"title":"sand","ticksuffix":"%","min":0.01,"linewidth":2,"ticks":"outside"},"caxis":{"title":"silt","ticksuffix":"%","min":0.01,"linewidth":2,"ticks":"outside"}},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"fillcolor":"#8dd3c7","type":"scatterternary","a":[0,10,0],"b":[100,90,90],"c":[0,0,10],"name":"sand","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"frame":null},{"fillcolor":"#ffffb3","type":"scatterternary","a":[0,10,15,0],"b":[90,90,85,70],"c":[10,0,0,30],"name":"loamy sand","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"frame":null},{"fillcolor":"#bebada","type":"scatterternary","a":[0,15,20,20,5,5,0],"b":[70,85,80,53,53,45,50],"c":[30,0,0,32,42,50,50],"name":"sandy loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"frame":null},{"fillcolor":"#fb8072","type":"scatterternary","a":[20,35,35,28,20],"b":[80,65,45,45,53],"c":[0,0,20,27,32],"name":"sandy clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"frame":null},{"fillcolor":"#80b1d3","type":"scatterternary","a":[35,35,55],"b":[65,45,45],"c":[0,20,0],"name":"sandy clay","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(148,103,189,1)","line":{"color":"rgba(148,103,189,1)"}},"frame":null},{"fillcolor":"#fdb462","type":"scatterternary","a":[55,100,60,40,40],"b":[45,0,0,20,45],"c":[0,0,40,40,15],"name":"clay","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(140,86,75,1)","line":{"color":"rgba(140,86,75,1)"}},"frame":null},{"fillcolor":"#b3de69","type":"scatterternary","a":[40,40,28,28],"b":[45,20,20,45],"c":[15,40,52,27],"name":"clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(227,119,194,1)","line":{"color":"rgba(227,119,194,1)"}},"frame":null},{"fillcolor":"#fccde5","type":"scatterternary","a":[60,40,40],"b":[0,0,20],"c":[40,60,40],"name":"silty clay","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(127,127,127,1)","line":{"color":"rgba(127,127,127,1)"}},"frame":null},{"fillcolor":"#d9d9d9","type":"scatterternary","a":[28,28,40,40],"b":[0,20,20,0],"c":[72,52,40,60],"name":"silty clay loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(188,189,34,1)","line":{"color":"rgba(188,189,34,1)"}},"frame":null},{"fillcolor":"#bc80bd","type":"scatterternary","a":[0,28,28,12,12,0],"b":[50,22,0,0,8,20],"c":[50,50,72,88,80,80],"name":"silty loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(23,190,207,1)","line":{"color":"rgba(23,190,207,1)"}},"frame":null},{"fillcolor":"#ccebc5","type":"scatterternary","a":[0,0,12,12],"b":[0,20,8,0],"c":[100,80,80,88],"name":"silt","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"frame":null},{"fillcolor":"#ffed6f","type":"scatterternary","a":[28,28,5,5,20],"b":[45,22,45,53,53],"c":[27,50,50,42,32],"name":"loam","mode":"lines","line":{"color":"#444"},"fill":"toself","showlegend":false,"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scatterternary](https://plot.ly/r/reference/#scatterternary) for more information and options!
