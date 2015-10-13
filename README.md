# lealfet-area-select [![npm version](https://badge.fury.io/js/leaflet-area-select.svg)](https://badge.fury.io/js/leaflet-area-select)

Control to just select an area and provide bbox for it

## [Demo](http://w8r.github.io/leaflet-area-select/example/)

## Include

### Browserify, Webpack

```shell
npm install --save leaflet-area-select
```

```javascript
var SelectArea = require('leaflet-area-select');
// or
import SelectArea from 'leaflet-area-select';
```

### Browser
```html
<script type="text/javascript" src="path/to/Map.SelectArea.min.js"></script>
```

## Usage

Including the handler into the project will automatically add it to the `L.Map`, 
so to enable/disable it you can use methods:

```javascript
let map = new L.Map('map', {
  selectArea: true // will enable it by default
});

// or
map.selectArea.enable();

map.on('areaselected', (e) => {
  console.log(e.bounds.toBBoxString()); // lon, lat, lon, lat
});

// You can restrict selection area like this:
const bounds = map.getBounds().pad(-0.25); // save current map bounds as restriction area
// check restricted area on start and move
map.selectArea.setValidate((layerPoint) => {
  return bounds.contains(
    this._map.layerPointToLatLng(layerPoint)
  );
});

// now switch it off
map.selectArea.setValidate();

```

## License

MIT
