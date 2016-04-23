---
id: 456
title: Creating Custom Tools in ArcGIS – Model Builder (Part 8)
date: 2012-07-22T13:21:25+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=456
---
[< Part 7: Bringing It All Together: Combining the Layers](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-7/)

**Run the Model from the Beginning!**
  
All right! The model is complete! Let’s completely run this sucker from the beginning to end. First off, remove all data layers except the four original ones. In other words, remove everything except DaneProtectedAreas, DaneStreams, DaneLandCover, and danedem.

If the _Add to Display_ option was working for your model, go ahead and right-click all layers that have that option toggled, and disable it. We only want our end result to appear in the map, and don’t need the many layers that it took to get there.

Before running the model, let’s reset it by checking **Validate Entire Model**. Do this by clicking the **Model** menu at the top of Model Builder window, and selecting **Validate Entire Model**. You’ll notice that the drop shadows on the tools and outputs are gone now.

Okay, we’re ready to run! Click the **run button** and watch as the model runs. (In 9.3, the tool icon turns red as it is processing, and adds a drop shadow upon completion of the tool. I’m not sure why it does not do this in Arc10).

Go to **Add Data**  > and add the **GoodHabitat** and **ProtectedHabitat** layers. These are the two layers we are interested in for determining suitable habitat for _homo delphinidae_. Both layers satisfy our three criteria for suitable habitat!

_What If It Doesn’t Work!_
  
Watch the output in the box while the model is running. If there is an error there will be red text. The program will say that the model-run is complete, even though an error occurred. Beware of this. If an error does occur, read the red text and see where the model broke. Make sure that your files are all in the Dane County GeoDatabase, and that the parameters being passed to them are valid. This is a huge issue and that is why setting your paths and parameters correctly the first time is very important.

If your model does break, make an attempt to fix your issue, and **Validate Entire Model** again, to reset the model.

[Part 9: Setting Up the Model as a Tool >](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-9/)