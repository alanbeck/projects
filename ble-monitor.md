# BLE Monitor

An Android application for passive Bluetooth and WiFi surveillance detection. The app continuously scans the RF environment and alerts the user to tracking devices, persistent followers across locations, and known surveillance hardware, with no network connection, no backend, and no data leaving the device.

---

## Problem

Commercial tracking devices and physical surveillance are increasingly difficult to detect without specialized equipment. Most people have no way to know whether an AirTag has been placed on their vehicle, whether a device is following them across locations, or whether a room contains a hidden WiFi camera.

BLE Monitor puts that detection capability on any Android phone.

---

## How It Was Built

I defined the requirements, selected the data sources, and validated the output against real data. The code was developed with AI coding assistants (Claude Code) to my specification; I read, modify, and debug it.

Components:

- **BLE scanning engine:** Foreground service that continuously scans nearby Bluetooth devices, surviving screen lock and backgrounding; extracts and normalizes advertisement data across device types
- **Tracker detection:** Signature-based identification of commercial tracking devices; detects known trackers immediately on first sighting without requiring location history; parses device state (offline, separated) from service data where available
- **Persistent follower detection:** GPS-based location clustering that identifies devices appearing across multiple distinct locations over time; applies a scored threat model incorporating timing patterns and behavioral indicators
- **Coordinated surveillance detection:** Identifies pairs of devices that consistently appear together across locations, suggesting a coordinated surveillance operation
- **WiFi analysis engine:** Scans nearby access points and classifies them by threat level using SSID pattern matching and vendor identification from hardware addresses; detects dedicated surveillance camera hardware and suspicious hidden networks
- **Threat UI:** Tabbed interface showing live threat summary, tracker details, follower sighting timelines, and full WiFi AP inventory; real-time alert banner for active threats
- **Whitelist management:** Persistent friendly-device registry that excludes known-safe devices from threat analysis

---

## Key Capabilities

- Detects all major commercial BLE tracking devices
- Flags devices that follow a user across three or more distinct GPS locations
- Identifies behavioral patterns associated with professional surveillance
- Detects WiFi-connected surveillance cameras by manufacturer and network name
- Estimates crowd density from BLE device count, which provides context for interpreting follower signals
- Fully offline: no network connection, no backend, no data transmitted

---

## Stack

React 18 · Vite · Capacitor 8 · Android (Java/Kotlin native plugin) · `@capacitor-community/bluetooth-le` · `@capacitor/geolocation`

---

## Legal

For authorized personal security and counter-surveillance use. All scanning is passive. The app reads voluntarily broadcast RF emissions and performs no active probing, injection, or network association.
