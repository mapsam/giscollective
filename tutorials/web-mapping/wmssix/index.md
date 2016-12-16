---
id: 492
title: 'WMS 6 &#8211; Making Your Own Tiles'
date: 2012-07-23T12:34:00+00:00
author: Carl
layout: page
guid: http://giscollective.org/?page_id=492
---
[<&#8211; Part 5: Storing GIS Data for the Web](http://giscollective.org/wmsfive/)

**Making Your Own Tiles**

The bulk of web mapping for public consumption these days is done through, or at least on top of, tile services. A lot of government data still comes in untiled form, but this data is either rendered as it is served or cached (stored for quick access) by the server. Building your own tile service requires an extra step: making the tiles.

[Part 4](http://giscollective.org/wmsfour/) covered data storage formats. Whatever format you use, you want to make sure the data for your map are put together right before making tiles. The quickest and easiest way to do this is with a desktop GIS application like ArcGIS (expensive) or open-source QuantumGIS (free). If using any kind of raster imagery, the free open-source GDAL utility can turn just about any image file into a TIFF, and you can load that into your GIS software for easy georeferencing. Raster data may need to be given a Web Mercator projection to be usable by tile-making software; consult the documentation of your chosen program to find out. Most tile services use Google’s “Spherical Mercator” projection, which is coded EPSG:900913 (gOOglE—get it?) or, more officially, EPGS:3785. I recommend saving everything you need to a single workspace (folder or database).

The next step is to actually make and store the tiles. There are a few pieces of software available for making tiles that automatically generate their specialized directory structure (/directory/z/x/y.png; see [Part 2](http://giscollective.org/wmstwo/)). They are summarized below.

1. [Mapnik:](http://mapnik.org/) OSM’s choice open-source tile-rendering engine, developed by Artem Pavlenko.<sup>23</sup> It can take input data from Shapefile, PostGIS, GeoTIFF, OSM XML, Kismet, and any other formats supported by the OGR and GDAL geospatial toolsets. It relies on XML stylesheets to turn the raw data into a pretty map, and uses a Python script to generate the folder hierarchy and tiles. It can also be used with server software to render tiles on the fly from database data as requested by clients, which is how OSM employs it. It’s up to you to set up a server to serve the tiles once they’ve been generated.

2. [TileMill:](http://mapbox.com/tilemill/) Perhaps you don’t feel like investing a couple thousand bucks in a server host and a bunch of hours to set it up. MapBox’s user-friendly, fee-based tile-hosting service might be appealing. It’s not cheap, so to get you hooked they built on Mapnik’s script and released a handy piece of tile-building software called TileMill. The software allows you to import layers from CSV, Shapefile, GeoJSON, KML, GeoTIFF, SQLite, or PostGIS formats and style them using a specialized CSS library, dubbed CartoCSS. The final map can be exported to a single image PDF, PNG or SVG, or as tiles in Mapnik XML or MapBox’s MBTiles database format. There is also the option to upload tiles directly to the MapBox server—so long as you’ve purchased enough space first. They give away the first 60 MB, which isn’t much when you’re dealing with even modest-sized tile sets. My own experiment with creating a tile set bounding a mid-sized U.S. metropolitan area between zoom levels 10 and 17 (out of 22 possible) took TileMill three hours to output with a final file size of 265 MB, which MapBox would charge $49 a month to host. (For more in-depth analysis of TileMill, see [Technology Research Memo #3](http://wicoastalatlas.wordpress.com/2012/07/03/technology-research-memo-3-tilemill/)).

3. [Maperitive:](http://maperitive.net/) Formerly called Kosmos, this is a desktop rendering tool with a command-line interface primarily designed to output image files from downloaded data. It was created to draw from OSM, but one of the neat bells and whistles is a built-in function to automatically download and draw contours from NASA SRTM elevation data. Since all of the necessary layers have to be stored locally, it works best for smaller maps. The data is styled using stylesheets and can be exported to single raster or SVG images or rendered into tiles.

4. [TileDrawer:](http://tiledrawer.com/) A project of Stamen’s tile guru Michal Migurski, TileDrawer is a simplistic, entirely cloud-based utility designed strictly to render restyled OSM data into tiles hosted on an Amazon server. The website presents a three-step process, but you also need to set up and pay for an Amazon EC2 (Elastic Cloud Computing) instance to do the computing. A map interface window on the website is used to select the area of the globe to render. The next step is to enter the URL of a stylesheet to use, or select one of the four style presets on the site. The stylesheet must be in [Cascadenik](https://github.com/mapnik/Cascadenik/wiki/Cascadenik), the CSS library Migurski developed to be convertible into Mapnik XML. A window on the page then spits out the code you need to plug into the Amazon instance to run the renderer. The end result should be a hosted tile basemap. More options for serving tile data will be covered in Part 7.

[Part 7: Serving Your Map &#8211;>](http://giscollective.org/wmsseven/)

**Sources**

<sup>23</sup>Migurski, Michal. 2008. Making Sense of Mapnik. tecznotes (blog). Accessed June 29, 2012. <<http://mike.teczno.com/notes/mapnik.html>>