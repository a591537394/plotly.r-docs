---
name: Funnel Charts
permalink: r/funnel-charts/
description: How to create a Funnel Chart in R with Plotly
layout: base
thumbnail: thumbnail/funnel.jpg
language: r
page_type: u-guide
display_as: financial
order: 6
output:
  html_document:
    keep_md: true
---



### Introduction
Funnel charts are often used to represent data in different stages of a business process. It’s an important mechanism in Business Intelligence to identify potential problem areas of a process. For example, it’s used to observe the revenue or loss in a sales process for each stage, and displays values that are decreasing progressively. Each stage is illustrated as a percentage of the total of all values.

### Basic Funnel Plot


```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly() 
fig <- fig %>%
  add_trace(
  type = "funnel",
  y = c("Website visit", "Downloads", "Potential customers", "Requested price", "invoice sent"),
  x = c(39, 27.4, 20.6, 11, 2)) 
fig <- fig %>%
  layout(yaxis = list(categoryarray = c("Website visit", "Downloads", "Potential customers", "Requested price", "invoice sent")))

fig
```

<div id="htmlwidget-32b78c1f95a21184c4aa" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-32b78c1f95a21184c4aa">{"x":{"visdat":{"33d84a0d47f6":["function () ","plotlyVisDat"]},"cur_data":"33d84a0d47f6","attrs":{"33d84a0d47f6":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","y":["Website visit","Downloads","Potential customers","Requested price","invoice sent"],"x":[39,27.4,20.6,11,2],"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"categoryarray":["Website visit","Downloads","Potential customers","Requested price","invoice sent"],"title":[],"type":"category","categoryorder":"array"},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"funnel","y":["Website visit","Downloads","Potential customers","Requested price","invoice sent"],"x":[39,27.4,20.6,11,2],"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Setting Marker Size and Color
This example uses [textposition](https://plot.ly/python/reference/#scatter-textposition) and [textinfo](https://plot.ly/python/reference/#funnel-textinfo) to determine information apears on the graph, and shows how to customize the bars.


```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly() 
fig <- fig %>%
  add_trace(type = "funnel",
            y = c("Website visit", "Downloads", "Potential customers", "Requested price", "Finalized"),
            x = c(39, 27.4, 20.6, 11, 2),
            textposition = "inside",
            textinfo = "value+percent initial",
            opacity = 0.65,
            marker = list(color = c("deepskyblue", "lightsalmon", "tan", "teal", "silver"),
                          line = list(width = c(4, 2, 2, 3, 1, 1), color = c("wheat", "wheat", "blue", "wheat", "wheat"))),
            connector = list(line = list(color = "royalblue", dash = "dot", width = 3))) 
fig <- fig %>%
  layout(yaxis = list(categoryarray = c("Website visit", "Downloads", "Potential customers", "Requested price", "Finalized")))

fig
```

<div id="htmlwidget-3fa6abc04c08734471ca" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3fa6abc04c08734471ca">{"x":{"visdat":{"33d8295a9fa6":["function () ","plotlyVisDat"]},"cur_data":"33d8295a9fa6","attrs":{"33d8295a9fa6":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","y":["Website visit","Downloads","Potential customers","Requested price","Finalized"],"x":[39,27.4,20.6,11,2],"textposition":"inside","textinfo":"value+percent initial","opacity":0.65,"marker":{"color":["deepskyblue","lightsalmon","tan","teal","silver"],"line":{"width":[4,2,2,3,1,1],"color":["wheat","wheat","blue","wheat","wheat"]}},"connector":{"line":{"color":"royalblue","dash":"dot","width":3}},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"categoryarray":["Website visit","Downloads","Potential customers","Requested price","Finalized"],"title":[],"type":"category","categoryorder":"array"},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"funnel","y":["Website visit","Downloads","Potential customers","Requested price","Finalized"],"x":[39,27.4,20.6,11,2],"textposition":["inside","inside","inside","inside","inside"],"textinfo":"value+percent initial","opacity":0.65,"marker":{"color":["deepskyblue","lightsalmon","tan","teal","silver"],"line":{"color":["wheat","wheat","blue","wheat","wheat"],"width":[4,2,2,3,1,1]}},"connector":{"line":{"color":"royalblue","dash":"dot","width":3}},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Stacked Funnel Plot


```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly(
    type = "funnel",
    name = 'Montreal',
    y = c("Website visit", "Downloads", "Potential customers", "Requested price"),
    x = c(120, 60, 30, 20),
    textinfo = "value+percent initial") 
fig <- fig %>%
  add_trace(
    type = "funnel",
    name = 'Toronto',
    orientation = "h",
    y = c("Website visit", "Downloads", "Potential customers", "Requested price", "invoice sent"),
    x = c(100, 60, 40, 30, 20),
    textposition = "inside",
    textinfo = "value+percent previous") 
fig <- fig %>%
  add_trace(
    type = "funnel",
    name = 'Vancouver',
    orientation = "h",
    y = c("Website visit", "Downloads", "Potential customers", "Requested price", "invoice sent", "Finalized"),
  x = c(90, 70, 50, 30, 10, 5),
  textposition = "outside",
  textinfo = "value+percent total") 
fig <- fig %>%
  layout(yaxis = list(categoryarray = c("Website visit", "Downloads", "Potential customers", "Requested price", "invoice sent", "Finalized")))

fig
```

