---
name: Waterfall Charts
permalink: r/waterfall-charts/
description: How to make waterfall charts in R with Plotly.
layout: base
thumbnail: thumbnail/waterfall-charts.jpg
language: r
page_type: example_index
display_as: financial
order: 4
output:
  html_document:
    keep_md: true
---


### Basic Waterfall Chart


```r
library(plotly)

x= list("Sales", "Consulting", "Net revenue", "Purchases", "Other expenses", "Profit before tax")
measure= c("relative", "relative", "total", "relative", "relative", "total")
text= c("+60", "+80", "", "-40", "-20", "Total")
y= c(60, 80, 0, -40, -20, 0)
data = data.frame(x=factor(x,levels=x),measure,text,y)

fig <- plot_ly(
  data, name = "20", type = "waterfall", measure = ~measure,
  x = ~x, textposition = "outside", y= ~y, text =~text,
  connector = list(line = list(color= "rgb(63, 63, 63)"))) 
fig <- fig %>%
  layout(title = "Profit and loss statement 2018",
        xaxis = list(title = ""),
        yaxis = list(title = ""),
        autosize = TRUE,
        showlegend = TRUE)

fig
```

<div id="htmlwidget-e2f902049b1777af2f2f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e2f902049b1777af2f2f">{"x":{"visdat":{"3396191ead4c":["function () ","plotlyVisDat"]},"cur_data":"3396191ead4c","attrs":{"3396191ead4c":{"measure":{},"x":{},"textposition":"outside","y":{},"text":{},"connector":{"line":{"color":"rgb(63, 63, 63)"}},"name":"20","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"waterfall"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Profit and loss statement 2018","xaxis":{"domain":[0,1],"automargin":true,"title":"","type":"category","categoryorder":"array","categoryarray":["Sales","Consulting","Net revenue","Purchases","Other expenses","Profit before tax"]},"yaxis":{"domain":[0,1],"automargin":true,"title":""},"autosize":true,"showlegend":true,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"measure":["relative","relative","total","relative","relative","total"],"x":["Sales","Consulting","Net revenue","Purchases","Other expenses","Profit before tax"],"textposition":["outside","outside","outside","outside","outside","outside"],"y":[60,80,0,-40,-20,0],"text":["+60","+80","","-40","-20","Total"],"connector":{"line":{"color":"rgb(63, 63, 63)"}},"name":"20","type":"waterfall","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Setting Marker Size and Color
This example uses [decreasing, increasing, and total attributes](https://plot.ly/r/reference/#waterfall-decreasing-marker-line-color) to customize the bars.


```r
library(plotly)

y = c(375, 128, 78, 0, -327, -78, 0, 32, 89, 0, -45, 0)
x = c("Sales", "Consulting", "Maintenance", "Net revenue", "Purchases", "Material expenses", "Operating profit", "Investment income", "Financial income",
"Profit before tax", "Income tax (15%)", "Profit after tax")
measure = c("relative", "relative", "relative", "total", "relative", "relative", "total", "relative", "relative", "total", "relative", "total")
data = data.frame(x=factor(x,levels = x), y, measure)

fig <- plot_ly(data, x = ~x, y = ~y, measure = ~measure, type = "waterfall", base = 300, decreasing = list(marker = list(color = "Maroon", line = list(color = "red", width = 2))),
increasing = (marker = list(color = "Teal")),
totals = list(marker = list(color = "deep sky blue", line = list(color = 'blue', width = 3))))
fig <- fig %>%
layout(title = "Profit and loss statement", xaxis = list(title = "", tickfont = "16", ticks = "outside"),
yaxis = list(title = ""), waterfallgap = "0.3")


fig
```

<div id="htmlwidget-300935ebabdecf6a7b48" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-300935ebabdecf6a7b48">{"x":{"visdat":{"3396403a836e":["function () ","plotlyVisDat"]},"cur_data":"3396403a836e","attrs":{"3396403a836e":{"x":{},"y":{},"measure":{},"base":300,"decreasing":{"marker":{"color":"Maroon","line":{"color":"red","width":2}}},"increasing":{"color":"Teal"},"totals":{"marker":{"color":"deep sky blue","line":{"color":"blue","width":3}}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"waterfall"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Profit and loss statement","xaxis":{"domain":[0,1],"automargin":true,"title":"","tickfont":"16","ticks":"outside","type":"category","categoryorder":"array","categoryarray":["Sales","Consulting","Maintenance","Net revenue","Purchases","Material expenses","Operating profit","Investment income","Financial income","Profit before tax","Income tax (15%)","Profit after tax"]},"yaxis":{"domain":[0,1],"automargin":true,"title":""},"waterfallgap":"0.3","hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["Sales","Consulting","Maintenance","Net revenue","Purchases","Material expenses","Operating profit","Investment income","Financial income","Profit before tax","Income tax (15%)","Profit after tax"],"y":[375,128,78,0,-327,-78,0,32,89,0,-45,0],"measure":["relative","relative","relative","total","relative","relative","total","relative","relative","total","relative","total"],"base":300,"decreasing":{"marker":{"color":"Maroon","line":{"color":"red","width":2}}},"increasing":{"color":"Teal"},"totals":{"marker":{"color":"deep sky blue","line":{"color":"blue","width":3}}},"type":"waterfall","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


```r
library(plotly)

x = c(375, 128, 78, 27, 0, -327, -12, -78, -12, 0, 32, 89, 0, -45, 0)
y = c("Sales", "Consulting", "Maintenance", "Other revenue", "Net revenue", "Purchases", "Material expenses",
"Personnel expenses", "Other expenses", "Operating profit", "Investment income", "Financial income",
"Profit before tax", "Income tax (15%)", "Profit after tax")
measure = c("relative", "relative", "relative", "relative", "total", "relative", "relative", "relative",
"relative", "total", "relative", "relative", "total", "relative", "total")
data = data.frame(x,y=factor(y,levels = y), measure)

fig <- plot_ly(data, x = ~x, y = ~y, measure = ~measure, type = "waterfall", name = "2018",
orientation = "h", connector = list(mode = "between", line = list(width = 4, color = "rgb(0, 0, 0)", dash = 0)))
fig <- fig %>%
layout(title = "Profit and loss statement 2018<br>waterfall chart displaying positive and negative",
xaxis = list(title = "", tickfont = "16", ticks = "outside"),
yaxis = list(title = "", type = "category", autorange = "reversed"),
        xaxis = list(title ="", type = "linear"),
        margin = c(l = 150),
        showlegend = TRUE)


fig
```

<div id="htmlwidget-c2d919d68a5424bf4c07" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c2d919d68a5424bf4c07">{"x":{"visdat":{"339623f57cb4":["function () ","plotlyVisDat"]},"cur_data":"339623f57cb4","attrs":{"339623f57cb4":{"x":{},"y":{},"measure":{},"orientation":"h","connector":{"mode":"between","line":{"width":4,"color":"rgb(0, 0, 0)","dash":0}},"name":"2018","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"waterfall"}},"layout":{"margin":150,"title":"Profit and loss statement 2018<br>waterfall chart displaying positive and negative","xaxis":{"domain":[0,1],"automargin":true,"title":"","tickfont":"16","ticks":"outside"},"yaxis":{"domain":[0,1],"automargin":true,"title":"","type":"category","autorange":"reversed","categoryorder":"array","categoryarray":["Sales","Consulting","Maintenance","Other revenue","Net revenue","Purchases","Material expenses","Personnel expenses","Other expenses","Operating profit","Investment income","Financial income","Profit before tax","Income tax (15%)","Profit after tax"]},"showlegend":true,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[375,128,78,27,0,-327,-12,-78,-12,0,32,89,0,-45,0],"y":["Sales","Consulting","Maintenance","Other revenue","Net revenue","Purchases","Material expenses","Personnel expenses","Other expenses","Operating profit","Investment income","Financial income","Profit before tax","Income tax (15%)","Profit after tax"],"measure":["relative","relative","relative","relative","total","relative","relative","relative","relative","total","relative","relative","total","relative","total"],"orientation":"h","connector":{"mode":"between","line":{"width":4,"color":"rgb(0, 0, 0)","dash":0}},"name":"2018","type":"waterfall","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
