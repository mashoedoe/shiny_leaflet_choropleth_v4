# Shiny Leaflet Choropleth (version 4)
A choropleth map of South Africa at ward, municipal & provincial level built in R using @RStudio's Shiny, their R package for @Leaflet and system call's to @mbloch's mapshaper to convert source map files from ESRI shapefiles to @mbostock's TopoJSON format.

R scripts to recreate the GIS data for this app can be sourced at [https://github.com/mashoedoe/shiny_leaflet_choropleth]. This version tries to improve by creating reactiveValues that allow different map levels to call the same leafletProxy functions (where possible) no matter the map object sourced for that level. When the user is at the Province and Municipal levels, the map objects are built from topojson string objects only for faster load times but individual geometries can't be manipulated individually or styled in the App but must be done using the R scripts during pre-processing. 

The highest detail level, 'Ward' uses R's SpatialPolygonDataframe object format subsetted (to reduce load time and memory usage) to display only a single municipality of Wards on top of a topojson string object of the whole country's municipalities. The topojson base records mouseover events that are used to select the next municipality of Wards for dispaly as the user's mouse moves across the map.

Inspired by @jcheng5's [https://jcheng.shinyapps.io/choropleth3] and @jcheng5 & @yihui's [https://github.com/rstudio/leaflet/blob/master/inst/examples/shiny.R]
