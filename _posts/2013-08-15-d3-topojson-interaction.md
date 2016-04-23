---
id: 12104
title: 'D3: Topojson Interaction'
date: 2013-08-15T10:00:57+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=12104
permalink: /d3-topojson-interaction/
categories:
  - Update
---

[bl.ock](http://bl.ocks.org/svmatthews/6083585), [gist](https://gist.github.com/svmatthews/6083585)

Interacting with the geographic data on your map is what gives web-maps a step up compared to static maps. All of that spatial information can hold it&#8217;s own attribute info, much like shapefiles. And all of that information is accessible on browser side with D3 and array interactions.

Simply, as the user interacts with the map, you can set which information should be returned to them. To take it one step further, you can use this information to computer new relationships and trends that effectively give web-mapping with spatial data a GIS feel. Upon updating your data, all of your spatial statistics will update as well, which doesn&#8217;t require you to re import your data as if you were creating a static map.

Taking from the previous example, [how to render topojson data](http://giscollective.org/d3-basemap-with-top/), the interaction portion is actually just a simple addition, but is only possible with the array created by D3. We&#8217;ll add the action item `.on('mouseover', ...)` to the data rendering process:

    .on('mouseover', function(d) {
        // grab specific data
        // use specific data
    })
    

The interactions with geographic data are numerous: `'mouseover', 'mouseout', 'mousedown', 'mouseup', 'mousemove'`. The following example looks for the `STATE_ABBR` property, passes it to a specific element in the HTML, and changes the style of the SVG element on the cursor entering and exiting the element.

    d3.json('us.json', function(error, us) {
        svg.selectAll('.states')
            .data(topojson.feature(us, us.objects.usStates).features)
            .enter()
            .append('path')
            .attr('class', 'states')
            .attr('d', path)
            .on('mouseover', function(d){
                // get state abbreviation
                var name = d.properties.STATE_ABBR;
                // add to element
                return document.getElementById('name').innerHTML=name; 
        });
    });
    

A _key component_ to this process is the difference between **`.data()`** and **`.datum()`**. In the topojson rendering tutorial, I used `.datum()` to define the source of the geometry. Datum is the singular of data. Therefore, your data object is treated as a single SVG object. Using `.data()` treats each iteration of the data as its own SVG element, allowing you to interact with each separately. The code difference is minimal, but the effect is enormous. See what [datum](http://bl.ocks.org/svmatthews/6195407) would do to your interactions with the svg canvas.