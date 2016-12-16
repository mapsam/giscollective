---
id: 499
title: 'WMS 7 &#8211; Serving Your Map'
date: 2012-07-23T12:39:16+00:00
author: Carl
layout: page
guid: http://giscollective.org/?page_id=499
---
[<&#8211; Part 6: Making Your Own Tiles](http://giscollective.org/wmssix)

**Serving Your Map**

Harkening back to Part 1, recall that the map image you see on your computer screen when you go to Google or MapQuest has to be _served, _i.e. sent from a database or memory cache to the client’s browser. This is the job of the web (or HTTP) server, a piece of software that sits on a host computer, relays requests from clients, and sends them back the information or images they are requesting. Once you have the information or images you want to share with internet users, you need a server to do the sharing for you. The most popular servers out there are open-source [Apache](http://httpd.apache.org/) and Microsoft’s proprietary [IIS](http://www.iis.net/). Another option that has gained a tremendous amount of use over the past few years is [Amazon’s cloud servers](http://aws.amazon.com/), which are hosted remotely from a warehouse and provide a powerful solution for those who would rather deal with monthly subscription fees than server configuration and hardware maintenance.

Web servers can send data, including images, to client browsers. But georeferenced maps are special images in that they include spatial relationships that must be maintained. Thus, it is easiest to serve them using specialized software that is built for the job and tacked onto a web server, called a _map server. _Map servers have built-in functionality to create services such as WMS and Tile services. The most popular map servers are listed below.

1. [MapServer:](http://mapserver.org/index.html) One of the oldest pieces of web mapping infrastructure out there, MapServer dates back to 1994, when NASA gave a grant to the University of Minnesota to develop a way to make satellite forest cover data publicly available.<sup>26</sup> Now on version 6, it remains a robust suite of open-source server software popular with GIS professionals. Its primary task is to render GIS data into images and send them to clients’ browsers through a connected Apache server. It can draw data both from local files and databases and from web services, and can be made to spit out pretty much any kind of map image you can think of, from static PDF to WMS to tiles and even Flash. One advantage to serving your own data this way is that you don’t have to settle for Greenland looking like it could swallow Australia on your web map. MapServer supports on-the-fly projection using the PROJ.4 library of 40-some different projections. The downsides are somewhat complicated setup and rendering that tends to produce maps with a less-than-aesthetically-pleasing look and feel.

<div>
  <dl id="attachment_116">
    <dt>
      <a href="http://wicoastalatlas.files.wordpress.com/2012/07/mapserver.jpg"><img title="MapServer" src="http://wicoastalatlas.files.wordpress.com/2012/07/mapserver.jpg" alt="" width="529" height="526" /></a>
    </dt>
    
    <dd>
      “The basic architecture of MapServer applications” from the MapServer website.<sup>27</sup>
    </dd>
  </dl>
</div>

2. [GeoServer:](http://geoserver.org/display/GEOS/Welcome) A complete map server built in Java, GeoServer can publish any spatial data source as an OGC-compliant web service. It serves data as WMS, WCS, WFS, and WPS (web processing service). The GeoWebCache application can be seamlessly integrated, which takes GeoServer’s WMS and renders and caches tiles from it as TMS or WMTS (Google-style tiles). The browser-based graphic interface is easy to navigate, with quick links for server administration, importing and styling data, and layer settings. Styles can be edited natively and saved or uploaded as XML-based SLD (Styled Layer Description) stylesheets. It comes integrated with OpenLayers for previewing data. There’s even a link to the very good documentation from the administration page. It has fewer output options than MapServer, but is better-organized and more user-friendly.

<div>
  <dl id="attachment_117">
    <dt>
      <a href="http://wicoastalatlas.files.wordpress.com/2012/07/geoserver.jpg"><img title="GeoServer" src="http://wicoastalatlas.files.wordpress.com/2012/07/geoserver.jpg" alt="" width="549" height="319" /></a>
    </dt>
    
    <dd>
      GeoServer’s attractive user interface
    </dd>
  </dl>
</div>

3. [ArcGIS for Server:](http://www.esri.com/software/arcgis/arcgisserver) A popular commercial product, ESRI’s server is integrated with its other Arc software. Data is added to the server through ArcCatalog and can be served as image files, globe files, geoprocessing commands, KML, WMS, WCS, WFS, and WFS-T.<sup>28</sup> Tiles can be generated and cached using ArcToolbox’s Server tools. The server comes bundled with an out-of-the-box web application configured through a wizard, and ArcMap and ArcExplorer can also be used as clients to preview services. The more pricey package also includes a configurable mobile web app. ArcServer can publish files generated with ArcMap and interface with a number of database management systems through ArcSDE, ESRI’s spatial database extension that piggybacks on the DBMS.<sup>29</sup> Version 10 requires a 64-bit Windows or Linux operating system.

4. [QGIS Server:](http://hub.qgis.org/projects/quantum-gis/wiki/QGIS_Server_Tutorial) The popular open source alternative to ArcGIS, Quantum GIS (QGIS) provides a full desktop GIS application with many functions useful for preparing map data (see Section 5). The application also comes with its own built-in map server, which can publish any recognized data format as a WMS. Setup is quick and easy. QGIS Server needs to be set up as a CGI/FastCGI Apache module, then you just drop the QGIS project file into the server directory, and a WMS is created that looks just like the map does in the desktop software.

5. [deegree:](http://www.deegree.org/) Professionally developed by the German GIS company lat/lon, deegree is now an open-source OSGeo project. It is written in Java. Its focus is on completely OGC-compliant web services, including WMS, WFS, WPS, WMTS, and Catalog Service for the Web (CSW). It includes the ability to cache and serve tiles.

There are many other commercial map server options out there, and it would be a poor use of time and space to detail them all. Those I discovered from searching online which I haven’t covered are linked to below.<sup>30</sup>

[Manifold Internet Map Server](http://www.manifold.net/info/ims.shtml)

[Safe Software FME Server](http://www.safe.com/fme/fme-technology/fme-server/overview/)

[Intergraph GeoMedia Map Publisher](http://www.intergraph.com/sgi/downloads.aspx?assetid=165)

[Oracle Fusion Middleware MapViewer](http://www.oracle.com/technetwork/middleware/mapviewer/overview/index.html)

[Google Earth Enterprise](http://www.google.com/enterprise/earthmaps/enterprise.html)

[VDS Technology AspMap](http://www.vdstech.com/aspmap.aspx)

[SpatialMedia map-TV Map Server](http://www.spatialmedia.com/products/products.html)

[GenericLogic GLG Map Server](http://www.genlogic.com/free_map_server.html)

[Demis Web Map Server](http://www.demis.nl/home/pages/wms/demiswms.htm)

_Tile Servers:_

These common server applications typically work with a map server to speed up the serving of tiles for slippy maps. A separate renderer is typically used to create the map image itself, possibly as many map images in a tile directory structure. Some tile servers can slice up one large map image into more manageable tiles. Their main function is to send only the tiles requested by the client, resulting in less data having to be transported than by untiled services. Most tile servers create a server-side cache to store the tiles so they don’t have to be regenerated on the fly every time they are requested by a user. While they can be stand-alone applications, which tile server to use usually depends on which map server you’re using. The most popular are listed below.

1. [Mod tile:](http://wiki.openstreetmap.org/wiki/Mod_tile) An exception to server-side caching of tiles is used by OpenStreetMap, which serves tiles by rendering the data from each request on the fly with Mapnik, then serving the tile with a specialized Apache server module called Mod tile. Mod tile’s job is to request the creation of needed tiles if they are not already cached in the user’s browser or if the data has changed since they were last cached. While slower than server-side caching, this system requires less host storage space, which is important when you consider the many terabytes of storage space required by Google Maps and the relatively limited resources of the open-source community.

2. [TileCache:](http://tilecache.org/) This python-based library caches WMS and TMS files, speeding up the serving of the data. It can be combined with a rendering engine such as Mapnik, MapServer, or Cascading WMS to cache and serve tilesets, and was designed to work with OpenLayers for accessing the cached tiles.

3. [TileStache:](http://tilestache.org/) Another Michal Migurski project, TileStache was put together to address the lack of support for layering in TileCache. It is a server-side application designed to render and serve tiles from different data sources layered on top of one another. It includes functionality to render SVG vector tiles for use in Stamen’s Polymaps JavaScript library. Its most notable use to date is as a rendering engine behind Stamen’s Prettymaps (covered in Part 3), and it has the potential for other creative uses for those with some server know-how and a desire to combine data in new and interesting ways.

4. [MapCache:](http://mapserver.org/trunk/mapcache/) MapServer’s tile caching plug-in supports tile requests using WMS, TMS, WMTS, KML, Bing/Virtual Earth, and Google services. It can respond to WMS GetFeatureInfo requests and untiled WMS requests as well as tile requests, merging tiles into a fused image for the latter function.

5. [GeoWebCache:](http://geowebcache.org/docs/current/index.html) GeoServer’s tile caching plug-in is built in Java and also supports WMS, TMS, WMTS, KML, Bing and Google services. It can be used as a standalone application or integrated into GeoServer. When integrated, it automatically configures GeoServer services as tile maps with default styles and two projections, Spherical Mercator and Lat/Long (Equirectangular, the OpenLayers default projection).

<div>
  <dl id="attachment_118">
    <dt>
      <a href="http://wicoastalatlas.files.wordpress.com/2012/07/geowebcache_howitworks.jpg"><img title="GeoWebCache_howitworks" src="http://wicoastalatlas.files.wordpress.com/2012/07/geowebcache_howitworks.jpg" alt="" width="396" height="151" /></a>
    </dt>
    
    <dd>
      A straightforward diagram of the role of a tile cache/tile server from GeoWebCache. The central tower represents the tile server, and the blue container the cache where tiles are stored. Notice the green arrow is much larger than the blue ones, meant to represent the tile server’s ability to respond to most client requests without having to consult the back-end WMS servers, speeding up the process greatly.
    </dd>
  </dl>
</div>

6. [MapProxy:](http://mapproxy.org/) A tile server that supports WMS-C (WMS Tile Caching),<sup>32</sup> TMS, WMTS, and KML, it caches tiles and supports on-the-fly reprojection of WMS data into a range of projections. Aside from speedier map serving, the application has some nice bells and whistles, like storing identical tiles as one image and embedding custom watermarks on tiles.

7. [TileStream:](https://github.com/mapbox/tilestream#readme) Used by MapBox to support their map hosting service, Tilestream can only serve pre-generated tiles stored in MBTiles format. It is not designed to handle live services, but can work on a server if you decide to create a custom tileset using TileMill and host it locally.

[Part 8: SDI-in-a-Box: Web Mapping Frameworks &#8211;>](http://giscollective.org/tutorials/web-mapping/wmseight/)

**Sources**

<sup>26 </sup>2012. MapServer. Wikipedia. Accessed July 4, 2012. <<http://en.wikipedia.org/wiki/Mapserver>>

<sup>27 </sup>McKenna, Jeff. 2011. An Introduction to MapServer. Accessed July 26, 2012. <<http://www.mapserver.org/introduction.html>>

<sup>28 </sup>2009. ArcGIS Server: A Complete and Integrated Server GIS. Redlands, CA: ESRI. <<http://www.esri.com/library/brochures/pdfs/arcgis-server.pdf>>

<sup>29 </sup>What is ArcGIS Server? ESRI Web Help. Accessed July 26, 2012. <<http://webhelp.esri.com/arcgisserver/9.2/dotnet/manager/concepts/whats_server.htm>>

<sup>30 </sup>List of Map Service Software. StackExchange Geographic Information Systems Wiki. Accessed July 26, 2012. <<http://gis.stackexchange.com/questions/12493/list-of-map-service-software>>