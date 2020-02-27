---
description: How to make a choropleth map in R. A choropleth map shades geographic
  regions by value.
display_as: maps
language: r
layout: base
name: Choropleth Maps
order: 1
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/choropleth-maps/
thumbnail: thumbnail/choropleth.jpg
---


# Choropleth Maps in R

```r
library(plotly)
df <- read.csv("https://raw.githubusercontent.com/plotly/datasets/master/2011_us_ag_exports.csv")
df$hover <- with(df, paste(state, '<br>', "Beef", beef, "Dairy", dairy, "<br>",
                           "Fruits", total.fruits, "Veggies", total.veggies,
                           "<br>", "Wheat", wheat, "Corn", corn))
# give state boundaries a white border
l <- list(color = toRGB("white"), width = 2)
# specify some map projection/options
g <- list(
  scope = 'usa',
  projection = list(type = 'albers usa'),
  showlakes = TRUE,
  lakecolor = toRGB('white')
)

fig <- plot_geo(df, locationmode = 'USA-states')
fig <- fig %>% add_trace(
    z = ~total.exports, text = ~hover, locations = ~code,
    color = ~total.exports, colors = 'Purples'
  )
fig <- fig %>% colorbar(title = "Millions USD")
fig <- fig %>% layout(
    title = '2011 US Agriculture Exports by State<br>(Hover for breakdown)',
    geo = g
  )

fig
```

