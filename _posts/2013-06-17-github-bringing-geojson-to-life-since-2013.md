---
id: 11898
title: 'GitHub: Bringing GeoJSON To Life Since 2013'
date: 2013-06-17T11:31:07+00:00
author: Lyzi Diamond
layout: post
guid: http://giscollective.org/?p=11898
permalink: /github-bringing-geojson-to-life-since-2013/
categories:
  - Data
  - Theory
  - Web Mapping
---
<p dir="ltr" style="text-align: center;">
  <a href="http://giscollective.org/wp-content/uploads/2013/06/githubgeojson1.png"><img class="aligncenter  wp-image-11901" alt="GeoJSON now renders on GitHub!" src="http://giscollective.org/wp-content/uploads/2013/06/githubgeojson1.png" width="734" height="405" /></a>
</p>

<p dir="ltr">
  Last week, the code repository heroes over at <a href="http://github.com">GitHub</a> made an awesome announcement: <a href="https://github.com/blog/1528-there-s-a-map-for-that">Any .geojson files living in GitHub repos will now be rendered on a Leaflet-driven, OSM tile-backed map right inside of GitHub</a>, with tooltips showing the data properties to boot! This is a truly exciting moment for all geonerds who code, developers who use geodata, and everyone in between.
</p>

“Hey, wait a minute,” you may be saying. “What is GitHub again? And [GeoJSON](http://www.geojson.org/)&#8230; I think I’ve heard of that, but what is it for?” Do not fret! We at GISC know that the field is moving quickly, and we are happy to provide guidance and direction for your geospatial journey.

### Git and GitHub

<img class="aligncenter" alt="Git and GitHub" src="http://www.palermo.edu/Archivos_content/ingenieria/top/130712_git_github_topdenota1.jpg" width="539" height="184" />

<p dir="ltr">
  Before learning about GitHub, we first have to understand <a href="http://git-scm.com">git</a>. Git is a tool that allows multiple people to work on the same files at the same time without overwriting each other’s changes. This general concept is called <em>version control</em>, and git is a <em>version control system</em>. There are several other version control systems out there, but git is popular because it does its job more efficiently than many (if not all) of the others.
</p>

<p dir="ltr">
  In order for multiple people to work on a project, the data has to live in a place where multiple people can access it, right? GitHub is that place: the site houses thousands and thousands of projects, in individual workspaces called <em>repositories</em>, or <em>repos</em>, that multiple people can access, copy, edit, and update using the tools available via git. These repositories also have a tracking element; when someone makes a change to a project, or a <em>commit</em>, information is stored about the user, the time, the exact changes that were made (all the way down to the individual line inside the file!), and a unique ID that allows the project owner to restore back to that particular moment. It’s pretty effing cool.
</p>

<p dir="ltr">
  Because git is so great, and GitHub is so popular, people have been using it for all kinds of projects, coding and otherwise. I have seen professors put lectures and lecture notes on GitHub, several of my friends use it as a place to work on resumes and terminal projects&#8230; you can basically use it for anything. Shoot, even the code for my website lives on GitHub. So it follows that with the advent of mapping and geospatial analysis on the web, there is a lot of geodata housed on GitHub.
</p>

<h3 dir="ltr">
  GeoJSON
</h3>

[<img class="aligncenter size-full wp-image-11902" alt="GeoJSON" src="http://giscollective.org/wp-content/uploads/2013/06/geojson.png" width="541" height="271" />](http://giscollective.org/wp-content/uploads/2013/06/geojson.png)

One of the more common formats used for geospatial data in web mapping applications is called _GeoJSON_. GeoJSON was born out of a format called _[JSON](http://json.org)_, which stands for _JavaScript Object Notation_. JSON is like a table turned on its side; each row gets its own section, and inside of that section is a series of properties and values unique to that row. For example, a table of Presidents of the United States might look something like this:

[<img class="aligncenter size-full wp-image-11903" alt="US Presidents" src="http://giscollective.org/wp-content/uploads/2013/06/presidents.png" width="649" height="137" />](http://giscollective.org/wp-content/uploads/2013/06/presidents.png)

<p dir="ltr">
  In JSON, the table might look like this:
</p>

<pre>{
   “presidents” : {
       “name” : “Barack Obama”,
       “hometown” : “Honolulu, HI”,
       “number” : “44”,
       “year elected” : “2008”,
       “terms served” : “2”,
       “child1” : {
           “name” : “Malia”,
           “born” : “1998”
       },
       “child2” : {
           “name” : “Sasha”,
           “born” : “2001”
       }
   },
   {
       “name” : “George W. Bush”,
       “hometown” : “New Haven, CT”,
       “number” : “43”,
       “year elected” : “2000”,
       “terms served” : “2”,
       “child1” : {
           “name” : “Jenna”,
           “born” : “1981”
       },
       “child2” : {
           “name” : “Barbara”,
           “born” : “1981”
      }
   }
}</pre>

<p dir="ltr">
  GeoJSON takes this format and adds geometry, allowing mapping engines and libraries to parse the data and place these objects in space using coordinates, as well as properties, which can be thought of like the fields and values in an attribute table. GeoJSON allows for points, lines, polygons, and a few other data types, but it’s all formatted in much the same way as the JSON example, above.
</p>

Many if not all of the open source mapping libraries for JavaScript ([Leaflet](http://leafletjs.com) and [MapBox](http://mapbox.com) most notably) support GeoJSON and allow GeoJSON layers to be added to their maps. [QGIS](http://qgis.org), the open source desktop mapping application, also allows the user to view and export data in the GeoJSON format. This has made it extremely popular as a geodata format, which is why it shows up frequently on GitHub.

### In Summary

<p dir="ltr">
  So now that we know what GitHub is used for and how GeoJSON works, we can clearly see why GitHub’s announcement last week was such a big deal: If you click on any .geojson file in a repo on github.com, the data will be rendered and displayed on a map. No more scrolling through text and trying to figure out where [45.528402,-122.65762] might be, because all of the data is displayed spatially for easy perusal!
</p>

With limited time and limited space, I can only say so much, so this wasn’t a thorough walkthrough of git, GitHub, or GeoJSON. I didn’t even touch Leaflet or [OpenStreetMap](http://openstreetmap.org) — posts going into all of these things in depth will be on the blog in the coming weeks. For now, head on over to GitHub, find some GeoJSON files, check out the sweet maps, and maybe try making your own repo! And please stay tuned for more updates — by the end of the summer, you’re going to be using git like a pro!