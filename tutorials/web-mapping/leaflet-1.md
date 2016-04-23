---
id: 61
title: 'Leaflet: Setup &#038; Basemap'
date: 2012-07-16T19:14:54+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=61
---
_By Max Axler, Sam Matthews, Chandler Sterling, and Matt McKenna_

**UPDATE 8/7/2013** The full tutorial has been updated to reflect the most recent stable version of leaflet.js &#8211; version 0.6.4. The tutorial explains how to build an HTML framework for leaflet and now has working examples on bl.ocks.org.

**UPDATE 8/5/2013** We have an updated example for our Leaflet 1 tutorial thanks to [Matthew McKenna](https://github.com/mpmckenna8). It is my understanding that updates have been made, rendering our tutorials obsolete. See a complete example of establishing a basemap using Leaflet at Matt&#8217;s Github repository: https://github.com/mpmckenna8/leaflettuts

* * *

There are many ways of putting spatial data online ranging from out of the box solutions such as Google’s Fusion Tables or Adobe Flash, to javascript libraries like Google Maps API. While the industry standard for javascript libraries has become Google Maps API, there are many reasons to seek out open alternatives. First, open javascript libraries are not subject to changing payment plans. Just recently, Google announced plans to charge on a per view basis after map views exceed a certain number. This tutorial will explain the set-up of a basic leaflet map.

## Step 1: HTML Framework

The first step to setting up any javascript web map is to put together the basic HTML framework. Using what you’ve learned from previous tutorials create the standard, and elements. Next, create a div with the ID of “map”. You will use this div as a container for the map object, which you will instantiate using the leaflet library.

    <div id = “map”></div>
    

You will also need to define some styling for the map `<div>`. This should be done through CSS styles in your `<head>` or in a separate `style.css` sheet.

    <style>
    #map {
        width:900px;
        height:500px;
    }
    </style>
    

When you have completed this setup code, create a new folder to house your web map and save the document as `index.html`.

## Step 2: Source & Setup

The next step is to download the leaflet source code and reference it in your html document. Point your web browser to [leafletjs.com](http://leafletjs.com) and download the latest stable version of leaflet (currently version 0.6.4) then move the contents of the folder into the same directory where you are storing the index.html document. Rename the downloaded folder leaflet to make it easier to reference in your code.

![leaflet directory structure](https://s3.amazonaws.com/gisc/wordpressImages/leaflet1.jpg)

Now that you have copies of the leaflet source code you need to referece the leaflet stylesheet and javascript files to your index page. To accomplish this place links within the head section of the document as follows.

    <link rel="stylesheet" href="leaflet/dist/leaflet.css" />
    <!--[if lte IE 8]>
        <link rel="stylesheet" href="leaflet/dist/leaflet.ie.css" />
    <![endif]-->
    <script type="text/javascript" src="leaflet/dist/leaflet.js"></script>
    

Note: Since versions of Internet Explorer are outdated (anything less than IE9) they will require a separate stylesheet. To make your map compatible with older versions of IE, be sure to include the `<!--[if]>` statement after the first CSS reference.

## Step 3: Script

The final step to creating your basic Leaflet map is write the script that loads your map. Now that you have created a space in the html for your map to sit, and connected a series of functions via the leaflet library, you can call these functions to create your interactive map. The first thing you should do, is create a new script within the head of the document.

    <script type="text/javascript">
      // your javascript code 
    </script>
    

Next, it is good practice to wrap your entire map script in the function:

    window.onload = function () { };
    

This ensures that your map script won’t run until the web page structure has loaded, preventing leaflet from trying to load your map in a non-existent div. First we&#8217;ll set some parameters for the basemap such as the center point and the zoom level. The following will also run the `L.map` function, which instantiates your map on a specified id (typically a div defined in your css).

    var map = L.map('map').setView([43.07265,-89.400929], 10);
    

Now you need to tell leaflet what type of tile layer to use. Tiles are simply a series of png images that make up the basemap of any javascript based webmap. Tiling allows your web browser to load base maps quickly at a variety of scales. Since leaflet is designed to be open and modular, you can load these tiles from a number of sources (such as google, tilemill, open street maps). We&#8217;ll use Open Street Maps here:

    L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
        attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map); 
    

This segment of code pulls the images from OSM&#8217;s tile server based on the X,Y, Z coordinates of your current map pane. In short, your script should look something like this:

    <script type="text/javascript">// 
        window.onload = function () {
            var map = L.map('map').setView([43.07265,-89.400929], 10);
            L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
            }).addTo(map);
        };
    </script>
    

Test it out in a browser by double clicking your index page or opening it on a localhost server. If you are having problems check out the completed code example on **[bl.ocks](http://bl.ocks.org/svmatthews/6175629)**.

**Creating a Marker:** Once you’ve instantiated your map object &#8211; you can add data in a variety of ways. The simplest is to manually geocode points. The code for this process can be found in the documentation portion of leaflet’s website. Basically all you have to do is specify a latitude and longitude, append it to leaflet&#8217;s `L.marker` function, and pass the `.bindPopup()` and `.openPopup()` functions

    L.marker([43.07265,-89.400929]).addTo(map)
        .bindPopup('Science Hall<br>Where the GISC was born.')
        .openPopup();
    

This will automatically open the popup on the page load. See the complete code example on **[bl.ocks](http://bl.ocks.org/svmatthews/6175692)**.

[Part 2: Bringin in data as a geoJSON –>](http://giscollective.org/tutorials/web-mapping/leaflet-2)