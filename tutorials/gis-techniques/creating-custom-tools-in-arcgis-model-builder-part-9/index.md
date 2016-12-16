---
id: 458
title: Creating Custom Tools in ArcGIS – Model Builder (Part 9)
date: 2012-07-22T13:25:23+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=458
---
[< Part 8: Run the Model from the Beginning!](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-8/)

**Setting Up the Model as a Tool**
  
As discussed earlier, the whole purpose of creating this model is to be able to run the exact same operations on other data. In order to use this model as a tool with other counties (in our case, Iowa County), we first need to make a few modifications to the model.

The modifications include setting our **Inputs** and **Final Outputs** as **Parameters**. Parameters are the data required to successfully run the model. **Right-click** on each data input and select **“Model Parameter”** to set the inputs as parameters. A bold letter P will appear next the data input to indicate that it is a parameter of the model.
  
<img class="aligncenter" src="https://lh6.googleusercontent.com/O8mNQ0xTr-GaT_qx-wQQgyiOE-9hPZhc3risZMngj6lVbzPd8XASrBRH-D1Oz0JYPZlxcOyOANp_HFGkqmKZo-uhqiHZ0jTxCKoct5S8euBTB29u_9k" alt="" width="454px;" height="300px;" />As a reminder, there were four inputs for our model, named: Landcover, Elevation, Streams, and Protected Areas.

Make the two final outputs (**GoodHabitat** and **ProtectedHabitat**) parameters as well.

_Heads Up!_ The text, or name, of the input parameter will be the text seen in the dialog box field for that parameter. For instance, one of our model’s parameters is named “Landcover” so in the tool’s dialogue box, it will say “Landcover” for the layer to be used. It’s a pretty easy concept to understand, but it’s important to keep in mind. Additionally, the order in which you assign the parameters in the model is the order in which they will appear in the tool’s dialogue box.

As is, our model is limited in flexibility. Say we want to use this tool for identifying a different species than the _Homo Delphinidae_, and let’s say that species’ habitat criteria is slightly different, such as living within 1000 feet of a stream. At this point, the model is rigid and only would create a 500 ft buffer around the streams. Let’s make the model a little more flexible so it can be applied more widely.

To do this, we will need to create a variable and set it as a parameter. **Right-click** on the **buffer** tool and select **Make Variable > From Parameter > Distance**. You’ll notice a light-blue oval appears in the model builder window, connected to the buffer tool. **Set this variable as a parameter** of the model as well.

Our model is finally finished! **Save it** by clicking **Model > Save**. **Rename** the model to **Habitat Analysis** by right-clicking the model in the toolbox and selecting Rename.

Now the moment we’ve been waiting for, running the model with completely different data! **Remove** all current data from the table of contents and add in the IowaStreams, IowaProtectedAreas, IowaDem, and IowaLandcover layers.

**Run** the habitat analysis model! Boom! Done! Check out the output! Remember, the GoodHabitat and ProtectedHabitat layers are the ones we are interested in for finding suitable habitat!

_What if it doesn’t work!_
  
If an error occurs (perhaps that the model has no parameters) you can remedy this temporarily by editing the model. Double click on each input parameter and set the data source to the appropriate data layer. For instance, double click on the Landcover layer and select the IowaLandcover layer from the menu. It is also a good idea to check the output paths for the new files. Make sure that they are saved in the correct directory. Run the model after the changes have been made and check out your new ouput!

Using Model Builder can save you hours of repetitive work. I hope this tutorial succinctly explained the concepts of model builder, and maybe even helped you see some practical applications of using it in your own work!