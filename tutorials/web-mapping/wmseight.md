---
id: 608
title: 'WMS 8 &#8211; SDI-in-a-Box: Web Mapping Frameworks'
date: 2012-07-31T14:31:56+00:00
author: Carl
layout: page
guid: http://giscollective.org/?page_id=608
---
[<&#8211; Part 7: Serving Your Map](http://giscollective.org/tutorials/web-mapping/wmsseven/)

**SDI-in-a-Box: Web Mapping Frameworks**

What’s exciting about all of the web mapping technology bits discussed in previous sections is that they can all be molded and combined in various ways to do new and interesting things with maps. Everything is customizable, and together they can provide a powerful range of functionality for creating interactive web maps. But the piecemeal approach presents challenges as well. For starters, some pieces fit together better than others. An integrated bundle of compatible software can be useful for Government institutions that require a complex application for displaying, querying, updating, and distributing geographic data as part of a Spatial Data Infrastructure (SDI). Businesses may just want an out-of-the-box solution that they don’t have to devote a lot of expensive man-hours to set up. These groups can save time and money while getting a product that meets their needs by looking toward some of the open-source frameworks that are out there. The most popular are summarized below.

1. [OpenGeo Suite:](http://opengeo.org/) Built by a non-profit team of experienced open-source developers, OpenGeo Suite is a popular and visually attractive bundle of open-source software that covers all levels of the development process. Available for Windows, Mac, and Linux platforms, it includes the PostGIS database, GeoServer, GeoWebCache for caching tiles, a browser-based mapping application called GeoExplorer, and a robust client-side API built on OpenLayers and GeoExt. Each module has an easy-to-master Graphic User Interface (GUI), including Postgres’ PgAdminIII database manager. The package comes in free Community and paid Enterprise editions, the difference being that customer support is provided to Enterprise buyers.

2. [OSGeo4W:](https://trac.osgeo.org/osgeo4w/) As the name implies, this is an OSGeo package that contains about 150 open-source software modules, including GDAL/OGR, QGIS, GRASS, MapServer, and OpenLayers. It is built for Windows only (_4W_). This is less an integrated framework and more just a big software bundle where each program runs more or less independently, but many of the components necessary for making and serving maps are included. The big missing piece is a DBMS; this will be necessary to install separately and build integration with MapServer.

3. [GeoMOOSE:](http://geomoose.org/) Built on MapServer and OpenLayers with the popular Dojo library for interface tools, the GeoMOOSE package provides a lightweight, attractive framework for basic web GIS. Geared toward state and local governments that want to distribute spatial data to the public, it comes with a modifiable demo application with a typical set up, including reprojection of WMS data into Spherical Mercator for use with tiled basemaps. The framework includes scripts for identify, search, and query operations, layer selection, and drawing functionality integrated into a WFS-T service to allow users to create, modify, and delete vector features on the map. The package claims to be highly configurable, and indeed their example applications—which include three put together by the Wisconsin State Cartographer’s Office—have some layout similarities but differ widely in styling.

<div>
  <dl id="attachment_123">
    <dt>
      <a href="http://wicoastalatlas.files.wordpress.com/2012/07/whaifinder.jpg"><img title="WHAIfinder" src="http://wicoastalatlas.files.wordpress.com/2012/07/whaifinder.jpg" alt="" width="549" height="354" /></a>
    </dt>
    
    <dd>
      Wisconsin State Cartographer’s Office WHAIFinder application, built with GeoMOOSE, won the 2011 Governor’s Award for Archival Innovation.<sup>33</sup>
    </dd>
  </dl>
</div>

4. [MapFish:](http://mapfish.org/) Created by French/Swiss/Austrian software company Camptocamp (not to be confused with the multilingual European mountaineering association of the same name), MapFish is an open-source mapping framework very similar to GeoMOOSE, although perhaps with less built-in functionality. It relies on server-side Python scripts and a client-side OpenLayers and GeoExt-based library for creating mapping applications with querying and feature-editing capabilities. It runs on Paster, a Python-based web server, and uses its own protocol for creating RESTful map services from database data, which it serves in GeoJSON format. A separate MapFish Print Java library for printing maps is available and integrates well with the framework.

5. [Geomajas:](http://www.geomajas.org/overview/about-geomajas) A graduated OSGeo project, Geomajas is a robust open-source web mapping framework built in Java. In includes just about every function you could want or need in a web GIS system, including support for multiple raster and vector layer types/services, projection transformations, a wide array of interactivity, drawing tools with the ability to anchor objects in screen or geographic space, custom tools, custom legends, support for user editing of data, highly configurable security methods, and more. The documentation is also thorough. Unlike frameworks that rely on JavaScript mapping libraries, almost all of the business logic is done through the server. It comes with two thin-client “faces,” a JavaScript skin that uses the Dojo user interface library, and an entirely Java-based one using Google Web Toolkit (GWT), which has a compiler that translates the Java code into JavaScript that runs in a browser without a plug-in. If you like working in Java instead of browser-based languages (JavaScript, PHP, XML, etc.), this is the web mapping software for you.

6. [MapGuide Open Source:](http://mapguide.osgeo.org/) First developed by Argus Technologies in 1995, this is one of the longest-lived web GIS frameworks out there. It was overhauled and turned into an open source project in 2005, and continues to be updated. It comes as a complete server-client package, including its own built-in map server and client APIs. While it is possible to bring in outside WMS and WFS services, it creates its own RESTful services for use by the client application. It does provide tile rendering and caching for a base layer, includes layer control, and allows for spatial queries.

7. [CartoDB:](http://cartodb.com/) Much more than a database, CartoDB is an entirely cloud-based, all-in-one package that includes data storage, styling, and publishing package. Of course it isn’t free in any meaningful way, with monthly prices starting at $29 for 50 MB of space and quickly rising into the hundreds. Data is added to PostGIS tables and manipulated through a web interface with graphic tools and a SQL dialog that takes any PostgreSQL-supported commands. Files can be exported to KML, Shapefile, CSV, and SQL, and imported from those as well as XLS, JSON, GPX, OSM, ODS, and GeoTIFF. The data can be visualized on a built-in map application, which includes tools for styling the data, customizing info windows, and creating choropleth coloring or proportional symbols. It also includes a dialog for styling using CartoCSS. A “Share” feature creates a link or embed code for the data mapped onto a Google basemap using TileJSON and Wax. CartoDB offers a SQL API for accessing the data through script and a Maps API that integrates well with Google Maps and Leaflet, but can be used with OpenLayers and other libraries. Vecnik is another library they offer that uses the SQL API, CartoCSS, and Modest Maps to render the data in the client’s browser instead of on the server, potentially allowing for greater interactivity (see Part 4).

**Sources**

<sup>31</sup>2012. TMS. OpenStreetMap Wiki. Accessed July 12, 2012. <<http://wiki.openstreetmap.org/wiki/TMS>>

<sup>32</sup>2010. WMS Tile Caching. OSGeo Wiki. Accessed July 30, 2012. <[http://wiki.osgeo.org/wiki/WMS\_Tile\_Caching](http://wiki.osgeo.org/wiki/WMS_Tile_Caching)>

<sup>33</sup>Veregin, Howard. 2011. WHAIFinder Project receives governor’s award for innovation. Wisconsin State Cartographer’s Office. <<http://www.sco.wisc.edu/news/whaifinder-award.html>