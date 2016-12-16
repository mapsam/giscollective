---
id: 973
title: Definition Query
date: 2012-09-17T16:42:12+00:00
author: Sam Matthews
layout: page
guid: http://giscollective.org/?page_id=973
---
_This short tutorial introduces the Definition Query, a query tool that allows you to specify which features of a layer to draw._

Suppose you are working on a project in ArcMap, and you’re using a large and detailed dataset, such as an entire state’s road network. Your task is to create a series of road maps at multiple scales- state wide, one for each county, and one for the 5 most populous cities in the state. The state-level map requires including interstate highways, US highways, and state highways. The county-level maps require the same as the state-level map, including county highways. The city-level maps require all roads.

To isolate each subset of the dataset you could run a ‘Select-by-Attributes’ operation, select each category of road and export to a new shapefile, and then add layer in to your map one by one.

OR you could use the definition query, which can save you time and hard drive space because you will not need to create new shapefiles to create your set of road maps.

The Definition Query is a tab in the Layer Properties window that allows you to specify which features of a layer you’d like to display. To access it, right-click on your data layer > Properties > Click the Definition Query tab.

[<img class="aligncenter" title="definition query" src="http://giscollective.org/wp-content/uploads/2012/09/definition-query-300x151.jpg" alt="" width="389" height="204" />](http://giscollective.org/wp-content/uploads/2012/09/definition-query.jpg)

You can click in the white box to write your own query, or you can click the Query Builder button to open the familiar Query Builder window.

[<img class="aligncenter" title="query builder" src="http://giscollective.org/wp-content/uploads/2012/09/query-builder-258x300.jpg" alt="" width="258" height="300" />](http://giscollective.org/wp-content/uploads/2012/09/query-builder.jpg)

To use the Query Builder with Definition Query, simply write a SQL statement to select all features that you want to show on your map in the same way that you would for any other select by attribute operation. For example, if you were working on the state-level road map you would write a SQL query to show all roads categorized as Interstate, US Highway, or State Highway. (SQL Example: &#8220;Roads&#8221; = &#8216;Interstate&#8217; OR &#8220;Roads&#8221; = &#8216;US HIGHWAY&#8217; OR &#8220;Roads&#8221; = &#8216;STATE HIGHWAY&#8217; _if my SQL is wrong, please send me a message, I&#8217;m not basing this off of any actual data!_)

After you write the query, hit OK, and back in the Layer Properties window hit Apply or Ok and you will see that only a subset of your data is shown. This can make your map-making quicker and easier than having to juggle multiple layers of data.

When you’re done making your State-level map, go back to the Definition Query and modify it for your next map to keep the workflow moving along smoothly.

Here’s an example from ESRI on using the Definition Query. They are working with a US County data layer and are only showing counties in the state they are interested in:

[<img class="aligncenter" title="example" src="http://giscollective.org/wp-content/uploads/2012/09/example-228x300.jpg" alt="" width="228" height="300" />](http://giscollective.org/wp-content/uploads/2012/09/example.jpg)

Now go give it a try with some of your own data!