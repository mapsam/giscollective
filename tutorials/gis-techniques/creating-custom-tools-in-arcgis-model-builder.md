---
id: 412
title: 'Creating Custom Tools in ArcGIS &#8211; Model Builder'
date: 2012-07-22T12:32:24+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=412
---
By Chandler Sterling

_This tutorial is broken into 9 parts. _
  
1. Introducing Model Builder with ArcGIS
  
[2. The Exercise: Analyze and Identify Potential Habitat](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-3/)
  
[3. Let&#8217;s Build That Model! ](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-2/)
  
[4. Adding Data](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-4/)
  
[5. Criteria 2: Elevations Under 275 Meters](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-5/)
  
[6. Criteria 3: Habitat Within 500 ft of a Stream](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-6/)
  
[7. Bringing it all Together &#8211; Combining the Layers](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-7/)
  
[8. Run the Model from the Beginning!](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-8/)
  
[9. Setting up the Model as a Tool  ](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-9/)

**Introducing Model Builder with ArcGIS**

If you’ve ever had to process a lot of GIS data, you may have noticed yourself going crazy, repeating the same task OVER and OVER and OVER and OVER again. As you’re slowly going crazy, you probably were thinking to yourself, ‘Boy I wish I could automate this process and let the computer do all of the work for me.’

Well, good news! With the use of ArcGIS’s Model Builder you can create a model by developing a process for automating analysis or tasks, which can end up saving you tons of time. Your boss will be impressed too, because you’re handling company time efficiently.

First, let’s discuss what a model is. Essentially, a model is a process, or set of processes, all packaged together. A process is a **tool**, such as **buffer** or **union**, and the tool’s **variables**. The variables are the parameters that you pass to the tool, such as buffer distance, or cluster tolerance.

Again, a model is a compilation of process(es). The idea behind creating a model is that you can perform a repetitive work flow with only one click. When the model is created, you can save it and add it to the ArcToolbox for future use. If you’re a code junkie, you can export the Python code and run it from a terminal. You can also run it from the Model Builder interface as well. It’s all up to your personal preference.

Another cool feature of Model Builder is that you can easily share the model with others (other GIS grunts like yourself) via the toolbox or the Python script.

[Part 2: The Exercise: Analyze and Identify Potential Habitat for Homo Delphinidae](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-3/) >