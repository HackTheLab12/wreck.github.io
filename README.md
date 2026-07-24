# UK Dive Sites

A responsive, browser-based planning guide for scuba diving around the United Kingdom.

The site combines live weather and marine forecasts with a curated database of UK sea wrecks, inland quarries, lakes and wild-diving locations. It provides quick condition summaries, interactive mapping and detailed site information without requiring an account, API key or build process.

## Live Site

**[Open UK Dive Sites](https://hackthelab12.github.io/wreck.github.io/)**

## What’s Included

The project is split into four main sections:

* **Home** — overview and navigation
* **Wreck Dives** — live conditions for 30 UK sea wrecks
* **Live Map** — map-based wreck exploration with condition-coloured markers
* **Inland Dives** — 15 UK quarries, lakes and wild-diving locations

Individual wrecks also have their own detailed dossier pages.

> [!WARNING]
> This site is a planning aid only. It is not a dive plan, weather guarantee, legal authority or substitute for training, local knowledge, tide tables, skipper advice, gas planning, decompression planning or a full risk assessment.

## Features

### Wreck dashboard

* 30 sea-wreck locations around the UK
* Live wind speed and wind-gust data
* Live wave-height data
* Green, amber and red **Dive Now?** indications
* 12-hour hourly conditions outlook
* Suggested first best forecast window
* Sunrise and sunset context
* Approximate tidal state and time to slack
* Spring, neap and mid-range tide indication
* Wrecks grouped by region
* Depth and qualification guidance
* Links to detailed wreck dossiers
* Coordinate-specific external forecasts
* Links to nearby authoritative tide information
* Automatic refresh every 15 minutes
* Manual refresh control
* Metric and imperial display options

### Interactive wreck map

* All included wrecks displayed geographically
* Markers coloured by current Dive-Now status
* Current wind, gust and wave information
* Links from each marker to the wreck’s detailed page
* Graceful fallback if map tiles or weather data are unavailable

### Wreck detail pages

Each wreck dossier may include:

* Wreck type and year lost
* Length
* Minimum and maximum depth
* Suggested gas
* Recommended qualification level
* Typical water-temperature range
* Best diving season
* Current strength
* Entry and tidal guidance
* Typical visibility
* Legal or protected status
* Launch and boat access information
* Nearest hyperbaric chamber information
* Travel information from Halifax
* Nearby gas-fill options
* Site-specific notes
* Live surface conditions
* External weather and tide links

Protected wrecks and controlled sites are clearly identified as **NO DIVE**.

### Inland dive guide

* 15 quarries, lakes and wild-diving locations
* Current access and closure information
* 13 currently open locations in the present dataset
* Sites ordered by distance from Halifax
* Live air temperature and weather
* Maximum-depth information
* Typical water-temperature guidance
* Facility information
* On-site gas-fill availability
* Booking and membership requirements
* Clear badges for:

  * Closed sites
  * Members-only locations
  * Wild-diving locations
  * Sites without facilities

Always verify opening times, bookings, membership rules and access restrictions with the site operator before travelling.

## Dive-Now Rating

The wreck dashboard calculates an indicative surface-condition rating from wind gusts and wave height.

| Rating      |  Wind gusts | Wave height |
| ----------- | ----------: | ----------: |
| **GO**      | Up to 16 kn | Up to 0.8 m |
| **CAUTION** | Up to 24 kn | Up to 1.3 m |
| **NO-GO**   | Above 24 kn | Above 1.3 m |

The most restrictive measurement determines the result.

For example, calm wind combined with waves above 1.3 metres results in a **NO-GO** indication.

The underlying thresholds are always calculated in knots and metres. Displayed measurements can be switched between:

* Knots and miles per hour
* Metres and feet

Unit preferences are saved locally in the browser.

### Tide-dependent wrecks

Wrecks that require or benefit from slack water are capped at **CAUTION**, even when the wind and wave forecast would otherwise produce a **GO** result.

The dashboard’s tide phase is an astronomical estimate based on lunar transit and a site-specific high-water interval. It is not an official local tide prediction.

Always check authoritative tide tables and obtain current local advice.

### Protected wrecks

Locations marked **NO DIVE** are shown for information and awareness only.

Legal restrictions may prohibit diving, anchoring, interference, entry or removal of artefacts. Divers are responsible for confirming a site’s current legal status before planning a visit.

## Data Sources

### Weather

The application retrieves coordinate-based weather information from the Open-Meteo Forecast API.

Data used includes:

* Current wind speed
* Current wind gusts
* Weather condition codes
* Hourly wind forecasts
* Sunrise and sunset

### Marine conditions

The Open-Meteo Marine API provides:

* Current wave height
* Current swell-wave height
* Hourly wave-height forecasts

Open-Meteo is currently accessed without an API key.

### Tides

The project estimates the broad tidal phase locally in JavaScript.

External links to [tidetime.org](https://www.tidetime.org/) are provided for nearby port predictions.

### External forecasts

Detailed coordinate-specific weather links open forecasts on [yr.no](https://www.yr.no/).

## Technology

The project intentionally uses a simple static architecture:

* HTML5
* CSS3
* Vanilla JavaScript
* Open-Meteo Forecast API
* Open-Meteo Marine API
* Browser `localStorage`
* Interactive web mapping
* GitHub Pages
* GitHub Actions

There is:

* No package manager
* No JavaScript framework
* No server-side application
* No database server
* No API key requirement
* No compilation or build step for local development

## Project Structure

```text
wreck.github.io/
├── .github/
│   └── workflows/
│       └── jekyll-gh-pages.yml
├── data.js
├── index.html
├── inland.html
├── map.html
├── README.md
├── style.css
├── wreck.html
└── wrecks.html
```

### File responsibilities

| File                                    | Purpose                                          |
| --------------------------------------- | ------------------------------------------------ |
| `index.html`                            | Main landing page and section navigation         |
| `wrecks.html`                           | Live wreck-conditions dashboard                  |
| `wreck.html`                            | Reusable individual wreck-detail page            |
| `map.html`                              | Interactive map of wreck locations               |
| `inland.html`                           | Inland quarry, lake and wild-site guide          |
| `data.js`                               | Shared wreck data, settings and helper functions |
| `style.css`                             | Shared visual styling and responsive layout      |
| `.github/workflows/jekyll-gh-pages.yml` | GitHub Pages deployment workflow                 |

The wreck data file is marked as auto-generated from a separate `UK_Wreck_Dives_Database.xlsx` source dataset.

Because this is a static project, deployment does not require secrets or environment variables for the weather APIs.

## Safety and Legal Disclaimer

Scuba diving, inland diving and wreck diving are inherently hazardous.

Information displayed by this project may be inaccurate, incomplete, outdated, delayed or unavailable. Forecast conditions may differ from the conditions encountered at the Dive site, on the surface, during descent or at depth.

Never make a diving decision using this site alone.

Divers remain responsible for:

* Checking authoritative marine forecasts
* Checking official tide tables
* Confirming opening and booking arrangements
* Confirming access and parking restrictions
* Confirming the legal status of a wreck
* Obtaining any required permissions
* Selecting sites appropriate to their training
* Planning gas and decompression
* Assessing currents, visibility and temperature
* Carrying suitable equipment and redundancy
* Following local operator and skipper advice
* Diving within certification and experience limits

The presence of a green **GO** indicator does not mean that a dive is safe or suitable.

The maintainers accept no responsibility for injury, loss, damage, missed bookings, access problems or legal consequences arising from use of this project.

## Acknowledgements

* [Open-Meteo](https://open-meteo.com/) for weather and marine forecast data
* [yr.no](https://www.yr.no/) for external coordinate-based forecasts
* [tidetime.org](https://www.tidetime.org/) for nearby port tide information
* UK dive operators, clubs and community sources used to research and verify locations
