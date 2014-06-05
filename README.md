Leaflet.SpotTracker
===================

Real-time tracking from your SPOT unit.

Usage
-----

```JavaScript
L.spotTracker('your_feed_id').addTo(map);
```

```JavaScript
L.spotTracker('your_feed_id', {
	api: 'http://turban.cartodb.com/api/v2/sql',
	url: "{api}?q=SELECT * FROM spot WHERE feed_id='{feed}' ORDER BY timestamp",
	liveUrl: "{api}?q=SELECT * FROM spot WHERE feed_id='{feed}' AND timestamp > {timestamp} ORDER BY timestamp",
	OK: {
		icon: L.MakiMarkers.icon({ icon: 'building',  color: '#145291', size: 'm' }),
		title: 'House'
	},
	CUSTOM: {
		icon: L.MakiMarkers.icon({ icon: 'campsite', color: '#145291', size: 'm' }),
		title: 'Tent'
	},
	onClick: function (evt) {
		console.log("click", evt);
	}			
}).addTo(map);
```