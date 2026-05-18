# city-temperature-tracker

Automated weather data collection workflow built with n8n. The project periodically fetches live weather data from the OpenWeatherMap API, extracts normalized temperature information, and stores timestamped readings in a GitHub-hosted JSON dataset.


## How it works

### 1. n8n Schedule Trigger

The workflow runs automatically at a configured interval (daily currently).

### 2. Weather Collection

The workflow calls the OpenWeatherMap API for a target city and retrieves current weather conditions and temperature data.

### 3. Data Transformation

The workflow extracts and normalizes only the required fields:

* UTC timestamp
* location
* temperature
* measurement unit

Example:

```json
{
  "date": "2026-05-18T03:00:00.000Z",
  "location": "Cluj-Napoca",
  "temperature": 10.71,
  "unit": "celsius"
}
```

### 4. GitHub Storage

The n8n workflow:

1. Reads the existing `temperatures.json`
2. Appends the new weather reading
3. Commits the updated JSON file back to GitHub automatically

### 5. Static Dashboard

GitHub Pages serves a lightweight frontend dashboard.

The frontend loads live JSON data directly from GitHub and displays:

* historical readings
* temperature statistics
* temperature evolution graph
* dynamic location filtering
* time-range filtering (week / month / year / all)


## Tech Stack

* n8n
* OpenWeatherMap API
* GitHub REST API
* GitHub Pages
* Vanilla HTML/CSS/JavaScript

## Features

* Automated weather data collection
* Lightweight JSON-based storage
* Static dashboard deployment
* Dynamic filtering by location
* Historical temperature visualization
* No frontend frameworks required

## Goals

This project demonstrates:

* lightweight automated time-series data collection
* workflow automation with n8n
* GitHub as a simple JSON datastore, static frontend visualization without frameworks
* automated time-series data collection

## Live Repository

[https://github.com/botacatalin/city-temperature-tracker](https://github.com/botacatalin/city-temperature-tracker)
