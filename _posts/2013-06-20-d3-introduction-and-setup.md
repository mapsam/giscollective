---
id: 11920
title: 'd3: Introduction and Setup'
date: 2013-06-20T19:18:48+00:00
author: Sam Matthews
layout: post
guid: http://giscollective.org/?p=11920
permalink: /d3-introduction-and-setup/
categories:
  - Data
  - Web Mapping
---
**d3** (Data Driven Documents) has become one of the more popular visualization libraries for the web, allowing the developer to create responsive and interactive graphics with a unique set of data. For a javascript visualization library, it allows for incredible amounts of manipulation and customization, but also has a gigantic user-group that is continually creating examples and other branch tools for making it easier to use.

The incorporation of geographic data into d3&#8217;s standard library is the beginning of a bridge between the web and traditional cartography, finding a common medium for aesthetics and true spatial representation to co-exist (i.e. projections beyond the standard Web Mercator and SVG scalability). To me, it&#8217;s a window into the future of cartography. But how do you use it?

Beyond the introduction tutorials it is easy to get lost in the code of brilliant developers. It&#8217;s not too long before you realize you have no idea how your visualization actually works. At the most basic, it&#8217;s tough to understand how d3 actually interacts with all of your data; how your _data_ actually _drives_ the _document_. So, let&#8217;s get started. 

## How to set up your workstation to use d3

First, get a cup of coffee. There&#8217;s no reason not to.

### The tools | _What I use_

  * Text Editor | _Sublime Text_
  * Browser | _Chrome, FF, IE*_
  * D3 Source | _[d3js.org](http://d3js.org/)_
  * Local Server Environment | _[MAMP](http://www.mamp.info/en/index.html) (for mac), [WAMP](http://www.wampserver.com/en/) (for PC)_
  * Coffee | _FTO_

_*d3 is not supported on IE8 or below. Why? Because they answer to no one. Also, d3 is new and progressive, which is not the case in many outdated IE8 platforms so they aim for a future of good web standards._

The list above is d3 at its most basic. It doesn&#8217;t even include data! Of course, you&#8217;ll bring in your own dataset to take advantage of the dynamic qualities of the library, but that doesn&#8217;t make it a requirement. Not really sure what a Local Server Environment is? [Set up MAMP on your Mac](http://giscollective.org/local-server-environment-setup/). In short, it will allow d3 to grab specific files or datasets from your directories. Otherwise you&#8217;ll run into [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) issues, which can be a headache. This may not come up in a basic setup, but once you start drawing data from different files, things can get complex.

So now you know the tools, but where to put all the files? Below is a common directory file structure:
  
[<img src="http://giscollective.org/wp-content/uploads/2013/06/Screen-shot-2013-06-20-at-4.20.45-PM.png" alt="d3 file structure" width="301" height="118" class="alignnone size-full wp-image-11930" />](http://giscollective.org/wp-content/uploads/2013/06/Screen-shot-2013-06-20-at-4.20.45-PM.png)

Quite basic, but leaves room for expansion. From here, you&#8217;ll want to set up your index file with the following:

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
  &lt;meta charset="utf-8"&gt;
  &lt;title&gt;D3 Setup&lt;/title&gt;
  &lt;link rel="stylesheet" type="text/css" href="css/style.css"/&gt;
  &lt;script type="text/javascript" src="js/d3.v3.js"&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;script type="text/javascript"&gt;
    <span>//d3 code here</span>
  &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

You can view your index.html in your browser through your localhost – typically something along the lines of localhost:8888/sites/your_project – and begin taking advantage of d3&#8217;s powerful functions. Next I&#8217;ll be jumping into d3.geo, the geographic library built within d3 for cartography productions.