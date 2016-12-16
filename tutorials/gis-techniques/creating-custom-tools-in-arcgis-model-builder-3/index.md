---
id: 414
title: 'Creating Custom Tools in ArcGIS &#8211; Model Builder (Part 2)'
date: 2012-07-22T12:36:51+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=414
---
< [Part 1: Introducing Model Builder with ArcGIS](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder/)

**The Exercise: Analyze and Identify Potential Habitat for Homo Delphinidae**

For this exercise we will build a model to identify potential habitat for the fictional species _Homo Delphinidae_ (common name: Dolphman). We will build a model to find suitable habitat for _Homo Delphinidae_ in Dane County, Wisconsin, and then we will take that model and apply it to neighboring Iowa County, Wisconsin.

First, let’s discuss the habitat requirements for the beloved _Homo Delphinidae_:
  
1) Lives in wetland habitat
  
2) Lives in elevations below 275 meters
  
3) Lives within 500 feet of a major stream

Additionally, we want to know if there are any areas of potential habitat in existing protected areas.

What we need to put into the model (inputs) are **landcover**, **elevation**, **streams**, and **protected areas**. What we will get out of the model (outputs) is the **potential habitat** for _Homo Delphinidae_, and **areas within existing protected lands** that are potential habitat.

The Data
  
The data for this exercise are in GeoDatabase format, and can be downloaded [here](https://docs.google.com/open?id=0BwDW4THnpFhkR2lQR2xkVTByZkE). There are two databases, one for Dane County and the other for Iowa County. Both GeoDatabases contain the following layers:

  * County Boundary
  * Digital Elevation Model
  * Landcover
  * Protected Areas (Federal, State, Tribal, and Local)
  * Streams

Additionally, there is a table stored outside the GeoDatabases titled _Reclasstable_, which is a table that defines which land cover will be considered as habitat for the species. We’ll use this table to reclassify landcover into two classes: suitable (1) or unsuitable (0).

All right, enough talk about models! Let’s get to building one!

[Part 3: Let&#8217;s Build That Model!](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-2/) >