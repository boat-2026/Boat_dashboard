# Charleston Boating Dashboard

**[Live Dashboard](https://boat-2026.github.io/Boat_dashboard/)**

A single-page weather and tide dashboard for Charleston Harbor, built for quick go/no-go boating decisions.

## What It Does

Opens in any browser and pulls live data to display:

- **Boating Score (1–10)** — weighted composite of wind, rain, visibility, and temperature
- **"When to Go" planner** — scores upcoming time blocks across 3 days so you can pick the best window
- **Tides** — current level, rising/falling direction, hi/lo schedule, and an intraday chart (NOAA Station 8665530)
- **Wind** — speed, gusts, compass direction, and Beaufort scale
- **Weather** — temperature, humidity, rain chance, visibility, and conditions
- **Sun** — sunrise/sunset times, daylight duration, and a sun-position arc
- **3-Day Forecast** — scrollable daily cards with highs, lows, wind, and rain probability

Data auto-refreshes every 15 minutes. Cached in `localStorage` for offline fallback.

## Tech

Zero dependencies, zero build step — just a single `Boating.html` file.

- **Tides**: [NOAA CO-OPS API](https://tidesandcurrents.noaa.gov/api/)
- **Weather**: [Open-Meteo API](https://open-meteo.com/) (no key required)
- **Fonts**: DM Sans + Libre Baskerville via Google Fonts
- **PWA-ready**: includes `apple-mobile-web-app` meta tags for home-screen install on iOS

## Usage

```bash
# just open it
open Boating.html
```

Or drop it on any static host (GitHub Pages, Netlify, S3, etc.).

## Scoring Logic

The boating score uses these weights:

| Factor      | Weight | Notes                                    |
|-------------|--------|------------------------------------------|
| Wind        | 40%    | Tuned for small boats (Gheenoe, skiff)   |
| Rain        | 25%    | Thunderstorm codes force score to 1      |
| Visibility  | 20%    | Harbor navigation safety                 |
| Temperature | 15%    | Comfort sweet spot: 65–85°F             |

## Customization

Edit the constants at the top of the `<script>` block:

```js
const LAT = 32.7766;       // your latitude
const LON = -79.9309;      // your longitude
const NOAA_STATION = '8665530';  // your nearest NOAA tide station
```

Find your NOAA station ID at [tidesandcurrents.noaa.gov](https://tidesandcurrents.noaa.gov/).

## License

MIT
