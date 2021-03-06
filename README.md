# DrawRouteMaps
Library for draw route maps between two point LatLang

![alt tag](https://github.com/ar-android/DrawRouteMaps/raw/master/example-app.png)

This is an Android project allowing to realize a PercentView instead of LinearLayout in the simplest way possible.

#Usage
Make sure your app have ready enable Google Map API and Google Direction API. Then you can use this library and follow this task to ad DrawRouteMaps into your project.

Add support jitpact repository in root build.gradle at the end of repositories:
```gradle
allprojects {
   repositories {
	maven { url "https://jitpack.io" }
   }
}
```
Add dependencies :
```gradle
dependencies {
    compile 'com.github.ar-android:DrawRouteMaps:1.0.0'
}
```

In Your GoogleMap Ready
-----
```java
    @Override
    public void onMapReady(GoogleMap googleMap) {
        mMap = googleMap;
        LatLng origin = new LatLng(-7.788969, 110.338382);
        LatLng destination = new LatLng(-7.781200, 110.349709);
        DrawRouteMaps.getInstance(this)
                .draw(origin, destination, mMap);
        DrawMarker.getInstance(this).draw(mMap, origin, R.drawable.marker_a, "Origin Location");
        DrawMarker.getInstance(this).draw(mMap, destination, R.drawable.marker_b, "Destination Location");

        LatLngBounds bounds = new LatLngBounds.Builder()
                .include(origin)
                .include(destination).build();
        Point displaySize = new Point();
        getWindowManager().getDefaultDisplay().getSize(displaySize);
        mMap.moveCamera(CameraUpdateFactory.newLatLngBounds(bounds, displaySize.x, 250, 30));
    }
```
If you want to change color of line route just add this in your resource
```xml
    <color name="colorRouteLine">#FF4081</color>
```

LICENCE
-----

DrawRouteMaps by [Ahmad Rosid](http://ahmadrosid.com/) is licensed under a [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).
