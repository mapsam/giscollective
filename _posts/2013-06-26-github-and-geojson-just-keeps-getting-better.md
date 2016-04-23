---
id: 11993
title: 'GitHub and GeoJSON: Just Keeps Getting Better'
date: 2013-06-26T12:25:11+00:00
author: Lyzi Diamond
layout: post
guid: http://giscollective.org/?p=11993
permalink: /github-and-geojson-just-keeps-getting-better/
categories:
  - 'Tips &amp; Tricks'
  - Update
  - Web Mapping
---
[<img class="aligncenter size-full wp-image-11994" alt="cluster" src="http://giscollective.org/wp-content/uploads/2013/06/cluster.png" width="626" height="498" />](http://giscollective.org/wp-content/uploads/2013/06/cluster.png)

GitHub has announced today some [new features](https://github.com/blog/1541-geojson-rendering-improvements) for rendering geographic data, coming off its [announcement two weeks ago](http://giscollective.org/github-bringing-geojson-to-life-since-2013/) that GeoJSON data would now be displayed on a map when opened inside a repo. These changes show that the folks over at GitHub are serious about the importance of geospatial, and recognize that more of the world&#8217;s developers are turning to maps and coordinates as a way to display, communicate, and analyze data. Spatial is special once again!

From the post:

>   * GitHub now supports rendering [TopoJSON](https://github.com/mbostock/topojson), an extension of GeoJSON that encodes topology and can be up to 80% smaller than their GeoJSON equivalents.
>   * Starting today, you don&#8217;t have to rename geo files with a new extension. GitHub will now render GeoJSON (and TopoJSON) in all [`.geojson`](https://github.com/search?q=extension%3Ageojson&type=Code&ref=searchresults), [`.topojson`](https://github.com/search?q=extension%3Atopojson&type=Code&s=), and[`.json`](https://github.com/search?q=FeatureCollection+extension%3Ajson&type=Code&s=indexed) files.
>   * Complex geographic datasets can often be difficult to visualize, especially if points are grouped close together. We now [automatically cluster](https://github.com/Leaflet/Leaflet.markercluster) nearby markers, allowing us to [better support larger datasets](https://github.com/benbalter/dc-maps).

You can also now use the rendered map and embed it elsewhere, which is great if you want a quick geographic visualization! Head over to the [original post](https://github.com/blog/1541-geojson-rendering-improvements) to read more, and let&#8217;s get some more geogeeks on the GitHubs!