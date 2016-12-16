---
id: 11740
title: Numbered Icons in Leaflet
date: 2012-10-31T23:30:05+00:00
author: John Czaplewski
layout: page
guid: http://giscollective.org/?page_id=11740
---
In the event you find yourself needing numbered icons in Leaflet, this [quick demo](http://maps.johnjcz.com/label_test/leaflet_labels.html) is a great place to start. It uses [Leaflet.Iconlabel](https://github.com/jacobtoye/Leaflet.iconlabel), a very nice Javascript plugin for [Leaflet](http://leafletjs.com) that allows the user to put text labels next to icons, but in the above example it is being used to create numbered marker icons. Here are some tips if you wish to replicate the above example for your own project:

First, get rid of the `background` property of `.leaflet-label-iconlabel `in leaflet.iconlabel.css. Because the label is being placed on top of a marker, there is no need to specify this property unless a background color is needed to make the text stand out. Additionally, you need to create your own CSS rules for whatever class you are going to apply to the label for each marker – in this case `placeMarkers_label` was used. To ensure the numbers appear on top of the icon, make sure this class contains `position:relative`. Because the numbers are going on top of a blue marker, also specify that the text should be white in this CSS class. In the above example, it ends up looking like this:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="line_numbers">
        <pre>1
2
3
4
5
6
7
</pre>
      </td>
      
      <td class="code">
        <pre class="css" style="font-family:monospace;"><span style="color: #6666ff;">.placeMarks-label</span> <span style="color: #00AA00;">&#123;</span>
   -moz-box-shadow<span style="color: #00AA00;">:</span> <span style="color: #993333;">none</span><span style="color: #00AA00;">;</span>
   -webkit-box-shadow<span style="color: #00AA00;">:</span> <span style="color: #993333;">none</span><span style="color: #00AA00;">;</span>
   box-shadow<span style="color: #00AA00;">:</span> <span style="color: #993333;">none</span><span style="color: #00AA00;">;</span>
   <span style="color: #000000; font-weight: bold;">color</span><span style="color: #00AA00;">:</span> <span style="color: #cc00cc;">#fff</span><span style="color: #00AA00;">;</span>
   <span style="color: #000000; font-weight: bold;">position</span><span style="color: #00AA00;">:</span><span style="color: #993333;">relative</span><span style="color: #00AA00;">;</span>
<span style="color: #00AA00;">&#125;</span></pre>
      </td>
    </tr>
  </table>
</div>

Perhaps the ugliest part of this “hack” is the need to create a new icon label class (L.Icon.Label.extend) for each length of label that might occur. Fortunately, in this example we are limited to three digits, so only three different classes needed to be created. 

In the code you will see three Javascript variables, `placeMarker_single`, `placeMarker_double`, and `placeMarker_triple`. They are all identical, with the exception of the `labelAnchor`, which varies by a few points to ensure the labels are aligned to the center of the icon. Depending on your font size, weight, etc, you will need to change this property accordingly.

That should help you get started! If you have any questions, please let us know, or contact the author (@JJCzaplewski).