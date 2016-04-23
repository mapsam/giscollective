---
id: 119
title: Bringing LiDAR Data into ArcGIS
date: 2012-07-16T23:45:48+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=119
---
_In this tutorial, Danielle Lee explains how to bring LiDAR data into ArcGIS. It requires the use of the 3D Analyst extension with ArcGIS, so hopefully you&#8217;ve got it!_

_To follow along, grab the data from http://lidar.swc.nd.gov/_
  
 _The data Danielle used is called 13908001.LAS, so feel free to grab that, or get any other LiDAR data!_
  
 _This tutorial was prepared for Arc version 9.3.1 but works with Arc v10._

1. Turn on the 3D Analyst Extension

2. Determine the Average Point Spacing of your LiDAR data by using the 3D Analyst Tools>Conversion>From File>Point File Information tool if unknown. The point spacing will be in the attribute table of the new Shapefile created.

a. In ArcMap ArcToolbox, browse to 3D Analyst Tools>Conversion>From File> LAS to Multipoint. Choose the LAS files for your area of interest and point spacing, and save as LAS\_to\_Multipoint.shp.

b. If your LAS data is in ASCII format, use the ASCII 3D to Feature tool.

3. Open ArcCatalog and browse to the folder that contains the new multipoint feature LAS\_to\_Multipoint.shp. Assign a coordinate system to the LAS\_to\_Multipoint if there is not one already assigned. (in Arc10 you can find the projection in: projectect coordinate systems > state plane > NAD 1983 > NAD 1983 StatePlane North Dakota S FIPS 3302 (US Feet))

&nbsp;

4. In the same folder that contains LAS\_to\_Multipoint, go to File>New>File Geodatabase and name it LiDAR:

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar4.jpg" alt="" />
</center>5. Right click on the new LiDAR.gdb and go to New>Feature Dataset and name it LiDAR_Files

&nbsp;

6. Right click on LiDAR\_Files Feature Dataset and go to Import>Feature class (single), importing LAS\_to_Multipoint.shp. You may also import breaklines, clipping boundaries, and any other files that cover the project area. Click through the wizard to completion.

&nbsp;

7. Right click on the LiDAR_Files Feature Dataset and go to New>Terrain

&nbsp;

8. This is the Terrain Wizard. See http://webhelp.esri.com/arcgisdesktop/9.3/index.cfm?id=3413&pid=3410&topicname=Building\_a\_terrain\_dataset\_with\_the\_terrain\_wizard for detailed information. Name the terrain Terrain and select all the LAS\_to_Multipoint and breaklines.

a. The pyramid levels are simply for display purposes, so only create one pyramid level (this will drastically cut down on processing time). Click Calculate Pyramid Properties to create pyramid (ensure that you have at least 1). Click Next, view the summary, and click Finish.

b. When the Wizard is complete, it will take a while to create the actual terrain. Click Yes to build now.

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar8.jpg" alt="" />
</center>9. When your 

_Terrain_ is created, bring it into ArcMap to check that it looks reasonable.

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar9.jpg" alt="" />
</center>10. If everything looks good, go back to Catalog, convert to Raster or to TIN by using 3D Analyst Tools> Conversion> From Terrain> Terrain to Raster/TIN.

_Note: When working with large terrains, you may want to click Environments>Terrain and limit memory use for terrain analysis._

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar10.jpg" alt="" />
</center>

**Supplementary Info: Importing ASCI LIDAR Break Lines**

If break lines are in this ASCII text format (if they are not in this format, the text file must first be modified):

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar11.jpg" alt="" />
</center>Use the 3-D Analyst “ASCII 3D to Feature Class” conversion tool:

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar12.jpg" alt="" />
</center>

**Options:** Generate & Polyline

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/lidar13.jpg" alt="" />
</center>