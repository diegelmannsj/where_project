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
```
requests
geopy
gpsd-py3
psutil
netifaces
argcomplete
speedtest-cli
```

Now, install these dependencies using pip:
```bash
pip install -r requirements.txt
```

### 4. Make the Script Executable
```bash
chmod +x ,where
```

### 5. Add to Your PATH (Recommended)
For easy access from any directory, move the script to a location in your system's PATH.
```bash
sudo mv ,where /usr/local/bin/
```

## Usage

Simply run the script by name:
```bash
,where
```

### Options

| Flag | Alias | Description |
| :--- | :--- | :--- |
| `--help` | `-h` | Show the help message and exit. |
| `--version` | `-v` | Show the script's version history and exit. |
| `--list` | `-l` | List all known IPs from history, sorted by last seen. |
| `--speedtest` | `-s` | Perform a network speed test. |
| `--add` | `-A` | Add the current IP to the manual VPN list if not already detected. |
| `--no-gps` | `-G` | Skip all GPS-related functions (live and cached). |
| `--verbose` | `-V` | Enable verbose output for debugging. |
| `--update-vpn-list`| | Force a refresh of the known VPN IP list. |
| `--clear-cache` | | Clear all cached data (GPS, IP history, results, etc.). |
| `--force-refresh`| `-f` | Force a refresh of the GPS location, ignoring the cache. |

## Example Output

```
,where v6.0
Using cached GPS location.

## Live GPS Location
  Latitude:                 37.422000
  Longitude:                -122.084000
  Altitude:                 39.00 meters
  GPS Last Updated:         just now
  Approx. Address:          123 Main Street, Mountain View, Santa Clara County, California, 94043, USA

Fetching your IP details...

## IP-Based Location Details
  Public IP:                1.2.3.4
  Country:                  United States
  Region:                   California
  City:                     Mountain View

## Connection Details
  Latency:                  1.23 ms
  Distance to ISP Server:   15.42 miles
  VPN List Updated:         08/04/2025 04:21:00 PM (0 minutes since)
  VPN/Proxy Detected:       No
  Provider/ISP:             Example ISP Inc.
  Times Seen:               1 (New IP!)
  Last Seen:                Never
  First Seen:               08/04/2025 04:21:54 PM

## Local Network Details

  Interface: wlan0
    Local IP:         192.168.1.123
    wlan0 MAC:        AA:BB:CC:DD:EE:FF
    Gateway:          192.168.1.1
    SSID:             MyHomeWiFi
    BSSID:            FF:EE:DD:CC:BB:AA
    Band:             5 GHz
    Signal:           -45.00 dBm
```

## Configuration
The script stores all of its data in a single JSON file located at `~/.where.json`. This file contains the GPS cache, IP history, VPN lists, and speed test records. You can safely delete this file at any time to reset the script's memory, or use the `--clear-cache` flag.