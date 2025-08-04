# ,where

**Version:** 6.0

A comprehensive command-line network and location information utility for Linux. This script provides a detailed overview of your system's current public and local network status, geolocation data, and connection history.

## Features

* **Public IP Details**: Fetches and displays your public IP address, ISP, and geographic location (City, Region, Country).
* **Local Network Info**: Lists all active network interfaces, showing their local IP address, MAC address, and default gateway.
* **Wi-Fi Details**: For wireless connections, it displays the SSID, BSSID, signal strength, and network band (2.4/5/6 GHz).
* **GPS Integration**: Connects to a local `gpsd` service to provide live, high-precision GPS coordinates, altitude, and a reverse-geocoded approximate street address.
* **Advanced VPN Detection**: Uses a dual-method approach, checking against a hosting provider API and a frequently updated list of known VPN IP ranges.
* **Connection History**: Automatically logs every public IP address you connect through. You can list this history, sorted by last seen, with the `-l`/`--list` flag.
* **Network Speed Test**: Includes an optional, secure (HTTPS) speed test to measure your current download/upload speeds and ping, and keeps a record of the fastest test for each server.
* **Highly Configurable**: Provides numerous command-line flags to control output, clear caches, and manage the IP history.

## Installation

### 1. Prerequisites
Make sure you have Python 3 and pip installed. The `gpsd` service is required for the live GPS feature.

### 2. Get the Script
Save the latest version of the script to a file named `,where`.

### 3. Install Dependencies
Save the following content into a file named `requirements.txt` in the same directory as the script.

**`requirements.txt`**
