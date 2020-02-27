---
description: How to create Polar Charts in R with Plotly.
display_as: scientific
language: r
layout: base
name: Polar Charts
order: 11
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/polar-chart/
thumbnail: thumbnail/polar.gif
---


#### Polar Charts 1.0

Looking for the old polar chart docs? See [legacy polar charts](https://plot.ly/r/legacy-polar-chart/)

#### Basic Polar Charts


```r
library(plotly)

fig <- plot_ly(
  type = 'scatterpolar',
  r = c(0,1,2,2),
  theta = c(0,45,90,0),
  mode = 'markers'
)

fig
```

<div id="htmlwidget-d8b55d5b1cd6743fa41a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d8b55d5b1cd6743fa41a">{"x":{"visdat":{"2dea171ced3":["function () ","plotlyVisDat"]},"cur_data":"2dea171ced3","attrs":{"2dea171ced3":{"r":[0,1,2,2],"theta":[0,45,90,0],"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"r":[0,1,2,2],"theta":[0,45,90,0],"mode":"markers","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Line Polar Charts


```r
library(plotly)

df <- read.csv("https://raw.githubusercontent.com/plotly/datasets/master/polar_dataset.csv")

fig <- plot_ly(
  df,
  type = 'scatterpolar',
  mode = 'lines'
  ) 
fig <- fig %>%
  add_trace(
    r = ~x1,
    theta = ~y,
    name = 'Figure8',
    line = list(
      color = 'peru'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = ~x2,
    theta = ~y,
    name = 'Cardioid',
    line = list(
      color = 'darkviolet'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = ~x3,
    theta = ~y,
    name = 'Hypercardioid',
    line = list(
      color = 'deepskyblue'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = ~x4,
    theta = ~y,
    name = 'Subcardioid',
    line = list(
      color = 'orangered'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = ~x5,
    theta = ~y,
    name = 'Supercardioid',
    line = list(
      color = 'green'
    )
  ) 

fig <- fig %>%
  layout(
    title = 'Mic Patterns',
    font = list(
      family = 'Arial',
      size = 12,
      color = '#000'
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-961a7087c4678b70375e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-961a7087c4678b70375e">{"x":{"visdat":{"2dea618e88c9":["function () ","plotlyVisDat"]},"cur_data":"2dea618e88c9","attrs":{"2dea618e88c9":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea618e88c9.1":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":{},"theta":{},"name":"Figure8","line":{"color":"peru"},"inherit":true},"2dea618e88c9.2":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":{},"theta":{},"name":"Cardioid","line":{"color":"darkviolet"},"inherit":true},"2dea618e88c9.3":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":{},"theta":{},"name":"Hypercardioid","line":{"color":"deepskyblue"},"inherit":true},"2dea618e88c9.4":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":{},"theta":{},"name":"Subcardioid","line":{"color":"orangered"},"inherit":true},"2dea618e88c9.5":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":{},"theta":{},"name":"Supercardioid","line":{"color":"green"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Mic Patterns","font":{"family":"Arial","size":12,"color":"#000"},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,0.995,0.978,0.951,0.914,0.866,0.809,0.743,0.669,0.588,0.5,0.407,0.309,0.208,0.105,0.105,0.208,0.309,0.407,0.5,0.588,0.669,0.743,0.809,0.866,0.914,0.951,0.978,0.995,1,0.995,0.978,0.951,0.914,0.866,0.809,0.743,0.669,0.588,0.5,0.407,0.309,0.208,0.105,0,0.105,0.208,0.309,0.407,0.5,0.588,0.669,0.743,0.809,0.866,0.914,0.951,0.978,0.995,1,1],"theta":[0,6,12,18,24,30,36,42,48,54,60,66,72,78,84,90,96,102,108,114,120,126,132,138,144,150,156,162,168,174,180,186,192,198,204,210,216,222,228,234,240,246,252,258,264,270,276,282,288,294,300,306,312,318,324,330,336,342,348,354,360],"name":"Figure8","line":{"color":"peru"},"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,0.997,0.989,0.976,0.957,0.933,0.905,0.872,0.835,0.794,0.75,0.703,0.655,0.604,0.552,0.5,0.448,0.396,0.345,0.297,0.25,0.206,0.165,0.128,0.095,0.067,0.043,0.024,0.011,0.003,0,0.003,0.011,0.024,0.043,0.067,0.095,0.128,0.165,0.206,0.25,0.297,0.345,0.396,0.448,0.5,0.552,0.604,0.655,0.703,0.75,0.794,0.835,0.872,0.905,0.933,0.957,0.976,0.989,0.997,1],"theta":[0,6,12,18,24,30,36,42,48,54,60,66,72,78,84,90,96,102,108,114,120,126,132,138,144,150,156,162,168,174,180,186,192,198,204,210,216,222,228,234,240,246,252,258,264,270,276,282,288,294,300,306,312,318,324,330,336,342,348,354,360],"name":"Cardioid","line":{"color":"darkviolet"},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,0.996,0.984,0.963,0.935,0.9,0.857,0.807,0.752,0.691,0.625,0.555,0.482,0.406,0.328,0.25,0.172,0.094,0.018,0.055,0.125,0.191,0.252,0.307,0.357,0.4,0.435,0.463,0.484,0.496,0.5,0.496,0.484,0.463,0.435,0.4,0.357,0.307,0.252,0.191,0.125,0.055,0.018,0.094,0.172,0.25,0.328,0.406,0.482,0.555,0.625,0.691,0.752,0.807,0.857,0.9,0.935,0.963,0.984,0.996,1],"theta":[0,6,12,18,24,30,36,42,48,54,60,66,72,78,84,90,96,102,108,114,120,126,132,138,144,150,156,162,168,174,180,186,192,198,204,210,216,222,228,234,240,246,252,258,264,270,276,282,288,294,300,306,312,318,324,330,336,342,348,354,360],"name":"Hypercardioid","line":{"color":"deepskyblue"},"marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,0.998,0.993,0.985,0.974,0.96,0.943,0.923,0.901,0.876,0.85,0.822,0.793,0.762,0.731,0.7,0.669,0.638,0.607,0.578,0.55,0.524,0.499,0.477,0.457,0.44,0.426,0.415,0.407,0.402,0.4,0.402,0.407,0.415,0.426,0.44,0.457,0.477,0.499,0.524,0.55,0.578,0.607,0.638,0.669,0.7,0.731,0.762,0.793,0.822,0.85,0.876,0.901,0.923,0.943,0.96,0.974,0.985,0.993,0.998,1],"theta":[0,6,12,18,24,30,36,42,48,54,60,66,72,78,84,90,96,102,108,114,120,126,132,138,144,150,156,162,168,174,180,186,192,198,204,210,216,222,228,234,240,246,252,258,264,270,276,282,288,294,300,306,312,318,324,330,336,342,348,354,360],"name":"Subcardioid","line":{"color":"orangered"},"marker":{"color":"rgba(148,103,189,1)","line":{"color":"rgba(148,103,189,1)"}},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,0.997,0.986,0.969,0.946,0.916,0.88,0.838,0.792,0.74,0.685,0.626,0.565,0.501,0.436,0.37,0.304,0.239,0.175,0.114,0.055,0,0.052,0.098,0.14,0.176,0.206,0.229,0.246,0.257,0.26,0.257,0.246,0.229,0.206,0.176,0.14,0.098,0.052,0,0.055,0.114,0.175,0.239,0.304,0.37,0.436,0.501,0.565,0.626,0.685,0.74,0.792,0.838,0.88,0.916,0.946,0.969,0.986,0.997,1],"theta":[0,6,12,18,24,30,36,42,48,54,60,66,72,78,84,90,96,102,108,114,120,126,132,138,144,150,156,162,168,174,180,186,192,198,204,210,216,222,228,234,240,246,252,258,264,270,276,282,288,294,300,306,312,318,324,330,336,342,348,354,360],"name":"Supercardioid","line":{"color":"green"},"marker":{"color":"rgba(140,86,75,1)","line":{"color":"rgba(140,86,75,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Area Polar Charts


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    mode = 'lines'
  ) 
fig <- fig %>%
  add_trace(
    r = c(0, 1.5, 1.5, 0, 2.5, 2.5, 0),
    theta = c(0, 10, 25, 0, 205, 215, 0),
    fill = 'toself',
    fillcolor = '#709Bff',
    line = list(
      color = 'black'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(0, 3.5, 3.5, 0),
    theta = c(0, 55, 75, 0),
    fill = 'toself',
    fillcolor = '#E4FF87',
    line = list(
      color = 'black'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(0, 4.5, 4.5, 0, 4.5, 4.5, 0),
    theta = c(0, 100, 120, 0, 305, 320, 0),
    fill = 'toself',
    fillcolor = '#FFAA70',
    line = list(
      color = 'black'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(0, 4, 4, 0),
    theta = c(0, 165, 195, 0),
    fill = 'toself',
    fillcolor = '#FFDF70',
    line = list(
      color = 'black'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(0, 3, 3, 0),
    theta = c(0, 262.5, 277.5, 0),
    fill = 'toself',
    fillcolor = '#B6FFB4',
    line = list(
      color = 'black'
    )
  ) 
fig <- fig %>%
  layout(
    polar = list(
      radialaxis = list(
        visible = T,
        range = c(0,5)
      )
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-e1c5cc2739fc07586512" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e1c5cc2739fc07586512">{"x":{"visdat":{"2dea59e1fb59":["function () ","plotlyVisDat"]},"cur_data":"2dea59e1fb59","attrs":{"2dea59e1fb59":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea59e1fb59.1":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[0,1.5,1.5,0,2.5,2.5,0],"theta":[0,10,25,0,205,215,0],"fill":"toself","fillcolor":"#709Bff","line":{"color":"black"},"inherit":true},"2dea59e1fb59.2":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[0,3.5,3.5,0],"theta":[0,55,75,0],"fill":"toself","fillcolor":"#E4FF87","line":{"color":"black"},"inherit":true},"2dea59e1fb59.3":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[0,4.5,4.5,0,4.5,4.5,0],"theta":[0,100,120,0,305,320,0],"fill":"toself","fillcolor":"#FFAA70","line":{"color":"black"},"inherit":true},"2dea59e1fb59.4":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[0,4,4,0],"theta":[0,165,195,0],"fill":"toself","fillcolor":"#FFDF70","line":{"color":"black"},"inherit":true},"2dea59e1fb59.5":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[0,3,3,0],"theta":[0,262.5,277.5,0],"fill":"toself","fillcolor":"#B6FFB4","line":{"color":"black"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"radialaxis":{"visible":true,"range":[0,5]}},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"fillcolor":"#709Bff","mode":"lines","type":"scatterpolar","r":[0,1.5,1.5,0,2.5,2.5,0],"theta":[0,10,25,0,205,215,0],"fill":"toself","line":{"color":"black"},"name":"#709Bff","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"frame":null},{"fillcolor":"#E4FF87","mode":"lines","type":"scatterpolar","r":[0,3.5,3.5,0],"theta":[0,55,75,0],"fill":"toself","line":{"color":"black"},"name":"#E4FF87","marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"frame":null},{"fillcolor":"#FFAA70","mode":"lines","type":"scatterpolar","r":[0,4.5,4.5,0,4.5,4.5,0],"theta":[0,100,120,0,305,320,0],"fill":"toself","line":{"color":"black"},"name":"#FFAA70","marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"frame":null},{"fillcolor":"#FFDF70","mode":"lines","type":"scatterpolar","r":[0,4,4,0],"theta":[0,165,195,0],"fill":"toself","line":{"color":"black"},"name":"#FFDF70","marker":{"color":"rgba(148,103,189,1)","line":{"color":"rgba(148,103,189,1)"}},"frame":null},{"fillcolor":"#B6FFB4","mode":"lines","type":"scatterpolar","r":[0,3,3,0],"theta":[0,262.5,277.5,0],"fill":"toself","line":{"color":"black"},"name":"#B6FFB4","marker":{"color":"rgba(140,86,75,1)","line":{"color":"rgba(140,86,75,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Categorical Polar Charts


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    mode = 'lines'
  ) 
fig <- fig %>%
  add_trace(
    r = c(5, 4, 2, 4, 5),
    theta = c("a", "b", "c", "d", "a"),
    name = 'angular categories',
    fill = 'toself'
  ) 
fig <- fig %>%
  add_trace(
    r = c("a", "b", "c", "d", "b", "f", "a"),
    theta = c(1, 4, 2, 1.5, 1.5, 6, 5),
    thetaunit = 'radians',
    name = 'radial categories',
    fill = 'toself',
    subplot = 'polar2'
  ) 
fig <- fig %>%
  add_trace(
    r = c(5, 4, 2, 4, 5),
    theta = c("a", "b", "c", "d", "a"),
    name = 'angular categories (w/ categoryarray)',
    fill = 'toself',
    subplot = 'polar3'
  ) 
fig <- fig %>%
  add_trace(
    r = c("a", "b", "c", "d", "b", "f", "a", "a"),
    theta = c(45, 90, 180, 200, 300, 15, 20, 45),
    name = 'radial categories (w/ category descending)',
    fill = 'toself',
    subplot = 'polar4'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      domain = list(
        x = c(0,0.46),
        y = c(0.56,1)
      ),
      radialaxis = list(
        angle = 45
      ),
      angularaxis = list(
        direction = 'clockwise',
        period = 6
      )
    ),
    polar2 = list(
      domain = list(
        x = c(0,0.46),
        y = c(0,0.44)
      ),
      radialaxis = list(
        angle = 180,
        tickangle = -180
      )
    ),
    polar3 = list(
      domain = list(
        x = c(0.54,1),
        y = c(0.56,1)
      ),
      sector = c(150,400),
      radialaxis = list(
        angle = -45
      ),
      angularaxis = list(
        categoryarray = c("d", "a", "c", "b")
      )
    ),
    polar4 = list(
      domain = list(
        x = c(0.54,1),
        y = c(0,0.44)
      ),
      radialaxis = list(
        categoryorder = "category descending"
      ),
      angularaxis = list(
        thetaunit= "radians",
        dtick = 0.3141592653589793
      )
    )
  )

fig
```

<div id="htmlwidget-9345e1c54de68d9a2905" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9345e1c54de68d9a2905">{"x":{"visdat":{"2dea102fa00e":["function () ","plotlyVisDat"]},"cur_data":"2dea102fa00e","attrs":{"2dea102fa00e":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea102fa00e.1":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[5,4,2,4,5],"theta":["a","b","c","d","a"],"name":"angular categories","fill":"toself","inherit":true},"2dea102fa00e.2":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":["a","b","c","d","b","f","a"],"theta":[1,4,2,1.5,1.5,6,5],"thetaunit":"radians","name":"radial categories","fill":"toself","subplot":"polar2","inherit":true},"2dea102fa00e.3":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[5,4,2,4,5],"theta":["a","b","c","d","a"],"name":"angular categories (w/ categoryarray)","fill":"toself","subplot":"polar3","inherit":true},"2dea102fa00e.4":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":["a","b","c","d","b","f","a","a"],"theta":[45,90,180,200,300,15,20,45],"name":"radial categories (w/ category descending)","fill":"toself","subplot":"polar4","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"domain":{"x":[0,0.46],"y":[0.56,1]},"radialaxis":{"angle":45},"angularaxis":{"direction":"clockwise","period":6}},"polar2":{"domain":{"x":[0,0.46],"y":[0,0.44]},"radialaxis":{"angle":180,"tickangle":-180}},"polar3":{"domain":{"x":[0.54,1],"y":[0.56,1]},"sector":[150,400],"radialaxis":{"angle":-45},"angularaxis":{"categoryarray":["d","a","c","b"]}},"polar4":{"domain":{"x":[0.54,1],"y":[0,0.44]},"radialaxis":{"categoryorder":"category descending"},"angularaxis":{"thetaunit":"radians","dtick":0.314159265358979}},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"fillcolor":"rgba(255,127,14,0.5)","mode":"lines","type":"scatterpolar","r":[5,4,2,4,5],"theta":["a","b","c","d","a"],"name":"angular categories","fill":"toself","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"line":{"color":"rgba(255,127,14,1)"},"frame":null},{"fillcolor":"rgba(44,160,44,0.5)","mode":"lines","type":"scatterpolar","r":["a","b","c","d","b","f","a"],"theta":[1,4,2,1.5,1.5,6,5],"thetaunit":"radians","name":"radial categories","fill":"toself","subplot":"polar2","marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"line":{"color":"rgba(44,160,44,1)"},"frame":null},{"fillcolor":"rgba(214,39,40,0.5)","mode":"lines","type":"scatterpolar","r":[5,4,2,4,5],"theta":["a","b","c","d","a"],"name":"angular categories (w/ categoryarray)","fill":"toself","subplot":"polar3","marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"line":{"color":"rgba(214,39,40,1)"},"frame":null},{"fillcolor":"rgba(148,103,189,0.5)","mode":"lines","type":"scatterpolar","r":["a","b","c","d","b","f","a","a"],"theta":[45,90,180,200,300,15,20,45],"name":"radial categories (w/ category descending)","fill":"toself","subplot":"polar4","marker":{"color":"rgba(148,103,189,1)","line":{"color":"rgba(148,103,189,1)"}},"line":{"color":"rgba(148,103,189,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Polar Charts Directions


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    mode = "lines+markers"
  ) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3,4,5),
    theta = c(0,90,180,360,0),
    line = list(
      color = "#ff66ab"
    ),
    marker = list(
      color = "#8090c7",
      symbol = 'square',
      size = 8
    ),
    text = "sector: 135->225<br>rotation: 90<br>direction: counterclockwise"
  ) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3,4,5),
    theta = c(0,90,180,360,0),
    line = list(
      color = "#ff66ab"
    ),
    marker = list(
      color = "#8090c7",
      symbol = 'square',
      size = 8
    ),
    text = "sector: 135->225<br>rotation: 90<br>direction: counterclockwise",
    subplot = 'polar2'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      domain = list(
        x = c(0,0.4),
        y = c(0,1)
      ),
      radialaxis = list(
        tickfont = list(
          size = 8
        )
      ),
      angularaxis = list(
        tickfont = list(
          size = 8
        ),
        rotation = 90,
        direction = 'counterclockwise'
      )
    ),
    polar2 = list(
      domain = list(
        x = c(0.6,1),
        y = c(0,1)
      ),
      radialaxis = list(
        tickfont = list(
          size = 8
        )
      ),
      angularaxis = list(
        tickfont = list(
          size = 8
        ),
        rotation = 90,
        direction = 'clockwise'
      )
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-f24b7d98cc637b014e38" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f24b7d98cc637b014e38">{"x":{"visdat":{"2dea6ef26d9e":["function () ","plotlyVisDat"]},"cur_data":"2dea6ef26d9e","attrs":{"2dea6ef26d9e":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea6ef26d9e.1":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8},"text":"sector: 135->225<br>rotation: 90<br>direction: counterclockwise","inherit":true},"2dea6ef26d9e.2":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8},"text":"sector: 135->225<br>rotation: 90<br>direction: counterclockwise","subplot":"polar2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"domain":{"x":[0,0.4],"y":[0,1]},"radialaxis":{"tickfont":{"size":8}},"angularaxis":{"tickfont":{"size":8},"rotation":90,"direction":"counterclockwise"}},"polar2":{"domain":{"x":[0.6,1],"y":[0,1]},"radialaxis":{"tickfont":{"size":8}},"angularaxis":{"tickfont":{"size":8},"rotation":90,"direction":"clockwise"}},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines+markers","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"lines+markers","type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8,"line":{"color":"rgba(255,127,14,1)"}},"text":["sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise"],"frame":null},{"mode":"lines+markers","type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8,"line":{"color":"rgba(44,160,44,1)"}},"text":["sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise","sector: 135->225<br>rotation: 90<br>direction: counterclockwise"],"subplot":"polar2","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Polar Charts Sector


```r
library(plotly)

fig <- plot_ly(
  type = 'scatterpolar',
  mode = "lines+markers"
) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3,4,5),
    theta = c(0,90,180,360,0),
    line = list(
      color = "#ff66ab"
    ),
    marker = list(
      color = "#8090c7",
      symbol = 'square',
      size = 8
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3,4,5),
    theta = c(0,90,180,360,0),
    line = list(
      color = "#ff66ab"
    ),
    marker = list(
      color = "#8090c7",
      symbol = 'square',
      size = 8
    ),
    subplot = 'polar2'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      domain = list(
        x = c(0,0.4),
        y = c(0,1)
      ),
      sector = c(150,210),
      radialaxis = list(
        tickfont = list(
          size = 8
        )
      ),
      angularaxis = list(
        tickfont = list(
          size = 8
        )
      )
    ),
    polar2 = list(
      domain = list(
        x = c(0.6,1),
        y = c(0,1)
      ),
      radialaxis = list(
        tickfont = list(
          size = 8
        )
      ),
      angularaxis = list(
        tickfont = list(
          size = 8
        )
      )
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-d502059cf0cb22acad18" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d502059cf0cb22acad18">{"x":{"visdat":{"2dea4873c02b":["function () ","plotlyVisDat"]},"cur_data":"2dea4873c02b","attrs":{"2dea4873c02b":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea4873c02b.1":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8},"inherit":true},"2dea4873c02b.2":{"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8},"subplot":"polar2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"domain":{"x":[0,0.4],"y":[0,1]},"sector":[150,210],"radialaxis":{"tickfont":{"size":8}},"angularaxis":{"tickfont":{"size":8}}},"polar2":{"domain":{"x":[0.6,1],"y":[0,1]},"radialaxis":{"tickfont":{"size":8}},"angularaxis":{"tickfont":{"size":8}}},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines+markers","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"lines+markers","type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8,"line":{"color":"rgba(255,127,14,1)"}},"frame":null},{"mode":"lines+markers","type":"scatterpolar","r":[1,2,3,4,5],"theta":[0,90,180,360,0],"line":{"color":"#ff66ab"},"marker":{"color":"#8090c7","symbol":"square","size":8,"line":{"color":"rgba(44,160,44,1)"}},"subplot":"polar2","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Polar Charts Subplot


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    mode = 'lines'
) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3),
    theta = c(50,100,200),
    marker = list(
      symbol = 'square'
    )
  ) 
fig <- fig %>%
  add_trace(
    r = c(1,2,3),
    theta = c(1,2,3),
    thetaunit = 'radians'
  ) 
fig <- fig %>%
  add_trace(
    r = c("a", "b", "c", "d"),
    theta = c("D","C","B","A"),
    subplot = 'polar2'
  ) 
fig <- fig %>%
  add_trace(
    r = c(50,300,900),
    theta = c(0,90,180),
    subplot = 'polar3'
  ) 
fig <- fig %>%
  add_trace(
    r = c(3,3,4,3),
    theta = c(0,45,90,270),
    fill = 'toself',
    subplot = 'polar4'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      domain = list(
        x = c(0,0.46),
        y = c(0.56,1)
      ),
      radialaxis = list(
        range = c(1,4)
      ),
      angularaxis = list(
        thetaunit = 'radians'
      )
    ),
    polar2 = list(
      domain = list(
        x = c(0,0.46),
        y = c(0,0.42)
      )
    ),
    polar3 = list(
      domain = list(
        x = c(0.54,1),
        y = c(0.56,1)
      ),
      sector = c(0,180),
      radialaxis = list(
        type = 'log',
        angle = 45
      )
    ),
    polar4 = list(
      domain = list(
        x = c(0.54,1),
        y = c(0,0.44)
      ),
      radialaxis = list(
        visible = F,
        range = c(0,6)
      )
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-4db665d2ac1a1f1d9abb" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-4db665d2ac1a1f1d9abb">{"x":{"visdat":{"2dea6d1f54ef":["function () ","plotlyVisDat"]},"cur_data":"2dea6d1f54ef","attrs":{"2dea6d1f54ef":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"2dea6d1f54ef.1":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3],"theta":[50,100,200],"marker":{"symbol":"square"},"inherit":true},"2dea6d1f54ef.2":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1,2,3],"theta":[1,2,3],"thetaunit":"radians","inherit":true},"2dea6d1f54ef.3":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":["a","b","c","d"],"theta":["D","C","B","A"],"subplot":"polar2","inherit":true},"2dea6d1f54ef.4":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[50,300,900],"theta":[0,90,180],"subplot":"polar3","inherit":true},"2dea6d1f54ef.5":{"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[3,3,4,3],"theta":[0,45,90,270],"fill":"toself","subplot":"polar4","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"domain":{"x":[0,0.46],"y":[0.56,1]},"radialaxis":{"range":[1,4]},"angularaxis":{"thetaunit":"radians"}},"polar2":{"domain":{"x":[0,0.46],"y":[0,0.42]}},"polar3":{"domain":{"x":[0.54,1],"y":[0.56,1]},"sector":[0,180],"radialaxis":{"type":"log","angle":45}},"polar4":{"domain":{"x":[0.54,1],"y":[0,0.44]},"radialaxis":{"visible":false,"range":[0,6]}},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"lines","type":"scatterpolar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"lines+markers","type":"scatterpolar","r":[1,2,3],"theta":[50,100,200],"marker":{"color":"rgba(255,127,14,1)","symbol":"square","line":{"color":"rgba(255,127,14,1)"}},"line":{"color":"rgba(255,127,14,1)"},"frame":null},{"mode":"lines","type":"scatterpolar","r":[1,2,3],"theta":[1,2,3],"thetaunit":"radians","marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"line":{"color":"rgba(44,160,44,1)"},"frame":null},{"mode":"lines","type":"scatterpolar","r":["a","b","c","d"],"theta":["D","C","B","A"],"subplot":"polar2","marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"line":{"color":"rgba(214,39,40,1)"},"frame":null},{"mode":"lines","type":"scatterpolar","r":[50,300,900],"theta":[0,90,180],"subplot":"polar3","marker":{"color":"rgba(148,103,189,1)","line":{"color":"rgba(148,103,189,1)"}},"line":{"color":"rgba(148,103,189,1)"},"frame":null},{"fillcolor":"rgba(140,86,75,0.5)","mode":"lines","type":"scatterpolar","r":[3,3,4,3],"theta":[0,45,90,270],"fill":"toself","subplot":"polar4","marker":{"color":"rgba(140,86,75,1)","line":{"color":"rgba(140,86,75,1)"}},"line":{"color":"rgba(140,86,75,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Webgl Polar Charts


```r
library(plotly)

df <- read.csv("https://raw.githubusercontent.com/plotly/datasets/master/hobbs-pearson-trials.csv")

fig <- plot_ly(
    type = 'scatterpolargl',
    mode = 'markers'
  )

j = 1
k = 2
for (i in 1:(length(df)/2)){
 fig <- add_trace(
    fig,
    r = df[,j],
    theta = df[,k],
    name = paste('Trial ', i),
    marker = list(
      size = 15,
      line = list(
        color = '#FFF'
      ),
      opacity = 0.7
    )
  )
  j <- j + 2
  k <- k + 2
}

fig <- layout(
  fig,
  title = "Hobbs-Pearson Trials",
  showlegend = F,
  paper_bgcolor = "rgb(223, 223, 223)",
  polar = list(
    bgcolor = "rgb(223, 223, 223)",
    angularaxis = list(
      tickwidth = 2,
      linewidth = 3,
      layer = 'below traces'
    ),
    radialaxis = list(
      side = 'counterclockwise',
      showline = T,
      linewidth = 2,
      tickwidth = 2,
      gridcolor = '#FFF',
      gridwidth = 2
    )
  )
)

fig
```

<div id="htmlwidget-8de739e3ea3fa2b05143" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-8de739e3ea3fa2b05143">{"x":{"visdat":{"2dea7ab2491d":["function () ","plotlyVisDat"]},"cur_data":"2dea7ab2491d","attrs":{"2dea7ab2491d":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl"},"2dea7ab2491d.1":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[6.804985785,3.389596011,5.381472111,8.059540219,5.318229228,2.985099936,1.966587002,6.769265408,4.073401899,6.504371825,7.556369819,4.047456094,7.386662496,5.413624737,7.470716531,7.982110217,4.73781408,4.206453043,5.478604805,4.824520281,5.59960061,6.866795217,3.085671366,7.771810943,3.687794435,5.360356685,5.140446739,6.045445681,6.83392094,3.620769463,3.989430583,5.3118245,4.60821348,6.640584716,3.055188854,7.492564164,5.485078178,3.897794997,5.976245114,5.447061561,5.377034117,4.690805788,4.711640491,3.629919329,5.957668076,5.357121284,3.849235283,6.250507136,7.122243357,3.399404234,3.510556672,4.100997604,4.0963821,6.233583075,3.939488527,3.925445077,6.118132501,3.940450346,7.583015573,3.513202145],"theta":[-30.35294436,-25.61145985,-12.42522745,13.96138052,-4.950932841,-25.69227419,12.46876416,-4.913764107,-10.96738029,30.81419405,2.474959431,17.97554375,0.771130593,6.137488486,-14.45196357,28.18453411,12.53868007,-8.983230337,5.231285165,-64.48900254,11.35748668,3.454074792,13.92434661,-25.36400205,-16.81800639,-10.26005103,-13.21213413,2.579338865,8.717574966,-10.67549872,-2.926366013,25.19588075,40.59032932,-9.12143363,-24.29736238,-3.176944506,10.85049842,-31.33205975,4.849567462,15.04827695,3.295104699,-6.197091873,-8.778574136,29.54917412,-5.137448793,23.02686049,-6.634816578,2.755014992,21.73325011,-24.81699496,-7.830547063,28.32579621,12.30097747,-21.56315724,-19.33551628,26.14644317,-1.706071203,16.0717237,2.053266303,-5.097911612],"name":"Trial  1","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true},"2dea7ab2491d.2":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[3.488043923,2.918478576,4.20182736,8.227324607,4.776690427,3.041912303,4.789947719,5.66388078,3.858262393,8.260212881,6.868624486,5.7401976,6.594979282,5.692703778,5.337916574,9.283604185,5.764590893,4.028864552,5.662344748,0.422837231,6.201266464,6.439265381,5.096758513,4.632081909,3.421846136,4.369404703,4.028334419,5.805767198,6.848189921,3.809295513,4.385268184,6.983326846,7.396273186,5.215125003,3.086148779,6.335394491,6.090414714,2.448056007,5.94278402,6.373129886,5.454205341,4.393337617,4.20594468,6.155542288,5.119087171,6.869860831,4.104599861,5.954348126,8.092332877,2.961769705,3.974012188,6.373384129,5.415409143,3.87689092,3.261446947,6.14580853,5.502451987,5.571553295,6.853049261,4.140355075],"theta":[14.80662578,79.00634037,49.02206554,49.69908314,54.13749108,86.41932102,96.95239194,41.46348826,67.13769169,68.06103944,42.68193032,76.39865661,42.19479347,59.57788897,27.5108668,60.75344483,68.3708328,65.74802815,58.53300837,-176.7441065,61.17401858,47.45150859,84.42665319,12.47934655,72.48080276,50.57883176,51.56022824,52.43785618,51.58682799,73.87294478,70.21705693,70.71429915,82.23439443,38.93539045,84.70936667,38.16582844,61.70405365,70.19695629,54.45429259,64.33489497,58.27389315,60.49982239,59.15523254,83.86561847,47.8734099,69.28260157,71.18991043,51.04839646,59.42758242,78.59873696,75.75586452,79.97048372,73.89378025,31.73341113,68.08475118,80.41107998,48.92425071,76.65025576,42.18286436,76.03333589],"name":"Trial  2","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true},"2dea7ab2491d.3":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[1.855870835,5.286962062,3.886013392,6.282863313,4.453414848,5.688008051,7.330864283,3.825660595,4.989604177,7.89743147,4.656693113,6.667153696,4.431006287,5.346113253,2.479945696,8.113477349,6.081311682,4.968216896,5.244453921,5.422207884,5.792774616,4.787580592,6.784318637,1.108936909,5.138911105,4.042929657,4.02289203,4.828428791,5.417378374,5.378635211,5.421097175,7.120561979,8.34930854,3.410485588,5.628378471,3.914936976,5.763940262,4.764374107,5.076236268,6.165558183,5.105576516,4.761036377,4.596249541,7.504188411,4.107031418,6.920422299,5.34912895,4.798065719,7.023251532,5.283680965,5.569071152,7.383794908,6.26923321,2.656529645,4.843984339,7.247992362,4.372959394,6.570981081,4.602479244,5.670052051],"theta":[151.2942552,147.188025,125.2821571,87.06729797,119.6278984,147.7408241,139.5645981,101.3914971,134.5601843,104.0244447,89.39314294,123.1940314,91.47434052,113.3323736,96.14992557,93.28073452,118.2155652,132.3229374,112.9411864,-179.7462331,110.3035136,97.75083617,131.6080893,115.4969192,140.5811822,123.3966621,128.342009,107.6088104,97.90468979,137.128448,130.4312449,112.2270845,118.6302022,106.0582256,146.9081097,90.27734956,111.5052824,151.0897425,107.7213942,111.300855,114.6802779,126.5693795,128.2189522,125.3548572,112.4180683,111.7973557,133.4180523,105.1841168,97.23103612,146.6680368,136.2393152,121.7918442,123.911328,129.862245,141.3439509,123.2709677,108.4588217,124.4123771,89.02711074,134.8767011],"name":"Trial  3","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true},"2dea7ab2491d.4":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[5.372470924,7.096355572,4.883823903,2.920135441,4.723963046,7.423693951,8.090946075,3.306844591,6.050828483,5.530232074,2.472306953,6.275670537,2.615896174,4.653539945,3.335440014,4.795883605,5.472711346,5.881930491,4.571587072,9.03986117,4.6429076,3.172767736,7.044248139,4.466336514,6.55733029,4.820849437,5.131915515,3.970012237,3.406323813,6.476722964,6.019218509,5.664501535,7.158758523,3.600712662,7.324127169,2.552946156,4.72713386,6.971755207,4.076578361,4.946223407,4.642155449,5.360574864,5.391719067,7.072524305,4.10111157,5.485732621,6.192535286,3.768711392,4.29031139,7.06019537,6.539691844,6.679744406,6.060825359,4.786574041,6.41668653,6.703281333,3.88884781,6.308591081,2.437044771,6.508186348],"theta":[-140.2033276,-168.0842454,-166.2851413,138.2488668,-174.4243864,-169.9604828,176.9918227,-169.9014162,-172.6415816,142.9516688,172.4157464,168.5193592,177.8220537,172.8551903,-146.0145217,128.177293,169.1670728,-173.5885738,173.7269927,-151.2061048,166.2604772,172.5075661,173.9491839,-131.8068409,-170.6352738,-168.5770855,-166.7655034,176.0704873,162.2975015,-174.0557463,-178.0609299,156.4712689,155.2391421,-163.0005264,-170.1167133,-170.6392725,167.3831437,-163.0988171,172.880737,163.3860077,176.182542,-174.5796802,-172.3358449,165.3380257,-172.5256643,157.5428777,-175.8815111,175.427644,142.0696747,-168.340734,-175.8058311,163.0637454,171.720975,-151.4039046,-168.2713691,165.0453279,-177.3153367,170.0424129,173.5991966,-177.2506567],"name":"Trial  4","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true},"2dea7ab2491d.5":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[7.937557871,7.302746492,5.929302221,2.407178713,5.270921887,7.400596128,6.810820338,4.967759034,6.19022937,2.158518658,4.004125894,4.776617322,4.232250452,4.307654873,6.200275173,0.727513849,4.378006804,6.004964939,4.341931703,10.23798294,3.802158889,3.96928117,5.758980142,7.674179069,6.699953533,5.734310388,6.044275915,4.312943066,3.377545282,6.367666727,5.737244182,3.396351472,4.216467481,5.464885017,7.311135578,4.745400769,3.916468532,7.60297299,4.125204829,3.67679495,4.551235789,5.606960532,5.794844257,5.030528156,5.109586241,3.405440208,6.026306125,4.221109264,1.909782937,7.254669394,6.268875872,4.562580567,4.918057965,6.836560963,6.786486549,4.751014334,4.719926348,4.927805215,4.059190587,6.128338984],"theta":[-101.8337858,-127.4783916,-112.244285,-82.32591087,-114.6888556,-130.5378634,-145.010265,-98.74884501,-124.4417488,-152.4541193,-89.29423655,-139.8324517,-91.54359518,-119.442163,-92.45583853,-129.6599243,-131.0512351,-123.8529175,-118.086739,-121.9792171,-121.91503,-99.36184758,-141.467702,-93.56626319,-126.3369014,-112.8349442,-114.3864799,-109.7960723,-102.7432647,-128.2467289,-127.7920926,-142.4736297,-161.5872942,-99.94061078,-130.1631173,-90.22881201,-122.6504912,-123.2677506,-111.9973088,-127.5283168,-117.9312953,-120.3916342,-119.3868715,-149.6746955,-107.8505175,-138.9899313,-127.5954702,-107.3208354,-117.5738074,-127.481661,-129.9120332,-148.4952117,-135.3316414,-104.4216593,-123.8754402,-146.8168266,-107.0584854,-138.9025649,-88.89688252,-130.7544674],"name":"Trial  5","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true},"2dea7ab2491d.6":{"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolargl","r":[8.469180528,5.821997567,6.140918328,5.831724285,5.546754472,5.627487709,3.948328976,6.490184615,5.320618245,3.243593041,6.444085332,3.363778101,6.463116811,4.730944926,7.796578411,4.57012783,3.926206816,5.25434814,4.838411107,8.694523999,4.399531818,5.856483905,3.621577039,8.894912373,5.494542836,5.968980891,6.047899574,5.384671397,5.381220018,5.111574623,4.770561105,3.098330883,1.665083172,6.740258533,5.594494929,6.879630826,4.382792466,6.410843616,5.154204318,4.015158519,4.939148868,5.298297314,5.490417177,2.623751259,5.953588662,3.301479372,4.954889001,5.50005367,4.45051235,5.786624513,4.906834424,2.629969473,3.769703608,7.396735716,5.764481902,2.794585196,5.78203327,3.485351918,6.500653599,4.74864071],"theta":[-66.53583633,-84.51442268,-63.3397417,-24.14681274,-59.70124532,-88.06537268,-98.44420454,-49.15839682,-73.63622331,-17.92387468,-38.41239945,-66.34036238,-40.88883874,-52.46063321,-52.61046256,-7.039351051,-57.23545869,-71.6422035,-52.34539617,-92.78303867,-47.18716306,-41.96920846,-82.14422825,-59.4391656,-79.19482259,-62.29990854,-65.53790404,-48.90605545,-37.74831104,-78.05333346,-71.87311766,-41.89109283,-53.11545549,-52.9976281,-87.08436102,-43.61190484,-48.79799841,-82.56680316,-47.909963,-46.57048559,-54.50048322,-65.90072713,-66.87331746,-75.48080725,-54.77769387,-42.59833459,-74.50816627,-47.11021844,-22.35687318,-84.19298675,-78.50528476,-65.03637179,-66.51373368,-63.52677656,-77.80907855,-68.51017974,-51.29686931,-68.33991303,-38.63173307,-77.85184859],"name":"Trial  6","marker":{"size":15,"line":{"color":"#FFF"},"opacity":0.7},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Hobbs-Pearson Trials","showlegend":false,"paper_bgcolor":"rgb(223, 223, 223)","polar":{"bgcolor":"rgb(223, 223, 223)","angularaxis":{"tickwidth":2,"linewidth":3,"layer":"below traces"},"radialaxis":{"side":"counterclockwise","showline":true,"linewidth":2,"tickwidth":2,"gridcolor":"#FFF","gridwidth":2}},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"markers","type":"scatterpolargl","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[6.804985785,3.389596011,5.381472111,8.059540219,5.318229228,2.985099936,1.966587002,6.769265408,4.073401899,6.504371825,7.556369819,4.047456094,7.386662496,5.413624737,7.470716531,7.982110217,4.73781408,4.206453043,5.478604805,4.824520281,5.59960061,6.866795217,3.085671366,7.771810943,3.687794435,5.360356685,5.140446739,6.045445681,6.83392094,3.620769463,3.989430583,5.3118245,4.60821348,6.640584716,3.055188854,7.492564164,5.485078178,3.897794997,5.976245114,5.447061561,5.377034117,4.690805788,4.711640491,3.629919329,5.957668076,5.357121284,3.849235283,6.250507136,7.122243357,3.399404234,3.510556672,4.100997604,4.0963821,6.233583075,3.939488527,3.925445077,6.118132501,3.940450346,7.583015573,3.513202145],"theta":[-30.35294436,-25.61145985,-12.42522745,13.96138052,-4.950932841,-25.69227419,12.46876416,-4.913764107,-10.96738029,30.81419405,2.474959431,17.97554375,0.771130593,6.137488486,-14.45196357,28.18453411,12.53868007,-8.983230337,5.231285165,-64.48900254,11.35748668,3.454074792,13.92434661,-25.36400205,-16.81800639,-10.26005103,-13.21213413,2.579338865,8.717574966,-10.67549872,-2.926366013,25.19588075,40.59032932,-9.12143363,-24.29736238,-3.176944506,10.85049842,-31.33205975,4.849567462,15.04827695,3.295104699,-6.197091873,-8.778574136,29.54917412,-5.137448793,23.02686049,-6.634816578,2.755014992,21.73325011,-24.81699496,-7.830547063,28.32579621,12.30097747,-21.56315724,-19.33551628,26.14644317,-1.706071203,16.0717237,2.053266303,-5.097911612],"name":"Trial  1","marker":{"color":"rgba(255,127,14,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(255,127,14,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[3.488043923,2.918478576,4.20182736,8.227324607,4.776690427,3.041912303,4.789947719,5.66388078,3.858262393,8.260212881,6.868624486,5.7401976,6.594979282,5.692703778,5.337916574,9.283604185,5.764590893,4.028864552,5.662344748,0.422837231,6.201266464,6.439265381,5.096758513,4.632081909,3.421846136,4.369404703,4.028334419,5.805767198,6.848189921,3.809295513,4.385268184,6.983326846,7.396273186,5.215125003,3.086148779,6.335394491,6.090414714,2.448056007,5.94278402,6.373129886,5.454205341,4.393337617,4.20594468,6.155542288,5.119087171,6.869860831,4.104599861,5.954348126,8.092332877,2.961769705,3.974012188,6.373384129,5.415409143,3.87689092,3.261446947,6.14580853,5.502451987,5.571553295,6.853049261,4.140355075],"theta":[14.80662578,79.00634037,49.02206554,49.69908314,54.13749108,86.41932102,96.95239194,41.46348826,67.13769169,68.06103944,42.68193032,76.39865661,42.19479347,59.57788897,27.5108668,60.75344483,68.3708328,65.74802815,58.53300837,-176.7441065,61.17401858,47.45150859,84.42665319,12.47934655,72.48080276,50.57883176,51.56022824,52.43785618,51.58682799,73.87294478,70.21705693,70.71429915,82.23439443,38.93539045,84.70936667,38.16582844,61.70405365,70.19695629,54.45429259,64.33489497,58.27389315,60.49982239,59.15523254,83.86561847,47.8734099,69.28260157,71.18991043,51.04839646,59.42758242,78.59873696,75.75586452,79.97048372,73.89378025,31.73341113,68.08475118,80.41107998,48.92425071,76.65025576,42.18286436,76.03333589],"name":"Trial  2","marker":{"color":"rgba(44,160,44,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(44,160,44,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[1.855870835,5.286962062,3.886013392,6.282863313,4.453414848,5.688008051,7.330864283,3.825660595,4.989604177,7.89743147,4.656693113,6.667153696,4.431006287,5.346113253,2.479945696,8.113477349,6.081311682,4.968216896,5.244453921,5.422207884,5.792774616,4.787580592,6.784318637,1.108936909,5.138911105,4.042929657,4.02289203,4.828428791,5.417378374,5.378635211,5.421097175,7.120561979,8.34930854,3.410485588,5.628378471,3.914936976,5.763940262,4.764374107,5.076236268,6.165558183,5.105576516,4.761036377,4.596249541,7.504188411,4.107031418,6.920422299,5.34912895,4.798065719,7.023251532,5.283680965,5.569071152,7.383794908,6.26923321,2.656529645,4.843984339,7.247992362,4.372959394,6.570981081,4.602479244,5.670052051],"theta":[151.2942552,147.188025,125.2821571,87.06729797,119.6278984,147.7408241,139.5645981,101.3914971,134.5601843,104.0244447,89.39314294,123.1940314,91.47434052,113.3323736,96.14992557,93.28073452,118.2155652,132.3229374,112.9411864,-179.7462331,110.3035136,97.75083617,131.6080893,115.4969192,140.5811822,123.3966621,128.342009,107.6088104,97.90468979,137.128448,130.4312449,112.2270845,118.6302022,106.0582256,146.9081097,90.27734956,111.5052824,151.0897425,107.7213942,111.300855,114.6802779,126.5693795,128.2189522,125.3548572,112.4180683,111.7973557,133.4180523,105.1841168,97.23103612,146.6680368,136.2393152,121.7918442,123.911328,129.862245,141.3439509,123.2709677,108.4588217,124.4123771,89.02711074,134.8767011],"name":"Trial  3","marker":{"color":"rgba(214,39,40,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(214,39,40,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[5.372470924,7.096355572,4.883823903,2.920135441,4.723963046,7.423693951,8.090946075,3.306844591,6.050828483,5.530232074,2.472306953,6.275670537,2.615896174,4.653539945,3.335440014,4.795883605,5.472711346,5.881930491,4.571587072,9.03986117,4.6429076,3.172767736,7.044248139,4.466336514,6.55733029,4.820849437,5.131915515,3.970012237,3.406323813,6.476722964,6.019218509,5.664501535,7.158758523,3.600712662,7.324127169,2.552946156,4.72713386,6.971755207,4.076578361,4.946223407,4.642155449,5.360574864,5.391719067,7.072524305,4.10111157,5.485732621,6.192535286,3.768711392,4.29031139,7.06019537,6.539691844,6.679744406,6.060825359,4.786574041,6.41668653,6.703281333,3.88884781,6.308591081,2.437044771,6.508186348],"theta":[-140.2033276,-168.0842454,-166.2851413,138.2488668,-174.4243864,-169.9604828,176.9918227,-169.9014162,-172.6415816,142.9516688,172.4157464,168.5193592,177.8220537,172.8551903,-146.0145217,128.177293,169.1670728,-173.5885738,173.7269927,-151.2061048,166.2604772,172.5075661,173.9491839,-131.8068409,-170.6352738,-168.5770855,-166.7655034,176.0704873,162.2975015,-174.0557463,-178.0609299,156.4712689,155.2391421,-163.0005264,-170.1167133,-170.6392725,167.3831437,-163.0988171,172.880737,163.3860077,176.182542,-174.5796802,-172.3358449,165.3380257,-172.5256643,157.5428777,-175.8815111,175.427644,142.0696747,-168.340734,-175.8058311,163.0637454,171.720975,-151.4039046,-168.2713691,165.0453279,-177.3153367,170.0424129,173.5991966,-177.2506567],"name":"Trial  4","marker":{"color":"rgba(148,103,189,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(148,103,189,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[7.937557871,7.302746492,5.929302221,2.407178713,5.270921887,7.400596128,6.810820338,4.967759034,6.19022937,2.158518658,4.004125894,4.776617322,4.232250452,4.307654873,6.200275173,0.727513849,4.378006804,6.004964939,4.341931703,10.23798294,3.802158889,3.96928117,5.758980142,7.674179069,6.699953533,5.734310388,6.044275915,4.312943066,3.377545282,6.367666727,5.737244182,3.396351472,4.216467481,5.464885017,7.311135578,4.745400769,3.916468532,7.60297299,4.125204829,3.67679495,4.551235789,5.606960532,5.794844257,5.030528156,5.109586241,3.405440208,6.026306125,4.221109264,1.909782937,7.254669394,6.268875872,4.562580567,4.918057965,6.836560963,6.786486549,4.751014334,4.719926348,4.927805215,4.059190587,6.128338984],"theta":[-101.8337858,-127.4783916,-112.244285,-82.32591087,-114.6888556,-130.5378634,-145.010265,-98.74884501,-124.4417488,-152.4541193,-89.29423655,-139.8324517,-91.54359518,-119.442163,-92.45583853,-129.6599243,-131.0512351,-123.8529175,-118.086739,-121.9792171,-121.91503,-99.36184758,-141.467702,-93.56626319,-126.3369014,-112.8349442,-114.3864799,-109.7960723,-102.7432647,-128.2467289,-127.7920926,-142.4736297,-161.5872942,-99.94061078,-130.1631173,-90.22881201,-122.6504912,-123.2677506,-111.9973088,-127.5283168,-117.9312953,-120.3916342,-119.3868715,-149.6746955,-107.8505175,-138.9899313,-127.5954702,-107.3208354,-117.5738074,-127.481661,-129.9120332,-148.4952117,-135.3316414,-104.4216593,-123.8754402,-146.8168266,-107.0584854,-138.9025649,-88.89688252,-130.7544674],"name":"Trial  5","marker":{"color":"rgba(140,86,75,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(140,86,75,1)"},"frame":null},{"mode":"markers","type":"scatterpolargl","r":[8.469180528,5.821997567,6.140918328,5.831724285,5.546754472,5.627487709,3.948328976,6.490184615,5.320618245,3.243593041,6.444085332,3.363778101,6.463116811,4.730944926,7.796578411,4.57012783,3.926206816,5.25434814,4.838411107,8.694523999,4.399531818,5.856483905,3.621577039,8.894912373,5.494542836,5.968980891,6.047899574,5.384671397,5.381220018,5.111574623,4.770561105,3.098330883,1.665083172,6.740258533,5.594494929,6.879630826,4.382792466,6.410843616,5.154204318,4.015158519,4.939148868,5.298297314,5.490417177,2.623751259,5.953588662,3.301479372,4.954889001,5.50005367,4.45051235,5.786624513,4.906834424,2.629969473,3.769703608,7.396735716,5.764481902,2.794585196,5.78203327,3.485351918,6.500653599,4.74864071],"theta":[-66.53583633,-84.51442268,-63.3397417,-24.14681274,-59.70124532,-88.06537268,-98.44420454,-49.15839682,-73.63622331,-17.92387468,-38.41239945,-66.34036238,-40.88883874,-52.46063321,-52.61046256,-7.039351051,-57.23545869,-71.6422035,-52.34539617,-92.78303867,-47.18716306,-41.96920846,-82.14422825,-59.4391656,-79.19482259,-62.29990854,-65.53790404,-48.90605545,-37.74831104,-78.05333346,-71.87311766,-41.89109283,-53.11545549,-52.9976281,-87.08436102,-43.61190484,-48.79799841,-82.56680316,-47.909963,-46.57048559,-54.50048322,-65.90072713,-66.87331746,-75.48080725,-54.77769387,-42.59833459,-74.50816627,-47.11021844,-22.35687318,-84.19298675,-78.50528476,-65.03637179,-66.51373368,-63.52677656,-77.80907855,-68.51017974,-51.29686931,-68.33991303,-38.63173307,-77.85184859],"name":"Trial  6","marker":{"color":"rgba(227,119,194,1)","size":15,"line":{"color":"#FFF"},"opacity":0.7},"line":{"color":"rgba(227,119,194,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Reference

See [https://plot.ly/r/reference/#polar](https://plot.ly/r/reference/#polar) for more information and options!
