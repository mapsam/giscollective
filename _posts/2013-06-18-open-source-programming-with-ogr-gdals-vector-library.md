---
id: 11909
title: 'Open Source Programming with OGR (GDAL&#8217;s vector library)'
date: 2013-06-18T13:47:59+00:00
author: Chandler
layout: post
guid: http://giscollective.org/?p=11909
permalink: /open-source-programming-with-ogr-gdals-vector-library/
categories:
  - Data
  - 'Tips &amp; Tricks'
---
I decided it could be beneficial to the community to provide the geoprocessing scripts I created using GDAL&#8217;s vector library, OGR, after a member of the [GIS and Geography](http://www.linkedin.com/groups/GIS-Geography-3887350?trk=myg_ugrp_ovr) group on LinkedIn posted a question about geoprocessing with GDAL. GDAL/OGR can be a challenge to learn because of the scarcity of online examples, so I hope I am able to provide a little bit more to help those beginning to learn the ins and outs of GDAL and open source GIS programming.

I uploaded the example scripts to a [I decided it could be beneficial to the community to provide the geoprocessing scripts I created using GDAL&#8217;s vector library, OGR, after a member of the [GIS and Geography](http://www.linkedin.com/groups/GIS-Geography-3887350?trk=myg_ugrp_ovr) group on LinkedIn posted a question about geoprocessing with GDAL. GDAL/OGR can be a challenge to learn because of the scarcity of online examples, so I hope I am able to provide a little bit more to help those beginning to learn the ins and outs of GDAL and open source GIS programming.

I uploaded the example scripts to a](https://github.com/csterling/ogrTools) for everyone to access. I hope they can help provide insight into how one could best utilize the geoprocessing tools within GDAL.

The scripts in the repository show how to perform the following geoprocessing tasks with GDAL/OGR:

<ul id="docs-internal-guid-52f54ec4-589b-fe7b-59ac-5d2e7f094fd3">
  <ul>
    <li dir="ltr">
      <p dir="ltr">
        Append &#8211; Adds one geometry or set of geometries to another.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Buffer &#8211; Creates a user-specified buffer (polygon) around the input geometry. Erosion can be achieved by passing a negative value to the buffer parameter.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Centroid &#8211; Returns or generates a point of an object’s geometric centroid/center.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Contains &#8211; Tests whether one geometry contains another.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Crosses &#8211; Tests whether one geometry crosses another.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Disjoint &#8211; Tests for disjointness between two geometries.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Distance &#8211; Finds and displays the shortest distance between two geometries.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Difference &#8211; Removes a section of a polygon where two geometries overlap.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Equals &#8211; Tests whether two geometries are equal or not.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Get Envelope &#8211; Returns the bounding envelope for a specific geometry
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Get Fields &#8211; Returns all fields within a specific file.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Get Layer Extent &#8211; Returns the extent of the entire layer
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Get Unique Values &#8211; Returns a list of all unique values within a specified field
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Intersect &#8211; Tests for intersection between two geometries.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Intersection &#8211; Computes a geometric intersection of the input features. Features or portions of features which overlap in all layers and/or feature classes are written to the output feature class.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Simplify &#8211; Creates a simplified representation of the geometric object. All points in the simplified object will be within the tolerance distance (which is set by the user) of the original geometry.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Symmetric Difference &#8211; Removes a section of a polygon where two geometries overlap.
      </p>
    </li>
    
    <li dir="ltr">
      <p dir="ltr">
        Union &#8211; Returns a representation of the union of the given geometric objects.
      </p>
    </li>
    
    <li dir="ltr">
      Within &#8211; Tests whether one geometry is within another.
    </li>
  </ul>
</ul>