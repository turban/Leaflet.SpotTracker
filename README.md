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

Options
-------

| Option       | Type           | Default                                                                                             | Description                                    |
| ------------ | -------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| api          | String         | 'https://api.findmespot.com/spot-main-web/consumer/rest-api/2.0/public/feed/'                       | Data API.                                      |
| url          | String         | '{api}{feed}/message.json'                                                                          | URL to data feed.                              |
| live         | Boolean        | true                                                                                                | Allow live updates.                            |
| liveUrl      | String         | '{api}{feed}/message.json?startDate={startDate}'                                                    | URL to update feed.                            |
| liveInterval | Number         | 10                                                                                                  | Time between each live update in minutes.      |
| liveMarker   | Object         | { radius: 5, color: 'orange', fillColor: '#333', fillOpacity: 1, className: 'leaflet-marker-live' } | Live marker style.                             |
| focus        | Boolean/Number | false                                                                                               | Add zoom value to focus map to last position.  |
| fitBounds    | Boolean        | true                                                                                                | Zoom the map to data bounds.                   |
| marker       | Object         | { radius: 5, color: '#333', fillOpacity: 1, stroke: false }                                         | Marker style.                                  |
| line         | Object         | { color: '#333', weight: 3, dashArray: '5,5' }                                                      | Line style.                                    |
| show         | Object         | { 'UNLIMITED-TRACK': 12, 'OK': 14, 'CUSTOM': 14 }                                                   | When to show message types (zoom value).       |


CSS
---

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
