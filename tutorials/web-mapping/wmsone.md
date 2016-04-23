---
id: 178
title: 'WMS 1 &#8211; The Standard That Isn&#8217;t'
date: 2012-07-17T12:35:43+00:00
author: Carl
layout: page
guid: http://giscollective.org/?page_id=178
---
**WMS: The Standard That Isn’t**

When you think of the words &#8220;Web Map Service,&#8221; you might think of something that generally defines all maps that are out there on the internet. You might think it could refer to getting directions to Grandma&#8217;s house on a Google Map, or you might think of a New York Times map of entitlement program use. In both cases, you&#8217;d be wrong.

A Web Map Service (WMS) is an Open Geospatial Consortium (OGC) specification that “defines a common interface for disseminating digital maps, rendered from spatial data, across the Internet. WMS supports the networked interchange of web based map layers, which are generally rendered in a digital image such as JPEG, GIF, PNG, etc.”<sup>1</sup>

In English, a WMS is computer language (script) that tells a server, “gimme your map!” The server then responds by sending an image file to your (the client’s) browser (e.g., Firefox, etc.). It is important to note that a WMS is _not _a map mash-up or a slippy map, which are increasingly the norm of interactive web maps made for public consumption.

WMS was the first standard put forward by the OGC to define how map servers _should_ communicate with client computers. It is still used by a lot of folks. But the thing about standards is that they are recommendations, not laws. And some people&#8211;in this case, those that control the majority of the web map market&#8211;like to play by their own rules. But first understanding how WMS works can be helpful to understanding those rules as well.

A Web Map _Service _is a _script._ A WMS _server _is the piece of software that actually responds to the script and sends you your requested image. Examples of this software include MapServer (open source) and ArcIMS (proprietary). The term _server _is commonly used to also mean the physical computer running the server software, but technically, the computer is the _host_. The server is the software program that serves clients from the host.<figure class="wp-caption aligncenter" style="width: 910px">

<img class="   " title="A metaphorical diagram of server-client architecture" src="http://wicoastalatlas.files.wordpress.com/2012/06/wmsarchitecture.jpg" alt="" width="900" height="180" /><figcaption class="wp-caption-text">A metaphorical diagram of server-client architecture</figcaption></figure> 

A WMS script consists of three different types of JavaScript requests (“can I have this please?”) made by a browser to a server.<sup>2</sup> Each request is in the form of a URL (web address) that specifies the server and what information is being requested from it—what’s referred to as RESTful (REpresentational State Transfer) style. WMS servers are required to support two of the requests, and the third is optional.

The first request, GetCapabilities, asks the server for information about what it has to offer. It’s like asking to see the menu at a restaurant where everything is a-la-carte. The server gives you an answer in XML: I have these data layers and can give you this many tiles at once in these styles, etc.

The next thing that has to happen to make your map work is a GetMap request. This is like giving the waiter your order. The request includes a list of parameters that include the layer names, styles, a coordinate reference system, bounding coordinates of the map to be returned, the width and height of the map, and some other optional ones.<sup>3</sup>

The third type of request, GetFeatureInfo, is optional, and only works on layers that are queryable, meaning that it contains features with data you can access. This is something that is often set up to be triggered by clicking on a feature on the map, and the info that gets returned is shown in some kind of pop-up window or panel.

The end result of a WMS is a layer rendered in a client’s browser. Now, if you want the client to be able to do stuff to that layer—say, turn it on and off, move it around, zoom in and out, put other layers on top of it, etc.—you need a bit more JavaScript. In the bad old days of 2004, all this sort of script was custom-built, so you usually didn’t mess with it unless you were a professional programmer. But then along came Google Maps, raster tiles, and web map APIs.<sup>4</sup>

[Part 2: Tile Maps and APIs &#8211;>](http://giscollective.org/tutorials/web-mapping/wmstwo/)

**Sources:**

<sup>1</sup>Wright, D., Dwyer, N., Cummins, V., eds. 2011. Coastal Infomatics: Web Atlas Design and Implementation.New York: Information Science Reference.

<sup>2</sup>de La Beaujardiere, J. (ed.) 2005. Web Map Service. OGC 04-024, version 1.3. Open Geospatial Consortium Inc.

<sup>3</sup>2012. Web Map Service. Wikipedia. Accessed June 21, 2012. <[http://en.wikipedia.org/wiki/Web\_map\_service](http://en.wikipedia.org/wiki/Web_map_service)>

<sup>4</sup>2012. Web Mapping. Wikipedia. Accessed June 25, 2012. <http://en.wikipedia.org/wiki/Web_cartography>