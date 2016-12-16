---
id: 424
title: Creating Custom Tools in ArcGIS – Model Builder (Part 3)
date: 2012-07-22T12:56:32+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=424
---
[< Part 2: The Exercise: Analyze and Identify Potential Habitat for Homo Delphinidae](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-3/)

**Let’s Build That Model!**

_Prepare the Environment_
  
The first step is to **Launch ArcMap**. This exercise requires the **spatial analyst extension** so be sure that it’s activated. We want to activate a setting to automatically overwrite the output since we will be running the model multiple times. To do this:

Arc 9.3
  
**Tools > Options > Geoprocessing Tab >** check the **“Overwrite the outputs of geoprocessing operations”** box.

Arc 10
  
**Geoprocess > Geoprocessing Options >** check the **“Overwrite the outputs of geoprocessing operations”** box

_Create a Personal Toolbox to Store Your Model_
  
Go ahead and open ArcToolbox if it is not already open. **Right-click** in the white space and select **Add Toolbox**. This will be the container that stores your models. Navigate to a desired directory, click the **Red Toolbox** icon in the upper right corner to create a new toolbox, and name it **MyTools**. **Select** your new toolbox and click **Open**.

If you look in the ArcToolbox you will see that your new toolbox has been added to the collection of toolboxes.

[<img class="size-medium wp-image-425 aligncenter" title="newToolbox" src="http://giscollective.org/wp-content/uploads/2012/07/newToolbox-255x300.png" alt="" width="255" height="300" />](http://giscollective.org/wp-content/uploads/2012/07/newToolbox.png)

Now, let’s create a model and add it to our new toolbox. To add a new model to your toolbox, **right-click** on your toolbox and select **New > Model**. Selecting this will launch the Model Builder window.

[<img class="aligncenter size-medium wp-image-431" title="modelBuilderWindow" src="http://giscollective.org/wp-content/uploads/2012/07/modelBuilderWindow-300x219.png" alt="" width="300" height="219" />](http://giscollective.org/wp-content/uploads/2012/07/modelBuilderWindow.png)

_Heads up!_ If you close the Model Builder window, you’ll need to right-click and select **Edit** to open the window again. If you select the **Open** option, you’ll end up _running_ the model, not _editing_ it. Feel free to try to run the model now, you’ll get an error telling you the model has no parameters.

[Part 4: Adding Data](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-4/) >