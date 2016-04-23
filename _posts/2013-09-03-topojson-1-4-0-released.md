---
id: 12141
title: TopoJSON 1.4.0 Released!
date: 2013-09-03T12:25:31+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=12141
permalink: /topojson-1-4-0-released/
categories:
  - Data
  - Web Mapping
---
Mike Bostock released [TopoJSON 1.4.0](https://github.com/mbostock/topojson/releases/tag/v1.4.0) today, which revisits the algorithm used to simplify topological data. This is an exciting release, as it really aims to widen the precision inputs when using the command line references to look at points that aren&#8217;t **exact** but assuming they are in the same location. Described by Bostock:

> An issue of particular importance to topology inference is messy inputs. For example, if you have two points [-122.416712304917, 37.783305712306] and [-122.416712304916, 37.783305712306], then in regards to the topology they are as distinct as San Francisco and New York. The TopoJSON reference implementation eliminates many of these errors by quantizing inputs, rounding them to lower precision.

He recently put together a great [visual explanation on how topojson works](http://bost.ocks.org/mike/topology/) from a practical and geographic perspective. It&#8217;s a great article explaining the four-step process. Hats off to an exciting release!