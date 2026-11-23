# Here, Now — The Web in Real Time

An illustrated waterfront that changes with current weather data, created by Mariam Riyal for a public API lab.

## Live data

The page uses fetch() to request Open-Meteo's public Forecast API, checks the HTTP response, parses response.json(), validates current values, and updates the DOM. Oakville, Burlington, and Toronto have fixed coordinates; the page does not request a visitor's location.

## Data-driven behaviour

- WMO weather codes choose clear, cloudy, rain, snow, fog, or storm visuals.
- is_day switches between sun/daylight and moon/stars/night.
- wind_speed_10m changes the speed of the illustrated waves. This is a visual metaphor, not a measurement of lake waves.
- Temperature, feels-like temperature, humidity, wind, and daylight populate the weather panel.
- Location selection requests new JSON. A refresh button requests another reading; automatic requests run every ten minutes while the page is visible.
- Celsius/Fahrenheit toggles convert displayed temperature without another API request.
- Pause motion stops the animations. The page also respects reduced-motion preferences.
- An expandable panel shows the latest successful JSON response and exact endpoint for the selected location.

## Loading and failures

Requests use AbortController with a 15-second timeout. Switching locations cancels the previous request, and a request counter prevents late responses from replacing a newer selection. Invalid JSON, incomplete data, and HTTP/network failures produce a visible error. A failed refresh retains a previously successful reading for that location with a warning and its timestamps. With no successful response, the page displays dashes and a neutral illustration, never invented current values.

These are modelled current conditions, not a live station feed or second-by-second stream. Both the provider's valid time and the retrieval time are shown in the America/Toronto timezone. Data older than an hour is flagged. In-memory readings clear on reload.

## Files and tools

The entire application, including CSS, JavaScript, and original inline SVG, is contained in index.html. README.md documents the project. No dependencies, API key, image files, or build step are required. An internet connection and JavaScript are required for live data.

## Credits

Weather data: Open-Meteo, licensed under CC BY 4.0.
- https://open-meteo.com/
- API documentation: https://open-meteo.com/en/docs
- License: https://creativecommons.org/licenses/by/4.0/

All scene artwork is original code-based SVG and represents an illustrative waterfront rather than an exact view or photograph. This is an educational, non-commercial API experiment.