<div id="htmlwidget-1f7755be0612f1d626d3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1f7755be0612f1d626d3">{"x":{"visdat":{"33d858ed9980":["function () ","plotlyVisDat"]},"cur_data":"33d858ed9980","attrs":{"33d858ed9980":{"y":["Website visit","Downloads","Potential customers","Requested price"],"x":[120,60,30,20],"textinfo":"value+percent initial","name":"Montreal","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel"},"33d858ed9980.1":{"y":["Website visit","Downloads","Potential customers","Requested price","invoice sent"],"x":[100,60,40,30,20],"textinfo":"value+percent previous","name":"Toronto","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","orientation":"h","textposition":"inside","inherit":true},"33d858ed9980.2":{"y":["Website visit","Downloads","Potential customers","Requested price","invoice sent","Finalized"],"x":[90,70,50,30,10,5],"textinfo":"value+percent total","name":"Vancouver","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnel","orientation":"h","textposition":"outside","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"categoryarray":["Website visit","Downloads","Potential customers","Requested price","invoice sent","Finalized"],"title":[],"type":"category","categoryorder":"array"},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"y":["Website visit","Downloads","Potential customers","Requested price"],"x":[120,60,30,20],"textinfo":"value+percent initial","name":"Montreal","type":"funnel","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"y":["Website visit","Downloads","Potential customers","Requested price","invoice sent"],"x":[100,60,40,30,20],"textinfo":"value+percent previous","name":"Toronto","type":"funnel","orientation":"h","textposition":["inside","inside","inside","inside","inside"],"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"y":["Website visit","Downloads","Potential customers","Requested price","invoice sent","Finalized"],"x":[90,70,50,30,10,5],"textinfo":"value+percent total","name":"Vancouver","type":"funnel","orientation":"h","textposition":["outside","outside","outside","outside","outside","outside"],"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Basic Area Funnel Plot


```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly(
  type = "funnelarea",
  text = c("The 1st","The 2nd", "The 3rd", "The 4th", "The 5th"),
  values = c(5, 4, 3, 2, 1))

fig
```

<div id="htmlwidget-65a0fc56917e6f7ebdc3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-65a0fc56917e6f7ebdc3">{"x":{"visdat":{"33d87ba3f8ff":["function () ","plotlyVisDat"]},"cur_data":"33d87ba3f8ff","attrs":{"33d87ba3f8ff":{"text":["The 1st","The 2nd","The 3rd","The 4th","The 5th"],"values":[5,4,3,2,1],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"text":["The 1st","The 2nd","The 3rd","The 4th","The 5th"],"values":[5,4,3,2,1],"type":"funnelarea","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Set Marker Size and Color in Area Funnel Plots

```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly(
  type = "funnelarea",
  values = c(5, 4, 3, 2, 1),
  text = c("The 1st","The 2nd", "The 3rd", "The 4th", "The 5th"),
  marker = list(colors = c("deepskyblue", "lightsalmon", "tan", "teal", "silver"),
                line = list(color = c("wheat", "wheat", "blue", "wheat", "wheat"), width = c(0, 1, 5, 0, 4))),
  textfont = list(family = "Old Standard TT, serif", size = 13, color = "black"),
  opacity = 0.65)

fig
```

<div id="htmlwidget-e17954ce38b872e59462" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e17954ce38b872e59462">{"x":{"visdat":{"33d839fbd7c3":["function () ","plotlyVisDat"]},"cur_data":"33d839fbd7c3","attrs":{"33d839fbd7c3":{"values":[5,4,3,2,1],"text":["The 1st","The 2nd","The 3rd","The 4th","The 5th"],"marker":{"colors":["deepskyblue","lightsalmon","tan","teal","silver"],"line":{"color":["wheat","wheat","blue","wheat","wheat"],"width":[0,1,5,0,4]}},"textfont":{"family":"Old Standard TT, serif","size":13,"color":"black"},"opacity":0.65,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[5,4,3,2,1],"text":["The 1st","The 2nd","The 3rd","The 4th","The 5th"],"marker":{"color":"rgba(31,119,180,1)","colors":["deepskyblue","lightsalmon","tan","teal","silver"],"line":{"color":["wheat","wheat","blue","wheat","wheat"],"width":[0,1,5,0,4]}},"textfont":{"family":"Old Standard TT, serif","size":13,"color":"black"},"opacity":0.65,"type":"funnelarea","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Multiple Area Funnels

```r
# Need to install plotly from Github to get funnel plots
# devtools::install_github("ropensci/plotly")
library(plotly)

fig <- plot_ly(
    type = "funnelarea",
    scalegroup = "first",
    values = c(500, 450, 340, 230, 220, 110),
    textinfo = "value",
    title = list(position = "top center", text = "Sales for Sale Person A in U.S."),
    domain = list(x = c(0.01, 0.48), y =c(0, 0.5))) 
fig <- fig %>%
  add_trace(
    type = "funnelarea",
    scalegroup = "first",
    values = c(600, 500, 400, 300, 200, 100),
    textinfo = "value",
    title = list(position = "top center", text = "Sales of Sale Person B in Canada"),
    domain = list(x = c(0.01, 0.48), y = c(0.56, 1))) 
fig <- fig %>%
  add_trace(
    type = "funnelarea",
    scalegroup = "second",
    values = c(510, 480, 440, 330, 220, 100),
    textinfo = "value",
    title = list(position = "top left", text = "Sales of Sale Person A in Canada"),
    domain = list(x = c(0.56, 0.98), y = c(0, 0.5))) 
fig <- fig %>%
  add_trace(
    type = "funnelarea",
    scalegroup = "second",
    values = c(360, 250, 240, 130, 120, 60),
    textinfo = "value",
    title = list(position = "top left", text = "Sales of Sale Person B in U.S."),
    domain = list(x = c(0.56, 0.98), y = c(0.56, 1))) 
fig <- fig %>%
  layout(
    margin = list(l= 200, r= 200), shapes = list(
      list(x0 = 0, x1 = 0.5, y0 = 0, y1 = 0.5),
      list(x0 = 0, x1 = 0.5, y0 = 0.55, y1 = 1),
      list(x0 = 0.55, x1 = 1, y0 = 0, y1 = 0.5),
      list(x0 = 0.55, x1 = 1, y0 = 0.55, y1 = 1)))

fig
```

<div id="htmlwidget-fcee075370799c21d4bd" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-fcee075370799c21d4bd">{"x":{"visdat":{"33d818e0a16":["function () ","plotlyVisDat"]},"cur_data":"33d818e0a16","attrs":{"33d818e0a16":{"scalegroup":"first","values":[500,450,340,230,220,110],"textinfo":"value","title":{"position":"top center","text":"Sales for Sale Person A in U.S."},"domain":{"x":[0.01,0.48],"y":[0,0.5]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea"},"33d818e0a16.1":{"scalegroup":"first","values":[600,500,400,300,200,100],"textinfo":"value","title":{"position":"top center","text":"Sales of Sale Person B in Canada"},"domain":{"x":[0.01,0.48],"y":[0.56,1]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea","inherit":true},"33d818e0a16.2":{"scalegroup":"second","values":[510,480,440,330,220,100],"textinfo":"value","title":{"position":"top left","text":"Sales of Sale Person A in Canada"},"domain":{"x":[0.56,0.98],"y":[0,0.5]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea","inherit":true},"33d818e0a16.3":{"scalegroup":"second","values":[360,250,240,130,120,60],"textinfo":"value","title":{"position":"top left","text":"Sales of Sale Person B in U.S."},"domain":{"x":[0.56,0.98],"y":[0.56,1]},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"funnelarea","inherit":true}},"layout":{"margin":{"b":40,"l":200,"t":25,"r":200},"shapes":[{"x0":0,"x1":0.5,"y0":0,"y1":0.5},{"x0":0,"x1":0.5,"y0":0.55,"y1":1},{"x0":0.55,"x1":1,"y0":0,"y1":0.5},{"x0":0.55,"x1":1,"y0":0.55,"y1":1}],"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"scalegroup":"first","values":[500,450,340,230,220,110],"textinfo":"value","title":{"position":"top center","text":"Sales for Sale Person A in U.S."},"domain":{"x":[0.01,0.48],"y":[0,0.5]},"type":"funnelarea","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"frame":null},{"scalegroup":"first","values":[600,500,400,300,200,100],"textinfo":"value","title":{"position":"top center","text":"Sales of Sale Person B in Canada"},"domain":{"x":[0.01,0.48],"y":[0.56,1]},"type":"funnelarea","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"frame":null},{"scalegroup":"second","values":[510,480,440,330,220,100],"textinfo":"value","title":{"position":"top left","text":"Sales of Sale Person A in Canada"},"domain":{"x":[0.56,0.98],"y":[0,0.5]},"type":"funnelarea","marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"frame":null},{"scalegroup":"second","values":[360,250,240,130,120,60],"textinfo":"value","title":{"position":"top left","text":"Sales of Sale Person B in U.S."},"domain":{"x":[0.56,0.98],"y":[0.56,1]},"type":"funnelarea","marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#funnel](https://plot.ly/r/reference/#funnel) and [https://plot.ly/r/reference/#funnelarea](https://plot.ly/r/reference/#funnelarea) for more information and chart attribute options!
