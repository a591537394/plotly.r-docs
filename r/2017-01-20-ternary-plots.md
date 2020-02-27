---
description: How to create ternary plots in R with Plotly.
display_as: scientific
language: r
layout: base
name: Ternary Plots
order: 14
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/ternary-plots/
thumbnail: thumbnail/ternary.jpg
---


### Basic Ternary Plot with Markers


```r
library(plotly)

journalist <- c(75,70,75,5,10,10,20,10,15,10,20)
developer <- c(25,10,20,60,80,90,70,20,5,10,10)
designer <- c(0,20,5,35,10,0,10,70,80,80,70)
label <- c('point 1','point 2','point 3','point 4','point 5','point 6',
           'point 7','point 8','point 9','point 10','point 11')


df <- data.frame(journalist,developer,designer,label)

# axis layout
axis <- function(title) {
  list(
    title = title,
    titlefont = list(
      size = 20
    ),
    tickfont = list(
      size = 15
    ),
    tickcolor = 'rgba(0,0,0,0)',
    ticklen = 5
  )
}


fig <- df %>% plot_ly()
fig <- fig %>% add_trace(
    type = 'scatterternary',
    mode = 'markers',
    a = ~journalist,
    b = ~developer,
    c = ~designer,
    text = ~label,
    marker = list( 
      symbol = 100,
      color = '#DB7365',
      size = 14,
      line = list('width' = 2)
    )
  )
fig <- fig %>% layout(
    title = "Simple Ternary Plot with Markers",
    ternary = list(
      sum = 100,
      aaxis = axis('Journalist'),
      baxis = axis('Developer'),
      caxis = axis('Designer')
    )
  )

fig
```

<div id="htmlwidget-212d18856e047bf8bb88" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-212d18856e047bf8bb88">{"x":{"visdat":{"2750f184c38":["function () ","plotlyVisDat"]},"cur_data":"2750f184c38","attrs":{"2750f184c38":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterternary","mode":"markers","a":{},"b":{},"c":{},"text":{},"marker":{"symbol":100,"color":"#DB7365","size":14,"line":{"width":2}},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Simple Ternary Plot with Markers","ternary":{"sum":100,"aaxis":{"title":"Journalist","titlefont":{"size":20},"tickfont":{"size":15},"tickcolor":"rgba(0,0,0,0)","ticklen":5},"baxis":{"title":"Developer","titlefont":{"size":20},"tickfont":{"size":15},"tickcolor":"rgba(0,0,0,0)","ticklen":5},"caxis":{"title":"Designer","titlefont":{"size":20},"tickfont":{"size":15},"tickcolor":"rgba(0,0,0,0)","ticklen":5}},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"scatterternary","mode":"markers","a":[75,70,75,5,10,10,20,10,15,10,20],"b":[25,10,20,60,80,90,70,20,5,10,10],"c":[0,20,5,35,10,0,10,70,80,80,70],"text":["point 1","point 2","point 3","point 4","point 5","point 6","point 7","point 8","point 9","point 10","point 11"],"marker":{"color":"#DB7365","symbol":100,"size":14,"line":{"color":"rgba(31,119,180,1)","width":2}},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scatterternary](https://plot.ly/r/reference#scatterternary) for more information and options!
