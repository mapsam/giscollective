---
id: 12144
title: How to Use Files with .e00 Extensions in ArcGIS
date: 2013-09-16T12:13:50+00:00
author: Chandler
layout: post
guid: http://giscollective.org/?p=12144
permalink: /how-to-use-files-with-e00-extensions-in-arcgis/
categories:
  - Update
---
[<img src="http://giscollective.org/wp-content/uploads/2013/09/sd.jpg" alt="sd" width="1049" height="753" class="aligncenter size-full wp-image-12145" />](http://giscollective.org/wp-content/uploads/2013/09/sd.jpg)

I was searching for some elevation data for San Diego and came upon a dataset with a .e00 extension. I downloaded it and I wasn&#8217;t able to add the file to ArcMap. It just didn&#8217;t show up in the folder as a file to select. What gives?

Files with the .e00 extension are ArcInfo Workstation interchange files, and they are used to transport coverages, INFO tables, text files, and other ArcInfo files. Adding .e00 files to ArcGIS is fairly simple, but you first need to convert them to a coverage.

To convert .e00 files to a coverage you need to use the Import from E00 script tool. The tool is located in the toolbox under **Conversion Tools > To Coverage > Import from E00**. Specify the input/output parameters and run the file.

Your .e00 will be converted to a grid file and will be able to be added to the Table of Contents in ArcGIS.