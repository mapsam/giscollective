---
id: 444
title: Creating Custom Tools in ArcGIS – Model Builder (Part 4)
date: 2012-07-22T13:05:19+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=444
---
[< Part 3: Let&#8217;s Build That Model!](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-2/)

**Adding Data**
  
We are now ready to begin building our model. As mentioned earlier, we’ll use the Dane County data to start.

Add the **DaneLandCover, DaneDEM, DaneProtectedAreas,** and **DaneStreams** from the Dane County GeoDatabase into ArcMap. With the layers in the Table of Contents, you can simply drag-and-drop them directly into the model. Similarly, you can drag-and-drop tools from the toolbox into the model as well.

Before we begin dragging data and tools into our model, let’s revisit the criteria for _Homo Delphinae_:

1) Lives in wetland habitat
  
2) Lives in elevations below 275 meters
  
3) Lives within 500 feet of a major stream

_**Criteria 1 &#8211; Wetland Habitat**_
  
In order to find wetland habitat we will use the **DaneLandcover** layer. Open the layer’s attribute table and notice the various wetland types. This is where that reclass table comes in handy. We’ll reclassify the table values to be either “1” for suitable landcover, or “0” for unsuitable landcover.

**Drag and drop** the landcover layer into the Model Builder window. You’ll notice that the layer is displayed as a blue oval; all layers/data are visualized as blue ovals in model builder. <img class="aligncenter" src="https://lh6.googleusercontent.com/k5mTpZM_FRMTo1XWcuBhWJlGUhefRcESoomNG8jB88M-ILyWA484exQPuYiWgh-qlQVr9NKYexyVD7J_qkkm5q3EJWGFwabHs6Le4RVR56IFI2tTats" alt="" width="260px;" height="152px;" />
  
Seeing as we’ll be using this model for other counties in addition to Dane County, let’s rename the layer in the model to **Landcover**. To rename the layer, **right-click** on the oval and select rename. (NOTE: You are not changing the name of the actual layer, only its representation in the model).

Additionally, you can change the size of the oval by first click it, and then clicking-and-dragging one of the blue boxes on the outside of the oval-shape. You can also move the layer around the window as you see fit.

_Extracting Wetland Habitat Data_
  
Seeing as the landcover layer is a raster layer, we cannot simply perform a select by attribute query to extract the wetland habitat like we could if it were a vector layer. We will instead need to employ the **Spatial Analyst** toolbox. This toolbox has many useful tools for working with raster data.

First, let’s bring in the **Reclass Table** mentioned earlier. Go to **Add Data** and bring it into the Table of Contents (it’s in the same directory as the two GeoDatabases). Fortunately, this table exists outside both GeoDatabases and can be used by any county in the State of Wisconsin. Go ahead and open the table and take a look at its structure.

You’ll note that the tables a Boolean value (0 or 1) to each possible habitat type in Wisconsin in the column named **OUT**. A value of 0 indicates unsuitable habitat for our species, a value of 1 indicates suitable habitat.

Now, let’s use that Reclass Table! In the ArcToolbox, navigate to **Spatial Analyst Tools > Reclass > Reclassify** and click-and-drag the **Reclassify** tool into the Model Builder window.

You’ll see two new objects in the window: a rectangle titled “Reclassify” (with a hammer icon, indicating it is a tool), and another oval, titled “Output Raster.” As mentioned earlier, all data layers are visualized as ovals. When a tool is added to the model, the data output from the tool’s operation is also added to the model.
  
<img class="aligncenter" src="https://lh5.googleusercontent.com/TK9A056_3yETdDJ0hBFd6mHYg50RlvjrVCZU66zFguAJSYEg8t1pU7_0b3-4B4uPA-0ZGrtOmULbMSTQYJ4Jmv8SzoWOpMbg9ledOyrM1-O18iWgcRc" alt="" width="504px;" height="136px;" />

You’ll also notice that the two new objects are only outlines; they have no fill. This indicates that the tool is not yet connected with the Landcover data layer.

_Connecting a Tool to Data_
  
There are a few ways in which you can connect a tool to your data.
  
1) You can **double-click** on the **Reclassify** tool, which opens the familiar tool interface window, and select the **DaneLandcover** layer (Layers with a recycle icon are layers that are currently in the layer).

<p style="text-align: center;" dir="ltr">
  OR
</p>

<p style="text-align: left;">
  2) You can use the connector tool to drag a connection from the <strong>Landcover</strong> layer to the <strong>Reclassify Tool</strong>. Simply select the connector tool and click-and-drag from the landcover layer to the tool to complete the connection. Select<strong> Input Raster</strong> (Arc 10) from the menu that pops up after you release the mouse, and the shape outlines will fill in. To get to the tool’s dialogue window to set the parameters,<strong> double-click</strong> on the tool.
</p>

<img class="aligncenter" src="https://lh6.googleusercontent.com/GS2Jhm_rHODEtZX6AFinsNHfb_M_1FraULl548PzPqKrY0WIFfx8kV0KJZD2ZH4l5HxVk2aVs2fN91NECUlWLyjn8fcIGcwTGS3d9mFw15hcn89X4zw" alt="" width="25px;" height="28px;" />__

<center>
  <em>Connector Tool</em>
</center>

_Reclassify Parameters_
  
In the Reclassify dialogue box, make sure that the Input raster is the **Landcover** layer. Load the **Reclass table** by clicking **Load&#8230;** and navigating to the directory that stores the table. Note how the old values will be changed after the **Reclassify** operation (Hint: Only old values ranging from 211-234 will be considered suitable habitat).

**Rename** the **output raster** to **“GoodType”**, make sure you’re saving it in the **Dane County** GeoDatabase, click **OK.**

If you didn’t use the connector tool, the shapes should now be colored in the model. All tools will be yellow rectangles, all input data layers are blue ovals, and all output data layers will be green ovals. Keep this color scheme in mind throughout the remaining exercise.

_Running the Model &#8211; The First Run_
  
All right! Now that we have a step of our model built, let’s run it and take a look at the output to make sure our reclass table did its job. To run your model, **right-click** on the **output data layer (green oval)** and choose **Add to Display.**

The Add to Display option can be toggled on or off, and what it does is adds the new output layer to the Table of Contents. So with that option toggled on, run the model by clicking the run tool. It’s the button that looks like a conventional “Play” button on a VCR (or Blue Ray player, for those of the digital age).

When the Run button is clicked, a new dialog box opens and shows the operation working. Click **close** when the operation finishes, and in the model builder window you’ll see a **drop shadow** has been applied to the tool and the output. This indicates that the operation ran successfully.

_Heads Up!_ If the layer did not get added to the Table of Contents, simply click **Add Data > Navigate to the Dane County GeoDatabase > Add GoodType.**

[Part 5: Criteria 2: Elevations Under 275 Meters >](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-5/)