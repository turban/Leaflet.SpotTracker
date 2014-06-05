Leaflet.SpotTracker
===================

Real-time tracking from your SPOT unit.

Requires
--------
[Leaflet](http://leafletjs.com/)

[reqwest](https://github.com/ded/reqwest)

Usage
-----

Load data from [SPOT API](http://faq.findmespot.com/index.php?action=showEntry&data=69):
```JavaScript
L.spotTracker('your_feed_id').addTo(map);
```

Load data from [CartoDB](http://blog.thematicmapping.org/2014/06/syncing-data-from-your-spot-satellite.html):
```JavaScript
L.spotTracker('your_feed_id', {
	api: 'http://turban.cartodb.com/api/v2/sql',
	url: "{api}?q=SELECT * FROM spot WHERE feed_id='{feed}' ORDER BY timestamp",
	liveUrl: "{api}?q=SELECT * FROM spot WHERE feed_id='{feed}' AND timestamp > {timestamp} ORDER BY timestamp"
}).addTo(map);
```

Live marker CSS:
```CSS
.leaflet-marker-live {
	-webkit-animation: pulse 2s ease-out;
	animation: pulse 2s ease-out;
	-webkit-animation-iteration-count: infinite;
	animation-iteration-count: infinite;
}
@-webkit-keyframes pulse {
	from { stroke-width: 15; stroke-opacity: 1; }
	to { stroke-width: 50; stroke-opacity: 0; }
}
@keyframes pulse {
	from { stroke-width: 15; stroke-opacity: 1; }
	to { stroke-width: 50; stroke-opacity: 0; }
}
```
