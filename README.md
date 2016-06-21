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

    <script src="https://maps.googleapis.com/maps/api/js"></script>
    <script type="text/javascript" src="dk.markerclusterer.js"></script>

    <script>
	...      
	var mcOptions1 = {
		data: 'mi data 1',
		substractValue: 1,
		hideZero: true,
		zoomOnClick: false
		gridSize: 5000,
		maxZoom: 11,
		styles: [{
			url: 'm1.png',
			width: 53,
			height: 52
		}],
		minimumClusterSize: 1,
	};

	...

	


``` 
<hr/>
