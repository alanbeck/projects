# CUAS Analysis

A geospatial analysis and reporting toolkit for reviewing counter-UAS sensor data. Designed for authorized government and public safety operators, it takes raw drone detection exports and produces operationally useful maps, reports, and analysis products for analyst review.

---

## Problem

Counter-UAS sensors produce raw track data: CSV exports of drone flight paths, signal types, identifiers, and altitudes. Turning that raw data into something an analyst can actually use (a map, a PDF summary, a Google Earth file, a detection report) requires significant manual work across multiple tools. For multi-day operations with many tracks, this becomes a bottleneck.

CUAS Analysis automates the full pipeline from raw export to finished analysis products.

---

## How It Was Built

I defined the requirements, selected the data sources, and validated the output against real data. The code was developed with AI coding assistants (Claude Code) to my specification; I read, modify, and debug it.

Components:

- **Track parser:** Ingests multi-day sensor exports, normalizes altitude references, decodes identifiers, and segments flights by time gap
- **Interactive HTML map:** Multi-layer Folium map with satellite, dark, and topo basemaps; military installation boundaries; FAA airspace overlays; drone paths, pilot positions, and RTL markers per track
- **Static PDF report:** Satellite-basemap report with full track summary table, altitude AGL annotations, and Part 107 violation flags; suitable for case files and interagency sharing
- **Google Earth outputs:** Combined 2D KML/KMZ with all tracks and overlays; per-track 3D KML files with absolute altitude, flight curtains, and time-animated playback
- **Line-of-sight analysis:** Terrain-based visibility analysis using USGS elevation data; produces raster overlays showing which ground areas were potentially observable from each drone's flight path
- **RF range overlays:** Free-space path loss calculations visualized as range rings, for planning and post-incident review
- **Interagency detection report:** Structured text report with flight indicators, proximity flags, and identifier summary for authorized reporting workflows
- **Remote ID lookup:** Serial number resolution against a local database with optional FAA API fallback
- **Browser GUI:** Local web interface for non-CLI operators; handles folder selection, date filtering, track selection, and report generation without terminal access

---

## Key Capabilities

- Processes single-session or multi-day track exports with date and track filtering
- Generates interactive HTML maps, static PDF summaries, and Google Earth KML/KMZ in one pass
- Overlays military installation boundaries, FAA national-security UAS flight restrictions, and airspace classification
- Flags flights that exceed FAA Part 107 altitude limits, operate near protected airspace, or show behavioral indicators of concern
- Line-of-sight analysis quantifies which ground areas were potentially visible from observed drone positions
- Fully offline after initial setup, with no cloud dependency for core analysis

---

## Stack

Python · geopandas · rasterio · folium · matplotlib · contextily · KML/KMZ (stdlib xml.etree)

---

## Intended Use

For use by authorized operators in public safety, defense, and critical infrastructure protection roles. All outputs use indicator language and require analyst validation before any operational or regulatory action.
