---
id: 95
title: 'Leaflet: GeoJSON Data'
date: 2012-07-16T23:07:24+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=95
---
**UPDATE 8/9/2013:** This tutorial has been updated to reflect the **0.6.4** version API for leaflet.js

## Adding a GeoJSON layer

First we need to get some data. We&#8217;ll just use a simple dataset of world country borders from [Johan Sundström&#8217;s collection](https://github.com/johan/world.geo.json) on github. You can also use shapefile data and convert it to geojson using some different conversion techniques (i.e. [GDAL & OGR](http://giscollective.org/tutorials/gis-techniques/spatial-data-conversion-using-python/)). Save it to the same directory as your index page for the leaflet map. It is important that you change the extension from `.json` to `.js` for this to work and link it in your `index.html` **after** your `leaflet.js` file:

    <script src="countries.js" type="text/javascript"></script>
    

Within your geojson file (`countries.js`) you want to set the entire geojson as a variable so it is accessible from within your script.

    var countries = {"type":"FeatureCollection", ... // rest of geojson
    

Once you have your `index.html` linking to the correct `.js` files and you have your [leaflet basemap](http://giscollective.org/tutorials/web-mapping/leaflet-1/) rendering properly, we can import the geojson via the `L.geoJson` function in leaflet.

    L.geoJson(countries, {
        // other variables (not required)
    }).addTo(map);
    

Simple as pie. `countries` was defined in your `countries.js` file that contains your geojson, remember. This will assign some generic styles to the data.

## GeoJSON Style & Interaction

Above you can see that `L.geoJson` allows for additional variables to be defined in addition to adding the GeoJSON to the map. This is where you give the data its styles and functionality on user interactions. You may want to style your data by assigning those styles to a variable:

    var countryStyle = {
        'color': '#000',
        'weight': 5,
        'opacity': 0.6
    };
    

You may also want to add some UI functionality by defining a function that dives into the properties data of your GeoJSON feature. The following is using Leaflet&#8217;s core popup functionality:

    function popup(feature, layer) {
        if (feature.properties && feature.properties.name) {
            layer.bindPopup(feature.properties.name);
        }
    }
    

This function checks to make sure the `properties` portion of the GeoJSON exists as well as the property `name`, which is unique to the data file. The `layer.bindPopup` function inherently builds the click functionality into the map. Your code will now look something like the following:

    L.geoJson(countries, {
        onEachFeature: popup, // onEachFeature is built in
        style: countryStyle
    }).addTo(map);
    

That&#8217;s that! You can see that `onEachFeature` is a property of the `L.geoJson` that can be passed with a function. Make sure to [view the working file](http://bl.ocks.org/svmatthews/6197016) on bl.ocks.org.

[<- Leaflet: Setup & Basemap](http://giscollective.org/tutorials/web-mapping/leaflet-1/)