---
id: 12017
title: Using ArcGIS Android SDK to Show Device Location on Map
date: 2013-07-23T16:11:54+00:00
author: Chandler
layout: post
guid: http://giscollective.org/?p=12017
permalink: /using-arcgis-android-sdk-to-show-device-location-on-map/
categories:
  - Update
---
<p style="text-align: center;">
  <a href="http://giscollective.org/wp-content/uploads/2013/07/Screenshot_2013-07-23-13-43-21.png"><img class="aligncenter  wp-image-12022" alt="Screenshot_2013-07-23-13-43-21" src="http://giscollective.org/wp-content/uploads/2013/07/Screenshot_2013-07-23-13-43-21.png" width="324" height="576" /></a>
</p>

So after spending WAY too much time looking for a simple tutorial to show how to add a device&#8217;s location to an Android App using the ArcGIS Android SDK, I decided to write one. This search caused me a lot of frustration and I imagine other new Android programmers have encountered the same thing. Follow these simple steps to add a device&#8217;s location to an Android App.

I added the project files to a [repository on GitHub](https://github.com/csterling/deviceLocationOnMap) for your viewing pleasure. Be warned, the app is only written to work on Android 4.2 devices- you&#8217;ll need to change the minimum version in the manifest to run it on older devices.

I apologize for the code formatting. To see the code in its entire formatted beauty, check out the [.java file on github](https://github.com/csterling/deviceLocationOnMap/blob/master/src/com/fuscoe/locationOnMapPractice/DeviceLocationOnMapActivity.java)

PS If a tutorial/resource exists that shows how to simply add the location to an app, please share!

* * *

To show the devices current location on a map, you need to utilize the [<p style="text-align: center;">
  <a href="http://giscollective.org/wp-content/uploads/2013/07/Screenshot_2013-07-23-13-43-21.png"><img class="aligncenter  wp-image-12022" alt="Screenshot_2013-07-23-13-43-21" src="http://giscollective.org/wp-content/uploads/2013/07/Screenshot_2013-07-23-13-43-21.png" width="324" height="576" /></a>
</p>

So after spending WAY too much time looking for a simple tutorial to show how to add a device&#8217;s location to an Android App using the ArcGIS Android SDK, I decided to write one. This search caused me a lot of frustration and I imagine other new Android programmers have encountered the same thing. Follow these simple steps to add a device&#8217;s location to an Android App.

I added the project files to a [repository on GitHub](https://github.com/csterling/deviceLocationOnMap) for your viewing pleasure. Be warned, the app is only written to work on Android 4.2 devices- you&#8217;ll need to change the minimum version in the manifest to run it on older devices.

I apologize for the code formatting. To see the code in its entire formatted beauty, check out the [.java file on github](https://github.com/csterling/deviceLocationOnMap/blob/master/src/com/fuscoe/locationOnMapPractice/DeviceLocationOnMapActivity.java)

PS If a tutorial/resource exists that shows how to simply add the location to an app, please share!

* * *

To show the devices current location on a map, you need to utilize the](https://developers.arcgis.com/en/android/api-reference/reference/com/esri/android/map/LocationService.html) class.

First of all, define the MapView in the standard onCreate method, and add the basemap (and any other layers):

<pre><b>public</b> <b>void</b> onCreate(Bundle savedInstanceState) {&lt;/code>

    <b>super</b>.onCreate(savedInstanceState);

    setContentView(R.layout.<i>main</i>);

    mMapView = (MapView) findViewById(R.id.<i>map</i>);

    mMapView.addLayer(<b>new</b> ArcGISTiledMapServiceLayer(<br />    "http://services.arcgisonline.com/ArcGIS/rest/services/<br />    World_Street_Map/MapServer"));
</pre>

After the MapView has been created, add a setOnStatusChangedListener to it. Inside this method is where we will establish the LocationService via a new OnStatusChangedListener and a method called onStatusChanged.

<pre>mMapView.setOnStatusChangedListener(<b>new</b> <span style="text-decoration: underline;">OnStatusChangedListener()</span> {&lt;/code>

    <b>public</b> <b>void</b> onStatusChanged(Object source, STATUS status) {

        <b>if</b> (source == mMapView && status == STATUS.<i>INITIALIZED</i>) {

            LocationService ls = mMapView.getLocationService();

            ls.setAutoPan(<b>false</b>);

            ls.start();
          }
       }
});
</pre>

&nbsp;

Here is the full java (main) activity code to add your device’s location to your android application:

&nbsp;

<pre><b>package</b> com.fuscoe.locationOnMapPractice;

&nbsp;

<b>import</b> android.app.Activity;

&nbsp;

<b>import</b> <span style="text-decoration: underline;">android.location.Location</span>;

<b>import</b> <span style="text-decoration: underline;">android.location.LocationListener</span>;

<b>import</b> android.os.Bundle;

&nbsp;

<b>import</b> com.esri.android.map.LocationService;

<b>import</b> com.esri.android.map.MapView;

<b>import</b> com.esri.android.map.ags.ArcGISTiledMapServiceLayer;

<b>import</b> com.esri.android.map.event.OnStatusChangedListener;

&nbsp;

<b>public</b> <b>class</b> LocationOnMapPracticeActivity <b>extends</b> Activity {

&nbsp;

    MapView mMapView;

&nbsp;

    /** Called when the activity is first created. */

    @Override

    <b>public</b> <b>void</b> onCreate(Bundle savedInstanceState) {

        <b>super</b>.onCreate(savedInstanceState);

        setContentView(R.layout.<i>main</i>);


        mMapView = (MapView) findViewById(R.id.<i>map</i>);

        mMapView.addLayer(<b>new</b> ArcGISTiledMapServiceLayer(

        "http://services.arcgisonline.com/ArcGIS/rest/services/<br />        World_Street_Map/MapServer"));

        mMapView.setOnStatusChangedListener(<br />            <b>new</b> <span style="text-decoration: underline;">OnStatusChangedListener()</span> {



        <b>public</b> <b>void</b> onStatusChanged(Object source, STATUS status) {

            <b>if</b> (source == mMapView && status == STATUS.<i>INITIALIZED</i>) {

                LocationService ls = mMapView.getLocationService();

                ls.setAutoPan(<b>false</b>);

                ls.start();
             }
          }
      });
}


@Override

<b>protected</b> <b>void</b> onDestroy() {

    <b>super</b>.onDestroy();

}


@Override

<b>protected</b> <b>void</b> onPause() {

    <b>super</b>.onPause();

    mMapView.pause();

}

&nbsp;

@Override

<b>protected</b> <b>void</b> onResume() {

    <b>super</b>.onResume();

    mMapView.unpause();

  }

}</pre>