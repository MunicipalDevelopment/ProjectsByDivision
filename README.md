# Projects By Division

The Projects by Division application can be found at the [Ongoing City Construction Projects](http://cognospublic.cabq.gov/cabqcognos/cgi-bin/cognos.cgi?b_action=cognosViewer&ui.action=run&ui.object=%2fcontent%2ffolder[%40name%3d%27DMD%20Projects%27]%2freport[%40name%3d%27DMD%20Division%20Projects%27]&ui.name=DMD%20Division%20Projects&run.outputFormat=&run.prompt=true)
page. The map is activated after running the Cognos report.

Using ESRI Leaflet, the feature is drawn by calling the service [DMD Projects Active](http://coagisweb.cabq.gov/arcgis/rest/services/public/fullviewer/MapServer/16) and supplying a query option.
```js
q="OBJECTID="+params.objectid;
var project = L.esri.featureLayer('http://coagisweb.cabq.gov/arcgis/rest/services/public/fullviewer/MapServer/16/',
              {where:q}).addTo(map);
```

The objectid is passed by Cognos when creating the iframe. You can open a URL directly using:

`http://coagisweb.cabq.gov/ProjectsByDivision/ProjectsByDivision.html?objectid=23513`

The use of ESRI Leaflet simplified the filtering vs using the ESRI REST API. An older version of this application
used the first and last coordinates of the feature to zoom to the layer. Not ideal.

### Warning
Using `objectid` is not a good idea. You should use another field if at all possible. The initial search in Cognos is done on project name. Cognos grabs the data for the feature for display and in doing so sends the objectid to the map application as an easy way to query the service.
