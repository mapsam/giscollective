---
id: 12055
title: 'D3: Basemap With Topojson'
date: 2013-08-05T11:18:31+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=12055
permalink: /d3-basemap-with-top/
categories:
  - Web Mapping
---
<p dir="ltr">
  <a href="http://giscollective.org/d3">D3 Tutorials</a> : Example 003 ( <a href="http://bl.ocks.org/svmatthews/6081504">bl.ock</a> | <a href="https://gist.github.com/svmatthews/6081504">gist</a> )
</p>

To get geodata to render properly in D3, there are some key properties you will have to define first:

  * Canvas dimensions (width, height)
  * SVG Canvas
  * Projection
  * Path
  * path/to/geodata.file

Typically geodata has come in geojson format (an extension of json). It has been an incredibly useful format for quickly rendering geographic data on the web. It’s fast, to be sure, but D3 has taken the geojson one step further and now we have topojson (learn about geojson > topojson conversion [_coming soon_]), which has significantly decreased file size for polygonal geographic data. These tutorials will use topojson format for land basemap rendering. Be sure to add the topojson extension library to your header **after** you have loaded the d3 library:

    <script src="http://d3js.org/topojson.v1.min.js"></script>
    

There are some variables in here that will definitely require some playing around with depending on what you are trying to show. One of the best things d3.geo has going for it is the defining of projections. This gives d3 (and svg in general) an advantage to normal tile-based mapping because you can display different parts of the world in the geographic extent that suits that area best. Take a look at the [projections that come built in](https://github.com/mbostock/d3/wiki/Geo-Projections) with d3.geo and the [projections extension](https://github.com/d3/d3-geo-projection/).

<p dir="ltr">
  So, let’s set up those key components.
</p>

## Javascript

**Canvas Dimensions**

    var width = 960;
    var height = 500;
    

**SVG**

    var svg = d3.select('body').append('svg')
        .attr('width', width)
        .attr('height', height);
    

**Projection**

    var projection = d3.geo.albersUsa()
        .scale(1000)
        .translate([width / 2, height / 2]); 
        // https://github.com/mbostock/d3/wiki/Geo-Projections#wiki-translate
    

**Path**

    var path = d3.geo.path()
        .projection(projection);
    

**Data (Topojson)**

    d3.json('js/world.json', function(error, us) {
        svg.append('path')
            .datum(topojson.feature(us, us.objects.state))
            .attr('class', 'states') // defined in CSS
            .attr('d', path);
    });
    

## CSS

<pre>.states {
    fill: #e5e5e5;
    stroke: #fff;
    stroke-width: 2px;
}</pre>

Depending on the scale of your project, the javascript can sit within the body of your \`index.html\` file or it can be within a separate file if you have more functionality to build into the map.

[View the working file](bl.ocks.org/svmatthews/6081504) on bl.ocks.org.</p>