---
id: 990
title: Generating CAD Files from GIS Data
date: 2012-09-20T11:29:38+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=990
---
**Generating CAD Files from GIS Data**

_This tutorial explains how to generate CAD files from GIS data, focusing on using Contour Line data_

If you ever work with civil engineers you will quickly learn that they live in the world of Computer Aided Graphics (CAD) software, and have little to no knowledge of GIS. They may request you to prepare data for them, such as by generating contour lines or simply providing them with building footprint data.

Popular software such as AutoCAD can read and display geographic data such as shapefiles, but an issue with the CAD software is that it does not bring in the associated feature attributes of the file. If you are providing the engineers with contour lines, it is crucial that the elevation attributes of each line are included in the file.

So if engineers can’t get feature attribute data from shapefiles, how are we supposed to provide them GIS support? Fortunately, ArcGIS provides a few tools that aid us in the process.

The most obvious tool we would want to use is the **Export to CAD** tool, found in **Conversion Tools > To CAD > Export to CAD**. Double-clicking on the tool opens a dialog box which prompts the user to specify input data to be combined into one CAD file. There are many Output Type options to choose from, so make sure you know what format you need the CAD file to be in.

[<img class="wp-image-994 aligncenter" title="export to cad" src="http://giscollective.org/wp-content/uploads/2012/09/export-to-cad.jpg" alt="" width="436" height="281" />](http://giscollective.org/wp-content/uploads/2012/09/export-to-cad.jpg) HOWEVER, before performing the Export to CAD operation, we need to some pre-processing to make sure our attribute data is retained! We could run this operation on a shapefile with no pre-processing if the data did not need attributes, such as building footprints. I.e, Go ahead and use this operation if you don’t need to retain attribute data.

If you’re working with data such as contours and need to retain the elevation data, we have to run one operation on the data first before converting to CAD. The operation we need to run is called **Feature to 3D by Attribute**, located in the ArcToolbox under 3D Analyst Tools > 3D Features > Feature to 3D By Attribute. Essentially, this tool gives your data 3D attribute, and you specify what field to turn into the 3D field.

[<img class="aligncenter  wp-image-992" title="to 3d" src="http://giscollective.org/wp-content/uploads/2012/09/to-3d.jpg" alt="" width="376" height="246" />](http://giscollective.org/wp-content/uploads/2012/09/to-3d.jpg)

So, the steps to turning contour data into CAD data are as follows:

  1. Load Contour data into ArcMap.
  2. In the ArcToolbox, open the Feature to 3D by Attribute tool (3D Analyst Tools > 3D Features > Feature to 3D by Attribute)
  3. For the **Input Features** field, select your contour file. For the **Output Feature Class** select the directory you want your new 3D enabled file to be stored, and give it a name. For the **Height Field** select the elevation field from your input file.
  4. Click Ok.
  5. Next in the ArcToolbox, open the **Export to CAD** tool (Conversion Tools > To CAD > Export to CAD)
  6. For the **Input Features** field, select your newly generated, 3D enabled contour line file. Specify the **Output Type** and then choose the directory where you want to store the CAD file and give it a name.
  7. Click Ok.
  8. Send the file to your CAD user after the **Export to CAD** operation runs!

For those interested, I have created a tool to automate the contour generation and exportation to CAD process with Model Builder. It is more complicated than converting to 3D and exporting to CAD.

The model requires a DEM and project area (polygon) for its inputs. It clips the DEM to the project area, generates contours from the clipped area, and smooths the contours first, before converting to 3D by attribute and exporting to CAD.

You can download the toolbox [here](https://s3.amazonaws.com/yorbaLinda/Contour+Generation.zip).

Also included in the toolbox is a tool for generating contours from a DEM for a project area, but does not perform the processing for exporting to CAD. I use that tool for when I need contours but don’t need to send it to CAD users.

Here is the Model Builder flow chart: [<img class="aligncenter size-full wp-image-991" title="flowchart" src="http://giscollective.org/wp-content/uploads/2012/09/flowchart.jpg" alt="" width="977" height="322" />](http://giscollective.org/wp-content/uploads/2012/09/flowchart.jpg)

Here is a screenshot of the custom tool for generating contours and exporting to CAD:

[<img class="wp-image-993 aligncenter" title="tool box" src="http://giscollective.org/wp-content/uploads/2012/09/tool-box.jpg" alt="" width="519" height="335" />](http://giscollective.org/wp-content/uploads/2012/09/tool-box.jpg)

To add the tools to Arc, right-click on the **ArcToolbox** and select **Add Toolbox**. Navigate to the directory where the toolbox is saved, click on the toolbox, and click Open. The toolbox will now be included in the list of toolboxes in the ArcToolbox!

<p align="center">