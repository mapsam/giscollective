---
id: 280
title: 'Spatial Data Conversion &#8211; Using the Command Line'
date: 2012-07-17T17:26:33+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=280
---
By Chandler Sterling

So you&#8217;ve got some spatial vector data and need it in a different format. Say you have a shapefile and are making a web-map, so you want it in GeoJSON or KML format. Your computer is getting kind of old, booting up ArcMap can take awhile, and you don&#8217;t actually need to use the software, you just need to convert the data. Or you&#8217;re a command line junkie and prefer to do things this way (if you are, feel free to skip ahead to the code syntax).

Fortunately, there is a quick and easy way to convert vector data using a neat tool called OGR2OGR (pronounced [ogre-to-ogre](http://puzzles-games.eu/data/media/3/Shrek-the-Ogre.jpg)), packaged within FW Tools. FW Tools is an Open Source Binary Kit for Windows and Linux. FW Tools includes a set of cool geospatial tools, such as OpenEV, GDAL (Geospatial Data Abstraction Library), MapServer, PROJ.4, and OGDI. 

Download and install FW Tools [here](http://fwtools.maptools.org/)

Once you have FW Tools installed, you are only a few short steps away from transforming your spatial data into a new format!

**The FW Tools Shell**
  
Open the FW Tools shell by navigating to the directory it was installed to. In Windows, this may be Start > Programs > FW Tools

A window (or shell) will open, and will look quite similar to the windows command shell. 

<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/ogr2ogr/winCmdShell.png" alt="FW Tools Shell" /></a><em>FW Tools Shell</em>
</center>


  


<center>
  <img src="https://s3.amazonaws.com/gisc/wordpressImages/ogr2ogr/winCmdShell.png" alt="Windows Command Shell" /><em>Windows Command Shell</em>
</center>

Fortunately, navigating your computer&#8217;s environment is similar to most command line terminals. For instance, to change directories, simply type cd for &#8216;change directory&#8217; and then specify the path.

For example:

[code]cd C:\YOUR\FOLDERS\NAMES\HERE[/code]

So with the FW Tools shell open, navigate to the directory that contains the files you want to convert. Converting your files into another format takes only one command once you are in the directory with the files. The syntax for the OGR2OGR command is:

[code]
  
ogr2ogr -f &#8220;FILE_TYPE&#8221; fileName1.newExtension fileName1.oldExtension
  
[/code]

If that doesn&#8217;t make a whole lot of sense, let me illustrate with an example, and then we&#8217;ll walk through each section of the command. For this example, we&#8217;ll convert a shapefile to a KML:

[code]
  
ogr2ogr -f &#8220;KML&#8221; amazonRivers.kml amazonRivers.shp
  
[/code]

You&#8217;ll see that we first call ogr2ogr, and pass the flag &#8216;-f&#8217; which indicates filetype. For a comprehensive list of the many options supported by OGR2OGR, type:

[code]
  
ogr2ogr &#8211;help
  
[/code]

After the filetype -f flag, we specify the format we wish to convert our file into. In the example case, we wanted the shapefile turned into a KML. For a list of OGR supported vector formats, check out this [handy table](http://www.gdal.org/ogr/ogr_formats.html). 

Following the file type specification, you specify the name of the new file. It does not have to be the same as the original file, but it should have the appropriate extension included (e.g., .kml, .shp, .json, etc). Then type the name of the old file, including the old extension. Hit enter. Your file should now be converted, and if you check the directory the new file should be in there! 

There you have it! File conversion in only a few short steps. To sum it all up, here are the steps again:

  1. Open FW Tools Shell
  2. Type the command: 
    [code]
  
    ogr2ogr -f &#8220;file type&#8221; newfile oldfile
  
    [/code] </li> 
    
      * Make awesome maps with your new files!</ol> 
    
    **Command Line Tips**
    
      * You can view all files and subdirectories by typing &#8216;dir&#8217; for directory
      * The shell will autofill what you type based on items in the current directory. For instance, if there is a file titled &#8216;ReadMe.txt&#8217; in your current directory, you can type the first few letters, and then hit the tab button and the shell will auto-complete the filename for you. This is a quick trick that can increase efficiency in navigating your computer&#8217;s environment through the command line!
  
        Try it out when performing OGR2OGR commands, those pesky GIS filenames can get tediously long to type!
      * Typing &#8216;cd /&#8217; brings you to back to the [Root directory](http://en.wikipedia.org/wiki/Root_directory). The root directory is the first directory in the computer&#8217;s hierarchy. </ul>