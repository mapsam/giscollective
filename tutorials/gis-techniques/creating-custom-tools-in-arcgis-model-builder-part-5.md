---
id: 446
title: Creating Custom Tools in ArcGIS – Model Builder (Part 5)
date: 2012-07-22T13:09:00+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=446
---
[< Part 4: Adding Data](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-4/)

**_Criteria 2:_ _Elevations Under 275 meters_**
  
Now that we have satisfied our first criteria (that our species’ ideal habitat is wetlands), let’s move on to our second criteria: Homo Delphinidae lives in habitats that are under 275 meters in elevation.

Add the **DaneDem** (digital elevation model) to the **Model Builder** window. Rename the layer to **Elevation** (right-click > rename). If you view the attribute table, the **Value** field is the field with elevation data, recorded in meters. Again, we’re looking for areas _under 275 meters_. To find these areas, we will use the **CON** tool.

The CON tool can be found in the ArcToolbox under **Spatial Analyst Tools > Conditional > CON**. Click-and-drag the CON tool into the Model Builder window. **Double-click** the tool, choose **DaneDem** as the input, rename the output to **GoodElevation.**

In the **Expression** field, we need to create a [SQL](http://en.wikipedia.org/wiki/SQL) expression to select the values that are less than 275 meters. Write:

<center>
  “VALUE” < 275
</center>in the Expression field. In the 

**Input true raster or constant value** field, set the value to 1. For the **Input false raster or constant value** field, set the value to 0. This is telling the software: “If the value in **danedem** is less than 275, set the output value to 1, otherwise, set the value to 0.”
  
<img class="aligncenter" src="https://lh6.googleusercontent.com/_lbZWyb8q5f-xJ8bZi2fouUtFTaXQzlSfR3BY25lTF2LuAA9oX8QWge-2j4IRfzb1mmmYH6kr3yoTRlYYQn0VIPle28VffZoleqR_zcj1uUBFokOus0" alt="" width="590px;" height="306px;" />
  
Click **OK.** You will notice two new blue ovals, the **input true** and **input false raster**.
  
<img class="aligncenter" src="https://lh6.googleusercontent.com/GJEyvcWjpEjvcZK0yQLKrXDuQT4uTchcIWmkrlrKgafr29X-rzmiZNXSQMCRF7ALx4NP99MbsvbMjwntReS6mwzcNzYKmZKNcmgVM8M3RhE2mrxixzs" alt="" width="424px;" height="344px;" />

<center>
  <em>I renamed the input true/false ovals to True value and False Value to clean up the model a bit</em>
</center>

_Heads Up!_ You may need to resize the Model Builder window to see all the processes of the model at once. You can zoom-in/out by holding the **Control key** and scrolling the mouse wheel up/down.

You can also move the items in the model around the window by selecting the **black arrow** tool from the toolbar, and clicking-and-dragging the items. What you’ll start to notice is the model essentially becomes a flow-chart of operations.

Before we run the model again, **right-click** on the **GoodElevation** output layer, and select **Add to Display**. Then click the **Run** button. (If the Add to Display does not work for you, just add the data like you would any other layer. For some reason, on writing this tutorial, the Add to Display button does not actually add the data to the Table of Contents) Note the drop shadows on the Con tool and the Good Elevation output shapes.

[Part 6: Criteria 3: Habitat Within 500 ft of a Stream >](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-6/)