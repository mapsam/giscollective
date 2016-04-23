---
id: 450
title: Creating Custom Tools in ArcGIS – Model Builder (Part 6)
date: 2012-07-22T13:13:51+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=450
---
[< Part 5: Criteria 2: Elevations Under 275 Meters](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-5/)

**Criteria 3: Habitat within 500 ft of a stream**
  
All right! Two criteria down! We are well on the way to completing our model, and identifying suitable habitat for _Homo Delphinidae_. Now let’s identify areas in the county that are within 500 feet of a stream.

Drag the **streams** layers into the Model Builder window and rename it to **streams**. To find areas that are 500 feet from a stream we will perform a simple **buffer** operation. Add the tool to the model from the ArcToolbox: **Analysis Tools > Proximity > Buffer**.

**Double-click** the buffer tool. Populate the tool’s parameters as follows:

  * Input Features: streams (with the recycle icon next to it)
  * Output Feature Class: StreamBuffer
  * Distance: 500 Feet
  * Side Type: Full (default value)
  * End Type: Round (default value)
  * Dissolve Type: ALL

The **Dissolve Type** specifies what type of feature output the buffer operation will result in. We selected ALL, because we want all the buffered features dissolved together into one single feature, and all the overlap to be removed. Click **OK**, check Add to Display on the streamBuffer output, and **run** the model. (Add the layer to the Table of Contents and check it out!)
  
<img class="aligncenter" src="https://lh3.googleusercontent.com/MBXgGhVv3GpTLjxOg1cwqIiC_sWk5Sm1EyOSvtTF3wbbxZCk3F82pz6Twt-5CtZeSyQA6f6e-CN9_xdlmsAFyfrVA0EbVjlqGtwfGFzxIQX7X5_jFk0" alt="" width="486px;" height="476px;" />

Keep in mind that this output is different, because it is in vector format. Our plan is to combine these three layers (the Wetlands, the Elevation < 275 meters, and the stream buffer) to see where they overlap, because where they overlap indicates a satisfaction of all three criteria for the species’ habitat.

In order to combine the streams buffer layer with the others, we have to **rasterize** it, since to combine the files they must all be in the same format, and the other two data sources are raster files.

Add the **Polygon to Raster** tool to the model from the ArcToolbox: **Conversion Tools > To Raster > Polygon to Raster.**

**Double-click** the Polygon to Raster tool in the Model Builder window, and set the **Input Features** to StreamsBuffer (with the recycle icon next ot it). The rest of the fields will automatically fill in after you select the input feature.

Change the **Output Raster Dataset** name to **BufferRaster**. The cell size of the other raster layers is 30 x 30 meters, so set the **cellsize** field to **98.4251**. Recall that the streams layer is in feet, so we needed to do some unit conversion to get the cell size in meters.

**Click Ok**. Before running the model, let’s add another conditional function to the model to convert the output to a Boolean value (1,0). Again, add the **CON** tool to the model. It can be found in the ArcToolbox under **Spatial Analyst > Conditonal > Con**.

**Double-click** the con tool, and set the input as **StreamBuffer_PolygonToRaster** (the output of rasterizing the streams layer), the **Input True** to 1, the **Input False** to 0, and the output name to **GoodStreamDis**. We do not need an expression in this case.

**Run** the model and check the output. Add it to the Table of Contents.
  
<img class="aligncenter" src="https://lh4.googleusercontent.com/ksv2Ub71SGFBSrLfif8j2KSpIICMyFCCyenyrmKXpqtIffZTixJS-KZfZZiljjnxM3Cv19vOyDC4q53puGw79EVA1oQBhGgDYjGH5xzOVBXJN47s4rE" alt="" width="540px;" height="283px;" />[Part 7: Bringing It All Together &#8211; Combining the Layers >](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-7/)