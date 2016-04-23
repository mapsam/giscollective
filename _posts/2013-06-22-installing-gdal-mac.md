---
id: 11958
title: Installing GDAL (mac)
date: 2013-06-22T10:34:02+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=11958
permalink: /installing-gdal-mac/
categories:
  - Update
---
GDAL is a powerful library, but for many it is the first step into an open-source GIS world, which tends to lack GUIs and becomes an introduction to the command line or terminal. To get GDAL installed on your mac, grab the most recent release from [Kyngchaos](http://www.kyngchaos.com/software:frameworks) (currently at version 1.10). If you haven&#8217;t installed any of the necessary packages, I recommend installing the **GDAL 1.xx Complete** package, which will include all of the necessary python frameworks.

Once you have that downloaded, go through the normal install process as if it were another application. Once installed, there is one _very important_ step in order to get it working on your command line. I&#8217;m grabbing this directly from [Mapbox](http://www.mapbox.com/tilemill/docs/guides/gdal/), but it&#8217;s such a necessary step that needs repeating. Run the following command in your terminal:

<pre>echo 'export PATH=/Library/Frameworks/GDAL.frame
work/Programs:$PATH' >> ~/.bash_profile
source ~/.bash_profile
</pre>

This will set your path for the GDAL framework and will make the &#8216;gdal&#8217; and &#8216;ogr&#8217; commands global. That&#8217;s it! Check out some of Chandler&#8217;s [tips on using GDAL/OGR](http://giscollective.org/tutorials/gis-techniques/spatial-data-conversion-using-python/), or even the [python examples](http://giscollective.org/open-source-programming-with-ogr-gdals-vector-library/) he put together to run spatial processes.