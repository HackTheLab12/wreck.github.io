# Wreck.github.io
# UK Wreck Dives — Live Dive-Now Dashboard

A lightweight, responsive dashboard for viewing current wind, wave and estimated tidal conditions at wreck-diving sites around the United Kingdom.

The dashboard combines live weather data with site-specific information to provide an at-a-glance **GO**, **CAUTION** or **NO-GO** indication, alongside a 12-hour conditions outlook.

> [!WARNING]
> This project is an indicative surface-conditions aid only. It is **not a dive plan**, weather guarantee or substitute for local knowledge, formal training, tide tables, skipper advice, gas planning, decompression planning or a complete risk assessment.

## Live Demo

[Open the UK Wreck Dives dashboard](https://hackthelab12.github.io/wreck.github.io/)

## Features

* Live wind speed and wind-gust data for each wreck location
* Live marine wave-height data
* Colour-coded **GO**, **CAUTION** and **NO-GO** assessments
* Hour-by-hour outlook for the next 12 hours
* Suggested first “best” hour within the forecast window
* Approximate tidal phase and time-to-slack estimates
* Spring and neap tide indication
* Wreck sites grouped by UK diving region
* Site depth and recommended experience level
* Links to coordinate-specific forecasts
* Links to external tide information for nearby ports
* Links for further information about each wreck
* Automatic refresh every 15 minutes
* Manual refresh button
* Responsive, dependency-free interface
* Graceful fallback when live weather services are unavailable
* Clear identification of protected or legally restricted **NO DIVE** sites

## How the Dive-Now Rating Works

The dashboard derives its indication from forecast wind gusts and wave height.

| Rating      |  Wind gusts | Wave height |
| ----------- | ----------: | ----------: |
| **GO**      | Up to 16 kn | Up to 0.8 m |
| **CAUTION** | Up to 24 kn | Up to 1.3 m |
| **NO-GO**   | Above 24 kn | Above 1.3 m |

The most restrictive condition determines the displayed rating.

For example, a site with calm wind but waves above 1.3 metres will be marked **NO-GO**.

### Tide-dependent sites

Sites that require or benefit from slack water are never shown as fully **GO** based on weather alone. Their rating is capped at **CAUTION** to highlight the need to verify the actual tidal window.

The displayed tidal phase is an astronomical estimate. Always check authoritative tide tables and obtain current local advice before diving.

### Protected wrecks

Sites marked **NO DIVE** are displayed for awareness only and must not be treated as available dive sites.

## Data Sources

### Weather and waves

Current conditions and the 12-hour outlook are requested directly from Open-Meteo using each site's coordinates.

The application uses:

* Wind speed
* Wind gusts
* Wave height
* Hourly weather forecasts
* Hourly marine forecasts

Open-Meteo is currently accessed without an API key.

### Tides

The application does not download official tide predictions. It estimates tidal phase from lunar transit calculations and a site-specific high-water interval.

This estimate may differ significantly from real local conditions because of:

* Bathymetry
* Coastal geography
* Atmospheric pressure
* Wind direction
* Storm surges
* Local currents
* Site-specific tidal behaviour

Use the external tide links and authoritative local sources for actual dive planning.

## Suggested Future Improvements

* Move wreck information into a separate JSON file
* Add filtering by region, depth and qualification level
* Add sorting by current rating
* Add an interactive map
* Display wind and wave trends as accessible charts
* Add caching and retry handling
* Add data-source timestamps
* Add automated validation for wreck entries
* Add unit and browser tests

## Safety and Legal Disclaimer

Scuba diving and wreck diving are inherently hazardous activities.

The information presented by this project may be incomplete, inaccurate, delayed or unavailable. Forecast conditions may differ from conditions encountered at the launch point, on the surface, during descent or at the wreck.

Never make a go/no-go diving decision using this dashboard alone.

Divers remain responsible for:

* Checking authoritative marine forecasts and tide tables
* Confirming the legal status of a wreck
* Obtaining required permissions
* Selecting an appropriate site for their training and experience
* Using suitable equipment and redundancy
* Planning gas, depth, decompression and contingencies
* Assessing currents, visibility, access and surface conditions
* Following the advice of local dive centres, skippers and authorities
* Diving within the limits of their certification and experience

The maintainers accept no responsibility for injury, loss, damage or legal consequences arising from use of this project.

## Acknowledgements

* [Open-Meteo](https://open-meteo.com/) for weather and marine forecast data
* [yr.no](https://www.yr.no/) for detailed external forecasts
* [tidetime.org](https://www.tidetime.org/) for external tidal information
* The UK diving community and wreck-information sources used to verify site details