<div id="htmlwidget-90cc9cf4cec8a1686347" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-90cc9cf4cec8a1686347">{"x":{"visdat":{"17817780cdc0":["function () ","plotlyVisDat"]},"cur_data":"17817780cdc0","attrs":{"17817780cdc0":{"locationmode":"USA-states","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"z":{},"text":{},"locations":{},"color":{},"colors":"Purples","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapType":"geo","scene":{"zaxis":{"title":"total.exports"}},"geo":{"domain":{"x":[0,1],"y":[0,1]},"scope":"usa","projection":{"type":"albers usa"},"showlakes":true,"lakecolor":"rgba(255,255,255,1)"},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5},"title":"2011 US Agriculture Exports by State<br>(Hover for breakdown)"},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"Millions USD","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(252,251,253,1)"],["0.0416666666666667","rgba(248,246,250,1)"],["0.0833333333333333","rgba(243,242,248,1)"],["0.125","rgba(239,237,245,1)"],["0.166666666666667","rgba(232,231,242,1)"],["0.208333333333333","rgba(225,224,238,1)"],["0.25","rgba(218,218,235,1)"],["0.291666666666667","rgba(208,208,230,1)"],["0.333333333333333","rgba(198,199,225,1)"],["0.375","rgba(188,189,220,1)"],["0.416666666666667","rgba(178,177,213,1)"],["0.458333333333333","rgba(168,166,207,1)"],["0.5","rgba(158,154,200,1)"],["0.541666666666667","rgba(148,144,195,1)"],["0.583333333333333","rgba(138,135,191,1)"],["0.625","rgba(128,125,186,1)"],["0.666666666666667","rgba(121,110,178,1)"],["0.708333333333333","rgba(114,96,171,1)"],["0.75","rgba(106,81,163,1)"],["0.791666666666667","rgba(99,67,156,1)"],["0.833333333333333","rgba(92,54,150,1)"],["0.875","rgba(84,39,143,1)"],["0.916666666666667","rgba(77,28,137,1)"],["0.958333333333333","rgba(70,16,131,1)"],["1","rgba(63,0,125,1)"]],"showscale":true,"locationmode":"USA-states","z":[1390.63,13.31,1463.17,3586.02,16472.88,1851.33,259.62,282.19,3764.09,2860.84,401.84,2078.89,8709.48,5050.23,11273.76,4589.01,1889.15,1914.23,278.37,692.75,248.65,3164.16,7192.33,2170.8,3933.42,1718,7114.13,139.89,73.06,500.4,751.58,1488.9,3806.05,3761.96,3979.79,1646.41,1794.57,1969.87,31.59,929.93,3770.19,1535.13,6648.22,453.39,180.14,1146.48,3894.81,138.89,3090.23,349.69],"text":["Alabama <br> Beef 34.4 Dairy 4.06 <br> Fruits 25.11 Veggies 14.33 <br> Wheat 70 Corn 34.9","Alaska <br> Beef 0.2 Dairy 0.19 <br> Fruits 0 Veggies 1.56 <br> Wheat 0 Corn 0","Arizona <br> Beef 71.3 Dairy 105.48 <br> Fruits 60.27 Veggies 386.91 <br> Wheat 48.7 Corn 7.3","Arkansas <br> Beef 53.2 Dairy 3.53 <br> Fruits 6.88 Veggies 11.45 <br> Wheat 114.5 Corn 69.5","California <br> Beef 228.7 Dairy 929.95 <br> Fruits 8736.4 Veggies 2106.79 <br> Wheat 249.3 Corn 34.6","Colorado <br> Beef 261.4 Dairy 71.94 <br> Fruits 17.99 Veggies 118.27 <br> Wheat 400.5 Corn 183.2","Connecticut <br> Beef 1.1 Dairy 9.49 <br> Fruits 13.1 Veggies 11.16 <br> Wheat 0 Corn 0","Delaware <br> Beef 0.4 Dairy 2.3 <br> Fruits 1.53 Veggies 20.03 <br> Wheat 22.9 Corn 26.9","Florida <br> Beef 42.6 Dairy 66.31 <br> Fruits 1371.36 Veggies 450.86 <br> Wheat 1.8 Corn 3.5","Georgia <br> Beef 31 Dairy 38.38 <br> Fruits 233.51 Veggies 154.77 <br> Wheat 65.4 Corn 57.8","Hawaii <br> Beef 4 Dairy 1.16 <br> Fruits 55.51 Veggies 24.83 <br> Wheat 0 Corn 0","Idaho <br> Beef 119.8 Dairy 294.6 <br> Fruits 21.64 Veggies 319.19 <br> Wheat 568.2 Corn 24","Illinois <br> Beef 53.7 Dairy 45.82 <br> Fruits 12.53 Veggies 39.95 <br> Wheat 223.8 Corn 2228.5","Indiana <br> Beef 21.9 Dairy 89.7 <br> Fruits 12.98 Veggies 37.89 <br> Wheat 114 Corn 1123.2","Iowa <br> Beef 289.8 Dairy 107 <br> Fruits 3.24 Veggies 7.1 <br> Wheat 3.1 Corn 2529.8","Kansas <br> Beef 659.3 Dairy 65.45 <br> Fruits 3.11 Veggies 9.32 <br> Wheat 1426.5 Corn 457.3","Kentucky <br> Beef 54.8 Dairy 28.27 <br> Fruits 6.6 Veggies 0 <br> Wheat 149.3 Corn 179.1","Louisiana <br> Beef 19.8 Dairy 6.02 <br> Fruits 17.83 Veggies 17.25 <br> Wheat 78.7 Corn 91.4","Maine <br> Beef 1.4 Dairy 16.18 <br> Fruits 52.01 Veggies 62.9 <br> Wheat 0 Corn 0","Maryland <br> Beef 5.6 Dairy 24.81 <br> Fruits 12.9 Veggies 20.43 <br> Wheat 55.8 Corn 54.1","Massachusetts <br> Beef 0.6 Dairy 5.81 <br> Fruits 80.83 Veggies 21.13 <br> Wheat 0 Corn 0","Michigan <br> Beef 37.7 Dairy 214.82 <br> Fruits 257.69 Veggies 189.96 <br> Wheat 247 Corn 381.5","Minnesota <br> Beef 112.3 Dairy 218.05 <br> Fruits 7.91 Veggies 120.37 <br> Wheat 538.1 Corn 1264.3","Mississippi <br> Beef 12.8 Dairy 5.45 <br> Fruits 17.04 Veggies 27.87 <br> Wheat 102.2 Corn 110","Missouri <br> Beef 137.2 Dairy 34.26 <br> Fruits 13.18 Veggies 17.9 <br> Wheat 161.7 Corn 428.8","Montana <br> Beef 105 Dairy 6.82 <br> Fruits 3.3 Veggies 45.27 <br> Wheat 1198.1 Corn 5.4","Nebraska <br> Beef 762.2 Dairy 30.07 <br> Fruits 2.16 Veggies 53.5 <br> Wheat 292.3 Corn 1735.9","Nevada <br> Beef 21.8 Dairy 16.57 <br> Fruits 1.19 Veggies 27.93 <br> Wheat 5.4 Corn 0","New Hampshire <br> Beef 0.6 Dairy 7.46 <br> Fruits 7.98 Veggies 4.5 <br> Wheat 0 Corn 0","New Jersey <br> Beef 0.8 Dairy 3.37 <br> Fruits 109.45 Veggies 56.54 <br> Wheat 6.7 Corn 10.1","New Mexico <br> Beef 117.2 Dairy 191.01 <br> Fruits 101.9 Veggies 43.88 <br> Wheat 13.9 Corn 11.2","New York <br> Beef 22.2 Dairy 331.8 <br> Fruits 202.56 Veggies 143.37 <br> Wheat 29.9 Corn 106.1","North Carolina <br> Beef 24.8 Dairy 24.9 <br> Fruits 74.47 Veggies 150.45 <br> Wheat 200.3 Corn 92.2","North Dakota <br> Beef 78.5 Dairy 8.14 <br> Fruits 0.25 Veggies 130.79 <br> Wheat 1664.5 Corn 236.1","Ohio <br> Beef 36.2 Dairy 134.57 <br> Fruits 27.21 Veggies 53.53 <br> Wheat 207.4 Corn 535.1","Oklahoma <br> Beef 337.6 Dairy 24.35 <br> Fruits 9.24 Veggies 8.9 <br> Wheat 324.8 Corn 27.5","Oregon <br> Beef 58.8 Dairy 63.66 <br> Fruits 315.04 Veggies 126.5 <br> Wheat 320.3 Corn 11.7","Pennsylvania <br> Beef 50.9 Dairy 280.87 <br> Fruits 89.48 Veggies 38.26 <br> Wheat 41 Corn 112.1","Rhode Island <br> Beef 0.1 Dairy 0.52 <br> Fruits 2.83 Veggies 3.02 <br> Wheat 0 Corn 0","South Carolina <br> Beef 15.2 Dairy 7.62 <br> Fruits 53.45 Veggies 42.66 <br> Wheat 55.3 Corn 32.1","South Dakota <br> Beef 193.5 Dairy 46.77 <br> Fruits 0.8 Veggies 4.06 <br> Wheat 704.5 Corn 643.6","Tennessee <br> Beef 51.1 Dairy 21.18 <br> Fruits 6.23 Veggies 24.67 <br> Wheat 100 Corn 88.8","Texas <br> Beef 961 Dairy 240.55 <br> Fruits 99.9 Veggies 115.23 <br> Wheat 309.7 Corn 167.2","Utah <br> Beef 27.9 Dairy 48.6 <br> Fruits 12.34 Veggies 6.6 <br> Wheat 42.8 Corn 5.3","Vermont <br> Beef 6.2 Dairy 65.98 <br> Fruits 8.01 Veggies 4.05 <br> Wheat 0 Corn 0","Virginia <br> Beef 39.5 Dairy 47.85 <br> Fruits 36.48 Veggies 27.25 <br> Wheat 77.5 Corn 39.5","Washington <br> Beef 59.2 Dairy 154.18 <br> Fruits 1738.57 Veggies 363.79 <br> Wheat 786.3 Corn 29.5","West Virginia <br> Beef 12 Dairy 3.9 <br> Fruits 11.54 Veggies 0 <br> Wheat 1.6 Corn 3.5","Wisconsin <br> Beef 107.3 Dairy 633.6 <br> Fruits 133.8 Veggies 148.99 <br> Wheat 96.7 Corn 460.5","Wyoming <br> Beef 75.1 Dairy 2.89 <br> Fruits 0.17 Veggies 10.23 <br> Wheat 20.7 Corn 9"],"locations":["AL","AK","AZ","AR","CA","CO","CT","DE","FL","GA","HI","ID","IL","IN","IA","KS","KY","LA","ME","MD","MA","MI","MN","MS","MO","MT","NE","NV","NH","NJ","NM","NY","NC","ND","OH","OK","OR","PA","RI","SC","SD","TN","TX","UT","VT","VA","WA","WV","WI","WY"],"type":"choropleth","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":13.31,"cmax":16472.88,"colorscale":[["0","rgba(252,251,253,1)"],["0.0416666666666667","rgba(248,246,250,1)"],["0.0833333333333333","rgba(243,242,248,1)"],["0.125","rgba(239,237,245,1)"],["0.166666666666667","rgba(232,231,242,1)"],["0.208333333333333","rgba(225,224,238,1)"],["0.25","rgba(218,218,235,1)"],["0.291666666666667","rgba(208,208,230,1)"],["0.333333333333333","rgba(198,199,225,1)"],["0.375","rgba(188,189,220,1)"],["0.416666666666667","rgba(178,177,213,1)"],["0.458333333333333","rgba(168,166,207,1)"],["0.5","rgba(158,154,200,1)"],["0.541666666666667","rgba(148,144,195,1)"],["0.583333333333333","rgba(138,135,191,1)"],["0.625","rgba(128,125,186,1)"],["0.666666666666667","rgba(121,110,178,1)"],["0.708333333333333","rgba(114,96,171,1)"],["0.75","rgba(106,81,163,1)"],["0.791666666666667","rgba(99,67,156,1)"],["0.833333333333333","rgba(92,54,150,1)"],["0.875","rgba(84,39,143,1)"],["0.916666666666667","rgba(77,28,137,1)"],["0.958333333333333","rgba(70,16,131,1)"],["1","rgba(63,0,125,1)"]],"showscale":false,"color":[1390.63,13.31,1463.17,3586.02,16472.88,1851.33,259.62,282.19,3764.09,2860.84,401.84,2078.89,8709.48,5050.23,11273.76,4589.01,1889.15,1914.23,278.37,692.75,248.65,3164.16,7192.33,2170.8,3933.42,1718,7114.13,139.89,73.06,500.4,751.58,1488.9,3806.05,3761.96,3979.79,1646.41,1794.57,1969.87,31.59,929.93,3770.19,1535.13,6648.22,453.39,180.14,1146.48,3894.81,138.89,3090.23,349.69]}},"geo":"geo","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### World Choropleth Map


