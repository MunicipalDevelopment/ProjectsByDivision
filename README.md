# Projects By Division

The goal of this application was to allow a user to select a project from Cognos and see it on a map.

The original version used a third party addin to Leaflet to display the [DMD Projects - Active](http://coagisweb.cabq.gov/arcgis/rest/services/public/fullviewer/MapServer/16) REST endpoint. 

The application then queries the REST Endpoint to find the selected project by objectid. It grabbed the first coordinates from the result, then decided if the feature was a line or polyline based on the length of coordinates. Pushing the coordinates to an array, it then loaded the feature as GeoJSON in red - as opposed to the other projects which were rendered blue. 

This was a very complicated way in which to go about displaying a single feature. The next iteration used ESRI Leaflet to simplify the code significantly. 
