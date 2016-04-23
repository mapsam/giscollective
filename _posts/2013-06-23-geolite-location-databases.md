---
id: 11964
title: GeoLite Location Databases
date: 2013-06-23T20:13:35+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=11964
permalink: /geolite-location-databases/
categories:
  - Data
  - GIS
---
Sometimes you just need file of cities and their lat/long locations. Thanks to [MaxMind](http://dev.maxmind.com/geoip/legacy/geolite/) you can download an enormous **CSV** list of political entities. The city location csv file is about 22MB and can be used for creating or adding to any database. 

From Max Mind:

> The GeoLite databases are our **free** IP geolocation databases. They are updated on the first Tuesday of each month. These databases are offered in the same binary and csv formats as our subscription databases. Any code which can read the subscription databases can also read the GeoLite databases.

_Warning: there are many cities with the same name so joins will have to be carefully executed._

I uploaded the entire database to a Google Fusion Table, which is designed to look through large databases; in this case [419,433 rows of cities](https://www.google.com/fusiontables/DataSource?docid=1xSYC9KHUS6tb73PasrSfNdAb2Tgi0hESIjGRfuI).

The GeoLite City Location columns:

  * Country
  * Region
  * City
  * Postal Code
  * Latitude
  * Longitude
  * Metro Code (_if applicable_)
  * Area Code (_if applicable_)

I came across this because I was having a hard time finding a good geocoder to get the information I wanted. This is a geocoder hack-around, basically. Enjoy!