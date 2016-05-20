# Leaflet.idw
A small Leaflet plugin to generate an IDW interpolation map
Leaflet.heat

A tiny, simple and fast Leaflet inverse distance weighting plugin. Largely based on the [Leaflet.heat] (https://github.com/Leaflet/Leaflet.heat) plugin by Vladimir Agafonkin.
Leaflet.idw implements a simple inverse distance weighting algorithm. Every cell is calculated with the center of the cell (h/2,w/2) as the anchor from which the distance to the points is calculated.

Demos

    coming soon...
    
Examples
CellSize: 1
![Image of CellSize 1](https://github.com/JoranBeaufort/Leaflet.idw/blob/master/example/Example-1px.png)

CellSize: 5
![Image of CellSize 1](https://github.com/JoranBeaufort/Leaflet.idw/blob/master/example/Example-5px.png)

CellSize: 10
![Image of CellSize 1](https://github.com/JoranBeaufort/Leaflet.idw/blob/master/example/Example-10px.png)

#### Basic Usage

```
var idw = L.idwLayer([
    [50.5, 30.5, 0.2], // lat, lng, intensity
    [50.6, 30.4, 0.5],
    ...
], {opacity: 0.3, cellSize: 10, exp: 2, max: 1200}).addTo(map);
```

To include the plugin, just use leaflet-idw.js from the src folder:

```<script src="leaflet-idw.js"></script>```

#### Options

Constructs an IDW layer given an array of points and an object with the following options:

    opacity - the opacity of the IDW layer
    max - maximum point values, 1.0 by default
    cellSize - height and width of each cell, 25 by default
    exp - exponant used for weighting, 1 by default
    gradient - color gradient config, e.g. {0.4: 'blue', 0.65: 'lime', 1: 'red'}

Each point in the input array can be either an array like [50.5, 30.5, 0.5], or a Leaflet LatLng object.

Third argument in each LatLng point represents point value. Unless max option is specified, values should range between 0.0 and 1.0.

#### Performance

Performance is linked to number of points and cell size:
* 1 - 50 points; Cell size 1 => OK
* 50 - 100; Cell size 1 => Slow

#### ToDo
* Add the option for a bounding box
* Maybe cluster points to increase performance
  * If points in cell then take average for cell
* Define bounding box for which points are used for each cell to increase performance
* Introduce option to do IDW in map units and not in viewport?

#### Changelog

0.0.1 — May 20, 2016

    Initial release.
