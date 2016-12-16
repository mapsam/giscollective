---
id: 212
title: 'WMS 2 &#8211; Tile Maps and APIs'
date: 2012-07-17T12:57:34+00:00
author: Carl
layout: page
guid: http://giscollective.org/?page_id=212
---
[<&#8211; Part 1: WMS: The Standard That Isn&#8217;t](http://giscollective.org/tutorials/web-mapping/wmsone/)

**Tile Maps and APIs**

Say you’re playing around on Google Maps. You click and hold your mouse button to magically drag the map around from Timbuktuto Connecticut. Then you zoom in on Schenectadyuntil you can see your cousin’s car parked in his driveway and his kid playing with his dog in the yard. You might not think much of it now, but let’s remember that all of this was novel just a few years ago. This new (circa 2005) sort of interface is called a _slippy map._

Since Gmaps covers the whole planet, and at 18 different scales to boot, the whole map would be WAY too much data for a server to send to your poor little laptop all at once. So what Google cleverly did was slice the map up into a bunch of smaller images, or tiles, which are stored on their servers in some huge warehouse in Wallawallastan. In your browser window, you only see a few tiles at once, and the rest are still packed away in the warehouse. Now say you click and drag the map over. Using a piece of JavaScript calledAJAX, your mouse action just told the server, “hey! I need more tiles over here!” Faster than you can blink, your browser dumps the tiles it doesn’t need anymore because they’re off your screen, and the server shoots you the new ones that make your new map view complete.

This is generally referred to as a _Tile Service_. It sends your browser a certain number, depending on the scale, of 256 x 256 pixel PNG (Portable Network Graphic) files, stored in a specialized folder hierarchy to conform to a universal URL tile request format.<sup>5</sup> On the server, each zoom level is a directory, each column of tiles a sub-directory, and each tile within that column a separate file. The URL for a tile is thus /tiles/zoom/x/y.png, also written as /{z}/{x}/{y}. The {z} directory is a number between 0 (a single tile covering the whole world) and the maximum zoom level, typically between 18 and 22. Folder names for {x} and filenames for {y} are determined by calculating the projected lat/long coordinates for the upper-left corner of each tile and indexing them according to the total number of map tiles (for more details on how tiles are indexed, see the excellent [OSM wiki page](http://wiki.openstreetmap.org/wiki/Slippy_map_tilenames) on the subject).

This format is specified in the OGC’s _Tile Map Service _(TMS) standard. But, confusingly, most public tile services don’t _quite _conform to the standard. Many follow Google’s lead, and their style does not support multiple spatial reference systems, which the TMS standard calls for. They also flip the y-coordinates for the tiles, so they are numbered north-to-south instead of TMS-standard south-to-north.<sup>6</sup>

Standards-compliant or not, most public tile services are easy to access using their own Application Programming Interface (API) or a publicly-available JavaScript library such as Modest Maps, Leaflet, or OpenLayers. An API is a set of functions and methods, written in any of a number of programming languages, that can be used to access a specific web application. It is essentially a collection of web services bundled together to work with an existing piece of internet software (e.g., Google Maps).<sup>7</sup> An API can, but does not necessarily need to, include one or more WMS or TMS. The API includes the functions needed to access various properties of the tile service it’s associated with, but can usually be added to in order to access a different tile service or layers from a WMS server. APIs often include their own methods for adding a map layer from an image file or drawing a vector layer on top of the map. The addition of custom layers on top of an existing tile service is commonly referred to as a _map_ _mash-up._<figure class="wp-caption aligncenter" style="width: 244px">

<img class=" " title="Routes for retrieving online maps" src="http://wicoastalatlas.files.wordpress.com/2012/06/api-wms.jpg" alt="" width="234" height="342" /><figcaption class="wp-caption-text">Routes for retrieving online maps</figcaption></figure> 

[Part 3: Public Tile Services &#8211;>](http://giscollective.org/wmsthree/)

**Sources:**

<sup>5</sup>2012. Serving Tiles. Switch2OSM. OpenStreetMap and contributors. Accessed June 29, 2012. <<http://switch2osm.org/serving-tiles/>>

<sup>6</sup>2012. TMS. OpenStreetMap Wiki. Accessed July 12, 2012. <<http://wiki.openstreetmap.org/wiki/TMS>>

<sup>7</sup>Gosnell, D. M. 2005. Professional Development with Web APIs. Wrox Press.