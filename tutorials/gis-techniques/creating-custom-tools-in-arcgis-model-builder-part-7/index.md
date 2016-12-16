---
id: 453
title: Creating Custom Tools in ArcGIS – Model Builder (Part 7)
date: 2012-07-22T13:19:07+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=453
---
[< Part 6: Criteria 3: Habitat Within 500 ft of a Stream](http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-6/)

<address>
  <strong>Bringing it All Together &#8211; Combining the Layers</strong><br /> So now we data that satisfies the three criteria, in raster form, and if we combine them all we can find areas of suitable habitat for our species! The end is in sight!We will need to use a <strong>Math</strong> function to combine the three layers. Fortunately, we planned ahead got our three raster files to have pixels of the same size. This will make the overlay process much easier.</p> 
  
  <p>
    We will overlay the layers and then perform mathematical functions on them. Since each area of suitable criteria has a value of 1, we can simply add the pixel values together and conclude that any area with a value of 3 is suitable for our species!
  </p>
  
  <p>
    Add the PLUS tool to the model. It can be found in the ArcToolbox under <strong>Spatial Analyst Tools > Math > Plus</strong>.
  </p>
  
  <p>
    Using the<strong> Connector</strong> tool, draw a line from the <strong>GoodType</strong> layer to the<strong> Plus</strong> tool, and select <strong>Input Raster 1</strong> from the menu that pops up after you release the mouse click. Do the same thing for the <strong>goodElevation</strong> layer, and select<strong> Input Raster 2</strong> from the menu. <strong>Rename</strong> the output raster to <strong>GoodTE</strong>. GoodTE stands for Good Type and Elevation.
  </p>
  
  <p>
    Add another <strong>PLUS</strong> tool to the model, but this time connect the <strong>GoodTE</strong> layer and the <strong>GoodStreamsDis</strong> layer. <strong>Double-click</strong> the tool and name this output <strong>GoodTED</strong> (Good Type, Elevation, and Distance), make sure the directory is set to the Dane County GeoDatabase, and<strong> run</strong> the model. Choose<strong> Input Raster 1</strong> for the GoodTE layer and<strong> Input Raster 2</strong> for the GoodStreamsDis layer.
  </p>
  
  <p>
    <img class="aligncenter" src="https://lh4.googleusercontent.com/_mkt7rEgy0gMWlUK2LbEcog3WqhMx7eQXxA_eaf5tgd3TuxUlMFE17LPiR-hRMrdgyu6FRKQjJ7yr5iKkTBAv2j_L_ucIpg9ZY6xXgAVSfX_SX-bvEs" alt="" width="665px;" height="493px;" />Add the GoodTED layer to the Table of Contents.
  </p>
  
  <p>
    <em>Extract Potential Habitat</em><br /> The GoodTED file should be a three-colored raster file that resembles the buffer streams file in shape. Each color indicates a value of 1 through 3. Remember, the pixels with a value of 3 represent areas of Dane County that satisfy all three of our criteria.
  </p>
  
  <p>
    Our next step is to extract the suitable habitat areas, and convert it into vector format. From the ArcToolbox, add the <strong>Raster to Vector</strong> tool to the model. It can be found in <strong>Conversion Tools > From Raster > Raster to Polygon</strong>.
  </p>
  
  <p>
    <strong>Double-click</strong> the Raster to Polygon tool and set the <strong>Input Raster</strong> to <strong>GoodTED</strong> and rename the output to<strong> PotHabitat</strong> (for potential habitat). Click <strong>OK</strong>.
  </p>
  
  <p>
    We need to export all polygons that satisfy our three criteria after we have vectorized our potential habitat raster layer. Add the <strong>Select</strong> tool to the model and <strong>double-click</strong> the tool to open the dialogue box. The Select tool can be found in the ArcToolbox under<strong> Analysis Tools > Extract > Select.</strong> For the input feature, select <strong>PotHabitat</strong>, and for the output feature class, navigate to the Dane County GeoDatabase and rename the output file “GoodHabitat.” For the <strong>Expression</strong>, write &#8220;<strong>GRIDCODE&#8221; = 3</strong>. Click <strong>OK</strong> and run the tool.
  </p>
  
  <p>
    Add the <strong>GoodHabitat</strong> file to the Table of Contents, and check it out! These are all the good locations for our species’ habitat. Pretty awesome!
  </p>
  
  <p>
    However, we’re not in the clear yet! We still want to find where the Potential Habitat falls within current protected areas.
  </p>
  
  <p>
    <em>Find Where Potential Habitat and Protected Areas Overlap</em><br /> Now that we have a vector layer representing good potential habitat for Homo Delphinidae, let’s check to see where they overlap with currently protected areas. We’ll use a simple <strong>clip</strong> operation to derive this information!
  </p>
  
  <p>
    Add the <strong>clip</strong> tool to the model from the ArcToolbox, which is located under <strong>Analysis Tools > Extract > Clip</strong>. Double-click the <strong>clip tool</strong> and set the input features to the <strong>GoodHabitat</strong> layer, the <strong>clip features</strong> to the <strong>DaneProtectedAreas</strong> layer, and navigate to the Dane County GeoDatabase and rename the output to <strong>ProtectedHabitat</strong>.<br /> <img class="aligncenter" src="https://lh4.googleusercontent.com/DVU3VjUNnxok24vytnUOq_P2SBJf84Jwi5lPenHeE0Pjx1OyZFBPolbfDE4_V0No_TaYIC59aCs_6zdp4963OIkXF2GqUJzNaxgjSlN2ex_X_FvPqC0" alt="" width="692px;" height="214px;" />
  </p>
</address>

<address>
  <a href="http://giscollective.org/tutorials/gis-techniques/creating-custom-tools-in-arcgis-model-builder-part-8/">Part 8: Run the Model from the Beginning! ></a>
</address>