---
name: Multiple Axes
permalink: r/multiple-axes/
description: How to make a graph with multiple axes in R with Plotly.
layout: base
thumbnail: thumbnail/multiple-axes.jpg
language: r
page_type: example_index
display_as: multiple_axes
order: 1
output:
  html_document:
    keep_md: true
---


### Multiple Y Axes


```r
library(plotly)
ay <- list(
  tickfont = list(color = "red"),
  overlaying = "y",
  side = "right",
  title = "second y axis"
)
fig <- plot_ly()
fig <- fig %>% add_lines(x = ~1:3, y = ~10*(1:3), name = "slope of 10")
fig <- fig %>% add_lines(x = ~2:4, y = ~1:3, name = "slope of 1", yaxis = "y2")
fig <- fig %>% layout(
    title = "Double Y Axis", yaxis2 = ay,
    xaxis = list(title="x")
  )

fig
```

<div id="htmlwidget-a16dbeb2d97aa6502930" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-a16dbeb2d97aa6502930">{"x":{"visdat":{"1ccf60409bbc":["function () ","plotlyVisDat"]},"cur_data":"1ccf60409bbc","attrs":{"1ccf60409bbc":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 10","inherit":true},"1ccf60409bbc.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Double Y Axis","yaxis2":{"tickfont":{"color":"red"},"overlaying":"y","side":"right","title":"second y axis"},"xaxis":{"domain":[0,1],"automargin":true,"title":"x"},"yaxis":{"domain":[0,1],"automargin":true,"title":"10 * (1:3)"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[10,20,30],"type":"scatter","mode":"lines","name":"slope of 10","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2,3,4],"y":[1,2,3],"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
