# MBTA Timings

This started out as an attempt to create an bus timings web page that runs on a Kindle experimental browser, to have as an in-home bus sign on my kitchen door.
It is thus written in the plainest, most archaic JS possible, because turns out if Chrome v1 doesn't support it the Kindle browser doesn't either.

Unfortunately, the Kindle browser also just sucks, and would randomly pop an error after running smoothly for some time.
So that didn't end up working, but it does repurpose as a mobile-first website for consolidating timings for multiple possible stops at a given location.

Usage: `https://jo-room.github.io/mbta/?stops=<comma-delimited list of MBTA stop IDs>&config=<optional JSON config>`

Config options
```json
{
	"title": "Optional page title",

	"string stop ID": {
		"name": "replaces the default MBTA stop name",
		"message": "any message to add in parentheses after the name",
		"filterRoutes": ["array of string route IDs to keep"],
		"maxNumPredictions": 5
	},
	"string stop ID 2": {
		"message": "5min away",
	}
}
```

E.g.: `https://jo-room.github.io/mbta/?stops=191,70075&config={"191":{"message":"5min walking","filterRoutes":["93"]},"70075":{"maxNumPredictions":5}}`

`key=<MBTA API KEY>` is an optional query param, but the API allows 20 requests/min without a key. We are under that threshold at max 2 requests/min (1 initial set up request, then 1 prediction request/min).

<img width="457" alt="image" src="https://github.com/user-attachments/assets/c76b7a31-0f1e-4982-8971-a95ae5f64ed5" />


With the deviations, not sure if `JSON.parse` is Kindle browser legal.
