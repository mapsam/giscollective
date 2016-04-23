---
id: 12200
title: Geocoding in the browser
date: 2015-02-17T10:53:13+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=12200
permalink: /geocoding-in-the-browser/
categories:
  - GIS
  - Web Mapping
---
Lately I&#8217;ve been working on projects that require quick geocoding in the browser based on a user search. Here I want to share two specific geocoding services that have worked well for me, have been cost effective (free), and return seemingly solid results: **Census** and **Mapbox**. Both services allow for one to structure an HTTP query with an address and the response comes in JSON format with the appropriate latitude and longitude information.

## The Census Geocoder

The [Census Geocoder](http://geocoding.geo.census.gov/geocoder/) has a pretty simple [REST API](http://geocoding.geo.census.gov/geocoder/Geocoding_Services_API.pdf) that is accessible without the need of a special API key or token, which is awesome. There are two valid ways to structure the query:

  1. **One Line Address**: allows you to send a single string into the query
  2. **Address parameters**: build the parameters for each part of the address

We&#8217;ll focus on the One Line Address for simplicity&#8217;s sake. The HTTP endpoint is as follows:

`http://geocoding.geo.census.gov/geocoder/locations/onelineaddress?...`

The necessary parameters are as follows:

  * `address` &#8211; the address string you are looking for
  * `benchmark` &#8211; A numerical ID or name that references what version of the locator should be searched. Here&#8217;s [a list of benchmarks](http://geocoding.geo.census.gov/geocoder/benchmarks). 
  * `format` &#8211; format of the response. Typically used with `json` or `jsonp`

An example call for the location of The Old Fashioned bar in Madison, WI with the address **23 North Pinkney St. Madison WI**:

<http://geocoding.geo.census.gov/geocoder/locations/onelineaddress?address=23+N+Pinckney+St+Madison+WI&benchmark=4&format=json>

## Mapbox Geocoder

Mapbox offers a great [geocoding service](https://www.mapbox.com/developers/api/geocoding/) that is very much like the Census, allowing for HTTP requests. They require an API key but beyond that you can make many calls to their API without going over the limit. One thing that draws me to the Mapbox version is the ability to make multiple queries for different addresses in the same request using their [batch geocoding service](https://www.mapbox.com/developers/api/geocoding/#batch) (allowing up to 50 per request). Here&#8217;s an example searching for three different zip codes:

<http://api.tiles.mapbox.com/v4/geocode/mapbox.places-permanent/20001;20009;22209.json?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6IlhHVkZmaW8ifQ.hAMX5hSW-QnTeRCMAy9A8Q>

The response is an array of objects with the geometry information for the respective features.