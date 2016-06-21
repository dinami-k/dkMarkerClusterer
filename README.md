# dkMarkerClusterer

Esta es una extensión de la versión de la libreria MarkerClusterer para manejar grandes cantidades de markers.

<h2>Versión Original</h2>
El archivo original de MarkerClusterer esta en:
<a href="https://github.com/googlemaps/js-marker-clusterer" target="_blank">Marker Clusterer</a>
<hr/>

<h2>Funcionalidades</h2>
<ul>
  <li> Clic sobre un markerCluster</li>
  <li> Mouse over sobre un markerCluster</li>
  <li> Mouse out sobre un markerCluster</li>
  <li> Campo para almacenar "data" adicional.</li>
  <li> Indicadores que permiten modificar el texto de un markerClusterer.</li>
</ul>
<hr/>

<h2>Uso</h2>
Descargar el archivo dkMarkerCluster.js y las imagenes m1.png a m3.png y crear un archivo como se indica a continuación:

``` 

<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>dkMarkerClusterer Example</title>
    <style >
      body, html {
        margin: 0;
        font-family: Arial;
        font-size: 16px;
        width: 100%;
        height: 100%;
        overflow: hidden;
      }
      #map-container {
        padding: 6px;
        border-width: 1px;
        border-style: solid;
        border-color: #ccc #ccc #999 #ccc;
        -webkit-box-shadow: rgba(64, 64, 64, 0.5) 0 2px 5px;
        -moz-box-shadow: rgba(64, 64, 64, 0.5) 0 2px 5px;
        box-shadow: rgba(64, 64, 64, 0.1) 0 2px 5px;
        width: 100%;
        height: 100%;
      }
      #map {
        width: 100%;
        height: 100%;
      }
    </style>

    <script src="https://maps.googleapis.com/maps/api/js"></script>
    <script type="text/javascript" src="dk.markerclusterer.js"></script>

    <script>
      function initialize() {

        var center = new google.maps.LatLng(-34.588050, -58.454756);

        var map = new google.maps.Map(document.getElementById('map'), {
          zoom: 11,
          center: center,
          mapTypeId: google.maps.MapTypeId.ROADMAP
        });

		var infowindow = new google.maps.InfoWindow({});

        var markers = [];
        var markers2 = [];
        var markers3 = [];

        var marker;
        var latLng;

		//push a markers
        latLng = new google.maps.LatLng(-34.549257, -58.485184);
        marker = new google.maps.Marker({ position: latLng });
        markers.push(marker);

        latLng = new google.maps.LatLng(-34.612217, -58.424544);
        marker = new google.maps.Marker({ position: latLng });
        markers.push(marker);

		//push a markers2
        latLng = new google.maps.LatLng(-34.607965, -58.461279);
        marker = new google.maps.Marker({ position: latLng });
        markers2.push(marker);

        latLng = new google.maps.LatLng(-34.546063, -58.466086);
        marker = new google.maps.Marker({ position: latLng });
        markers2.push(marker);

		//push a markers3
        latLng = new google.maps.LatLng(-34.557117, -58.464809);
        marker = new google.maps.Marker({ position: latLng });
        markers3.push(marker);

		var mcOptions1 = {
		    data: 'mi data 1',
			gridSize: 5000,
			maxZoom: 11,
			styles: [{
				 url: 'm1.png',
				 width: 53,
				 height: 52
			}],
			minimumClusterSize: 1,
			substractValue: 1,
			zoomOnClick: false
		};

		var mcOptions2 = {
			gridSize: 5000,
			maxZoom: 12,
			styles: [{
				 url: 'm2.png',
				 width: 56,
				 height: 55
			}],
			minimumClusterSize: 1,
			data: 'mi data 2',
			zoomOnClick: false
		};

		var mcOptions3 = {
			gridSize: 5000,
			maxZoom: 13,
			styles: [{
				 url: 'm3.png',
				 width: 66,
				 height: 65
			}],
			minimumClusterSize: 1,
			data: 'mi data 3',
			substractValue: 1,
			hideZero: true,
			zoomOnClick: false
		};


        var markerCluster = new MarkerClusterer(map, markers, mcOptions1);

		var markerCluster2 = new MarkerClusterer(map, markers2, mcOptions2);

		var markerCluster3 = new MarkerClusterer(map, markers3, mcOptions3);

		google.maps.event.addListener(markerCluster, 'clusterclick', function(cluster) {
    		map.setCenter(cluster.getCenter());
    		map.setZoom(15);
		});

		google.maps.event.addListener(markerCluster2, 'clusterclick', function(cluster) {
    		map.setCenter(cluster.getCenter());
    		map.setZoom(17);
		});

		google.maps.event.addListener(markerCluster3, 'clusterclick', function(cluster) {
		    alert(cluster.data_);
		});

		google.maps.event.addListener(markerCluster, 'clustermouseover', function (cluster) {
		    infowindow.setContent(cluster.data_);

		    infowindow.setPosition(cluster.getCenter());
		    infowindow.open(map);
		});

		google.maps.event.addListener(markerCluster, 'clustermouseout', function (cluster) {
			infowindow.close();
		});

		google.maps.event.addListener(markerCluster2, 'clustermouseover', function (cluster) {
		    infowindow.setContent(cluster.data_);

		    infowindow.setPosition(cluster.getCenter());
		    infowindow.open(map);
		});

		google.maps.event.addListener(markerCluster2, 'clustermouseout', function (cluster) {
			infowindow.close();
		});


		google.maps.event.addListener(markerCluster3, 'clustermouseover', function (cluster) {
		    infowindow.setContent(cluster.data_);

		    infowindow.setPosition(cluster.getCenter());
		    infowindow.open(map);
		});

		google.maps.event.addListener(markerCluster3, 'clustermouseout', function (cluster) {
			infowindow.close();
		});

		google.maps.event.addListener(map, 'click', function (event) {
           infowindow.close();
        });

      }
      google.maps.event.addDomListener(window, 'load', initialize);
    </script>
    
  </head>
  <body>
    <div id="map-container"><div id="map"></div></div>
  </body>
</html>

``` 
<hr/>
