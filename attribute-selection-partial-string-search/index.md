---
id: 8991
title: 'Attribute Selection &#8211; Partial String Search and Field Data Type Conversion in ArcGIS'
date: 2012-10-26T10:41:19+00:00
author: Chandler
layout: page
guid: http://giscollective.org/?page_id=8991
---
\*In this short tutorial I will discuss performing Partial String Searches and Converting Field Data Types in ArcGIS \* Using the LIKE operator in the Attribute Selection dialog box allows you build selection queries to select partial values of strings. For instance, say you are interested in selecting all states that start with the letter ‘W’, or selecting all contour lines that end in 0 or 5 to build a 5ft contour base from a 1ft contour line dataset. If you are interested in searching through a field that is not a string value (e.g., integer, float, double) you will need to convert that column to a string, or Text, values. **Skip ahead to Partial Selections if you’re not working with integers, floats or doubles** **Converting non-text field values to text values** Open the Attribute Table and click the **Table Options** button and select Add Field.

<p align="center">
  <a href="http://giscollective.org/wp-content/uploads/2012/10/newField.png"><img class="aligncenter  wp-image-8998" title="newField" src="http://giscollective.org/wp-content/uploads/2012/10/newField.png" alt="" width="261" height="408" /></a>
</p>

 In the Add Field dialog box, give your new field a name (I suggest appending the name with _STR) and for the type select “Text.” Click OK.

<p align="center">
  <a href="http://giscollective.org/wp-content/uploads/2012/10/newfield_props.png"><img class="aligncenter  wp-image-8995" title="newfield_props" src="http://giscollective.org/wp-content/uploads/2012/10/newfield_props.png" alt="" width="213" height="218" /></a>
</p>

The new column should now be added to the attribute table. Now use the Field Calculator to bring the values from the non-string column you’re interested in. To do this, right click on the new field and select Field Calculator. If you’re not in an edit session, an alert message will pop up, it’s just warning you that you cannot undo any results that are calculated. That’s okay, click Yes. In the Field Calculator window, double click the field you are interested in selecting from. Essentially, what we’re doing is copying the data from the original column that is in non-string (non-text) format, and turning it into string (text) format for partial selecting.

<p align="center">
  <a href="http://giscollective.org/wp-content/uploads/2012/10/field-calculator.png"><img class="aligncenter size-full wp-image-8997" title="field calculator" src="http://giscollective.org/wp-content/uploads/2012/10/field-calculator.png" alt="" width="241" height="269" /></a>
</p>

Click OK and the new values generated should be a copy of the original field, in text format.

\*\*Partial Selections \*\*Open the Select By Attributes window by clicking Selection > Select By Attributes. Double click the new field that was just created to add it to the selection query. Click the LIKE button. Use the % sign to tell the query that any value is acceptable in its place.

<p align="center">
  <a href="http://giscollective.org/wp-content/uploads/2012/10/selectByAttributes.png"><img class="aligncenter  wp-image-8996" title="selectByAttributes" src="http://giscollective.org/wp-content/uploads/2012/10/selectByAttributes.png" alt="" width="346" height="466" /></a>
</p>

For instance, in this scenario I am interested in selecting all values of elevation that end in 0. I would write ‘%0’ to indicate that any value that comes before 0 is acceptable. The entire query that would be built would be “

_your\_new\_field_string_” LIKE ‘%0’ **NOTE:** You must use single quotes following the LIKE You could also use the % sign to select all states beginning with the letter W by writing “_state\_name\_field”_ LIKE ‘W%’ Partial String Selection allows for more complex selections from your data and is a great way to perform advanced selection queries. For more information on using the Select by Attributes function in ArcGIS, see their [Help Guide](http://webhelp.esri.com/arcgisdesktop/9.2/index.cfm?Topicname=Using_Select_By_Attributes) on it.

<p align="center">