```r
df <- read.csv('https://raw.githubusercontent.com/plotly/datasets/master/2014_world_gdp_with_codes.csv')

# light grey boundaries
l <- list(color = toRGB("grey"), width = 0.5)

# specify map projection/options
g <- list(
  showframe = FALSE,
  showcoastlines = FALSE,
  projection = list(type = 'Mercator')
)

fig <- plot_geo(df)
fig <- fig %>% add_trace(
    z = ~GDP..BILLIONS., color = ~GDP..BILLIONS., colors = 'Blues',
    text = ~COUNTRY, locations = ~CODE, marker = list(line = l)
  )
fig <- fig %>% colorbar(title = 'GDP Billions US$', tickprefix = '$')
fig <- fig %>% layout(
    title = '2014 Global GDP<br>Source:<a href="https://www.cia.gov/library/publications/the-world-factbook/fields/2195.html">CIA World Factbook</a>',
    geo = g
  )

fig
```

<div id="htmlwidget-278bb17de15941ae5c9a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-278bb17de15941ae5c9a">{"x":{"visdat":{"17815af63b5f":["function () ","plotlyVisDat"]},"cur_data":"17815af63b5f","attrs":{"17815af63b5f":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"z":{},"color":{},"colors":"Blues","text":{},"locations":{},"marker":{"line":{"color":"rgba(190,190,190,1)","width":0.5}},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapType":"geo","scene":{"zaxis":{"title":"GDP..BILLIONS."}},"geo":{"domain":{"x":[0,1],"y":[0,1]},"showframe":false,"showcoastlines":false,"projection":{"type":"Mercator"}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5},"title":"2014 Global GDP<br>Source:<a href=\"https://www.cia.gov/library/publications/the-world-factbook/fields/2195.html\">CIA World Factbook<\/a>"},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"GDP Billions US$","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top","tickprefix":"$"},"colorscale":[["0","rgba(247,251,255,1)"],["0.0416666666666667","rgba(239,246,252,1)"],["0.0833333333333333","rgba(230,240,250,1)"],["0.125","rgba(222,235,247,1)"],["0.166666666666667","rgba(214,230,244,1)"],["0.208333333333333","rgba(206,224,242,1)"],["0.25","rgba(198,219,239,1)"],["0.291666666666667","rgba(185,213,234,1)"],["0.333333333333333","rgba(172,208,230,1)"],["0.375","rgba(158,202,225,1)"],["0.416666666666667","rgba(142,193,221,1)"],["0.458333333333333","rgba(125,183,218,1)"],["0.5","rgba(107,174,214,1)"],["0.541666666666667","rgba(94,165,209,1)"],["0.583333333333333","rgba(81,155,203,1)"],["0.625","rgba(66,146,198,1)"],["0.666666666666667","rgba(57,135,192,1)"],["0.708333333333333","rgba(46,124,187,1)"],["0.75","rgba(33,113,181,1)"],["0.791666666666667","rgba(27,102,173,1)"],["0.833333333333333","rgba(19,91,164,1)"],["0.875","rgba(8,81,156,1)"],["0.916666666666667","rgba(9,70,139,1)"],["0.958333333333333","rgba(9,59,123,1)"],["1","rgba(8,48,107,1)"]],"showscale":true,"z":[21.71,13.4,227.8,0.75,4.8,131.4,0.18,1.24,536.2,10.88,2.52,1483,436.1,77.91,8.65,34.05,186.6,4.28,75.25,527.8,1.67,9.24,5.2,2.09,34.08,19.55,16.3,2244,1.1,17.43,55.08,13.38,65.29,3.04,1.98,16.9,32.16,1794,2.25,1.73,15.84,264.1,10360,400.1,0.72,32.67,14.11,0.18,50.46,33.96,57.18,77.15,5.6,21.34,205.6,347.2,1.58,0.51,64.05,100.5,284.9,25.14,15.4,3.87,26.36,49.86,0.16,2.32,4.17,276.3,2902,7.15,20.68,0.92,16.13,3820,35.48,1.85,246.4,2.16,0.84,4.6,58.3,2.74,1.04,6.77,3.14,8.92,19.37,292.7,129.7,16.2,2048,856.1,402.7,232.2,245.8,4.08,305,2129,13.92,4770,5.77,36.55,225.6,62.72,0.16,28,1410,5.99,179.3,7.65,11.71,32.82,47.5,2.46,2.07,49.34,5.11,48.72,63.93,51.68,10.92,11.19,4.41,336.9,2.41,12.04,10.57,0.18,4.29,12.72,1296,0.34,7.74,6.06,11.73,4.66,112.6,16.59,13.11,19.64,880.4,11.1,201,11.85,594.3,8.29,0.01,1.23,511.6,80.54,237.5,0.65,44.69,16.1,31.3,208.2,284.6,552.2,228.2,93.52,212,199,2057,8,0.81,1.35,0.56,0.22,0.75,0.83,1.86,0.36,777.9,15.88,42.65,1.47,5.41,307.9,304.1,99.75,49.93,1.16,2.37,341.2,11.89,1400,71.57,70.03,5.27,3.84,559.1,679,64.7,529.5,9.16,36.62,373.8,4.51,4.84,0.49,29.63,49.12,813.3,43.5,0.04,26.09,134.9,416.4,2848,17420,55.6,63.08,0.82,209.2,187.8,5.08,6.64,45.45,25.61,13.74],"text":["Afghanistan","Albania","Algeria","American Samoa","Andorra","Angola","Anguilla","Antigua and Barbuda","Argentina","Armenia","Aruba","Australia","Austria","Azerbaijan","Bahamas, The","Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bermuda","Bhutan","Bolivia","Bosnia and Herzegovina","Botswana","Brazil","British Virgin Islands","Brunei","Bulgaria","Burkina Faso","Burma","Burundi","Cabo Verde","Cambodia","Cameroon","Canada","Cayman Islands","Central African Republic","Chad","Chile","China","Colombia","Comoros","Congo, Democratic Republic of the","Congo, Republic of the","Cook Islands","Costa Rica","Cote d'Ivoire","Croatia","Cuba","Curacao","Cyprus","Czech Republic","Denmark","Djibouti","Dominica","Dominican Republic","Ecuador","Egypt","El Salvador","Equatorial Guinea","Eritrea","Estonia","Ethiopia","Falkland Islands (Islas Malvinas)","Faroe Islands","Fiji","Finland","France","French Polynesia","Gabon","Gambia, The","Georgia","Germany","Ghana","Gibraltar","Greece","Greenland","Grenada","Guam","Guatemala","Guernsey","Guinea-Bissau","Guinea","Guyana","Haiti","Honduras","Hong Kong","Hungary","Iceland","India","Indonesia","Iran","Iraq","Ireland","Isle of Man","Israel","Italy","Jamaica","Japan","Jersey","Jordan","Kazakhstan","Kenya","Kiribati","Korea, North","Korea, South","Kosovo","Kuwait","Kyrgyzstan","Laos","Latvia","Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Macau","Macedonia","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Marshall Islands","Mauritania","Mauritius","Mexico","Micronesia, Federated States of","Moldova","Monaco","Mongolia","Montenegro","Morocco","Mozambique","Namibia","Nepal","Netherlands","New Caledonia","New Zealand","Nicaragua","Nigeria","Niger","Niue","Northern Mariana Islands","Norway","Oman","Pakistan","Palau","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Poland","Portugal","Puerto Rico","Qatar","Romania","Russia","Rwanda","Saint Kitts and Nevis","Saint Lucia","Saint Martin","Saint Pierre and Miquelon","Saint Vincent and the Grenadines","Samoa","San Marino","Sao Tome and Principe","Saudi Arabia","Senegal","Serbia","Seychelles","Sierra Leone","Singapore","Sint Maarten","Slovakia","Slovenia","Solomon Islands","Somalia","South Africa","South Sudan","Spain","Sri Lanka","Sudan","Suriname","Swaziland","Sweden","Switzerland","Syria","Taiwan","Tajikistan","Tanzania","Thailand","Timor-Leste","Togo","Tonga","Trinidad and Tobago","Tunisia","Turkey","Turkmenistan","Tuvalu","Uganda","Ukraine","United Arab Emirates","United Kingdom","United States","Uruguay","Uzbekistan","Vanuatu","Venezuela","Vietnam","Virgin Islands","West Bank","Yemen","Zambia","Zimbabwe"],"locations":["AFG","ALB","DZA","ASM","AND","AGO","AIA","ATG","ARG","ARM","ABW","AUS","AUT","AZE","BHM","BHR","BGD","BRB","BLR","BEL","BLZ","BEN","BMU","BTN","BOL","BIH","BWA","BRA","VGB","BRN","BGR","BFA","MMR","BDI","CPV","KHM","CMR","CAN","CYM","CAF","TCD","CHL","CHN","COL","COM","COD","COG","COK","CRI","CIV","HRV","CUB","CUW","CYP","CZE","DNK","DJI","DMA","DOM","ECU","EGY","SLV","GNQ","ERI","EST","ETH","FLK","FRO","FJI","FIN","FRA","PYF","GAB","GMB","GEO","DEU","GHA","GIB","GRC","GRL","GRD","GUM","GTM","GGY","GNB","GIN","GUY","HTI","HND","HKG","HUN","ISL","IND","IDN","IRN","IRQ","IRL","IMN","ISR","ITA","JAM","JPN","JEY","JOR","KAZ","KEN","KIR","PRK","KOR","KSV","KWT","KGZ","LAO","LVA","LBN","LSO","LBR","LBY","LIE","LTU","LUX","MAC","MKD","MDG","MWI","MYS","MDV","MLI","MLT","MHL","MRT","MUS","MEX","FSM","MDA","MCO","MNG","MNE","MAR","MOZ","NAM","NPL","NLD","NCL","NZL","NIC","NGA","NER","NIU","MNP","NOR","OMN","PAK","PLW","PAN","PNG","PRY","PER","PHL","POL","PRT","PRI","QAT","ROU","RUS","RWA","KNA","LCA","MAF","SPM","VCT","WSM","SMR","STP","SAU","SEN","SRB","SYC","SLE","SGP","SXM","SVK","SVN","SLB","SOM","ZAF","SSD","ESP","LKA","SDN","SUR","SWZ","SWE","CHE","SYR","TWN","TJK","TZA","THA","TLS","TGO","TON","TTO","TUN","TUR","TKM","TUV","UGA","UKR","ARE","GBR","USA","URY","UZB","VUT","VEN","VNM","VGB","WBG","YEM","ZMB","ZWE"],"marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0.01,"cmax":17420,"colorscale":[["0","rgba(247,251,255,1)"],["0.0416666666666667","rgba(239,246,252,1)"],["0.0833333333333333","rgba(230,240,250,1)"],["0.125","rgba(222,235,247,1)"],["0.166666666666667","rgba(214,230,244,1)"],["0.208333333333333","rgba(206,224,242,1)"],["0.25","rgba(198,219,239,1)"],["0.291666666666667","rgba(185,213,234,1)"],["0.333333333333333","rgba(172,208,230,1)"],["0.375","rgba(158,202,225,1)"],["0.416666666666667","rgba(142,193,221,1)"],["0.458333333333333","rgba(125,183,218,1)"],["0.5","rgba(107,174,214,1)"],["0.541666666666667","rgba(94,165,209,1)"],["0.583333333333333","rgba(81,155,203,1)"],["0.625","rgba(66,146,198,1)"],["0.666666666666667","rgba(57,135,192,1)"],["0.708333333333333","rgba(46,124,187,1)"],["0.75","rgba(33,113,181,1)"],["0.791666666666667","rgba(27,102,173,1)"],["0.833333333333333","rgba(19,91,164,1)"],["0.875","rgba(8,81,156,1)"],["0.916666666666667","rgba(9,70,139,1)"],["0.958333333333333","rgba(9,59,123,1)"],["1","rgba(8,48,107,1)"]],"showscale":false,"color":"rgba(190,190,190,1)","width":0.5}},"type":"choropleth","geo":"geo","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Choropleth Inset Map


```r
df <- read.csv('https://raw.githubusercontent.com/plotly/datasets/master/2014_ebola.csv')
# restrict from June to September
df <- subset(df, Month %in% 6:9)
# ordered factor variable with month abbreviations
df$abbrev <- ordered(month.abb[df$Month], levels = month.abb[6:9])
# September totals
df9 <- subset(df, Month == 9)

# common plot options
g <- list(
  scope = 'africa',
  showframe = F,
  showland = T,
  landcolor = toRGB("grey90")
)

g1 <- c(
  g,
  resolution = 50,
  showcoastlines = T,
  countrycolor = toRGB("white"),
  coastlinecolor = toRGB("white"),
  projection = list(type = 'Mercator'),
  list(lonaxis = list(range = c(-15, -5))),
  list(lataxis = list(range = c(0, 12))),
  list(domain = list(x = c(0, 1), y = c(0, 1)))
)

g2 <- c(
  g,
  showcountries = F,
  bgcolor = toRGB("white", alpha = 0),
  list(domain = list(x = c(0, .6), y = c(0, .6)))
)
 
fig <- df %>% plot_geo(
    locationmode = 'country names', sizes = c(1, 600), color = I("black")
  )
fig <- fig %>% add_markers(
    y = ~Lat, x = ~Lon, locations = ~Country,
    size = ~Value, color = ~abbrev, text = ~paste(Value, "cases")
  )
fig <- fig %>% add_text(
    x = 21.0936, y = 7.1881, text = 'Africa', showlegend = F, geo = "geo2"
  )
fig <- fig %>% add_trace(
    data = df9, z = ~Month, locations = ~Country,
    showscale = F, geo = "geo2"
  )
fig <- fig %>% layout(
    title = 'Ebola cases reported by month in West Africa 2014<br> Source: <a href="https://data.hdx.rwlabs.org/dataset/rowca-ebola-cases">HDX</a>',
    geo = g1, geo2 = g2
  )

fig
```

<div id="htmlwidget-ac578896ef89a07f1a86" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-ac578896ef89a07f1a86">{"x":{"visdat":{"178128cd4850":["function () ","plotlyVisDat"],"17812d5bd5d6":["function () ","data"]},"cur_data":"17812d5bd5d6","attrs":{"178128cd4850":{"locationmode":"country names","color":{},"alpha_stroke":1,"sizes":[1,600],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"markers","locations":{},"size":{},"text":{},"inherit":true},"178128cd4850.1":{"locationmode":"country names","color":["black"],"alpha_stroke":1,"sizes":[1,600],"spans":[1,20],"x":21.0936,"y":7.1881,"text":"Africa","type":"scatter","mode":"text","showlegend":false,"geo":"geo2","inherit":true},"17812d5bd5d6":{"locationmode":"country names","color":["black"],"alpha_stroke":1,"sizes":[1,600],"spans":[1,20],"z":{},"locations":{},"showscale":false,"geo":"geo2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"mapType":"geo","title":"Ebola cases reported by month in West Africa 2014<br> Source: <a href=\"https://data.hdx.rwlabs.org/dataset/rowca-ebola-cases\">HDX<\/a>","geo":{"domain":{"x":[0,1],"y":[0,1]},"scope":"africa","showframe":false,"showland":true,"landcolor":"rgba(229,229,229,1)","resolution":50,"showcoastlines":true,"countrycolor":"rgba(255,255,255,1)","coastlinecolor":"rgba(255,255,255,1)","projection.type":"Mercator","lonaxis":{"range":[-15,-5]},"lataxis":{"range":[0,12]}},"geo2":{"scope":"africa","showframe":false,"showland":true,"landcolor":"rgba(229,229,229,1)","showcountries":false,"bgcolor":"rgba(255,255,255,0)","domain":{"x":[0,0.6],"y":[0,0.6]}},"scene":{"zaxis":{"title":"Month"}},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"locationmode":"country names","type":"scattergeo","mode":"markers","locations":["Guinea","Liberia","Senegal","Sierra Leone"],"text":["1022 cases","3362 cases","3 cases","1940 cases"],"name":"Sep","marker":{"color":"rgba(253,231,37,1)","size":[182.963403748884,600,1.35644153525736,346.570068432014],"sizemode":"area","line":{"color":"rgba(253,231,37,1)"}},"textfont":{"color":"rgba(253,231,37,1)","size":[182.963403748884,600,1.35644153525736,346.570068432014]},"line":{"color":"rgba(253,231,37,1)"},"geo":"geo","lat":[9.95,6.43,14.5,8.46],"lon":[-9.7,-9.43,-14.45,-11.78],"frame":null},{"locationmode":"country names","type":"scattergeo","mode":"markers","locations":["Guinea","Liberia","Senegal","Sierra Leone"],"text":["771 cases","1395 cases","1 cases","1216 cases"],"name":"Aug","marker":{"color":"rgba(53,183,121,1)","size":[138.229991074085,249.439750074383,1,217.538232668849],"sizemode":"area","line":{"color":"rgba(53,183,121,1)"}},"textfont":{"color":"rgba(53,183,121,1)","size":[138.229991074085,249.439750074383,1,217.538232668849]},"line":{"color":"rgba(53,183,121,1)"},"geo":"geo","lat":[9.95,6.43,14.5,8.46],"lon":[-9.7,-9.43,-14.45,-11.78],"frame":null},{"locationmode":"country names","type":"scattergeo","mode":"markers","locations":["Guinea","Liberia","Sierra Leone"],"text":["460 cases","329 cases","533 cases"],"name":"Jul","marker":{"color":"rgba(49,104,142,1)","size":[82.803332341565,59.4564117822077,95.8134483784588],"sizemode":"area","line":{"color":"rgba(49,104,142,1)"}},"textfont":{"color":"rgba(49,104,142,1)","size":[82.803332341565,59.4564117822077,95.8134483784588]},"line":{"color":"rgba(49,104,142,1)"},"geo":"geo","lat":[9.95,6.43,8.46],"lon":[-9.7,-9.43,-11.78],"frame":null},{"locationmode":"country names","type":"scattergeo","mode":"markers","locations":["Guinea","Liberia","Sierra Leone"],"text":["413 cases","107 cases","239 cases"],"name":"Jun","marker":{"color":"rgba(68,1,84,1)","size":[74.426956263017,19.8914013686403,43.4165426956263],"sizemode":"area","line":{"color":"rgba(68,1,84,1)"}},"textfont":{"color":"rgba(68,1,84,1)","size":[74.426956263017,19.8914013686403,43.4165426956263]},"line":{"color":"rgba(68,1,84,1)"},"geo":"geo","lat":[9.95,6.43,8.46],"lon":[-9.7,-9.43,-11.78],"frame":null},{"locationmode":"country names","text":"Africa","type":"scattergeo","mode":"text","showlegend":false,"geo":"geo2","marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"line":{"color":"rgba(0,0,0,1)"},"lat":[7.1881],"lon":[21.0936],"frame":null},{"locationmode":"country names","z":[9,9,9,9],"locations":["Guinea","Liberia","Senegal","Sierra Leone"],"showscale":false,"geo":"geo2","type":"choropleth","marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
