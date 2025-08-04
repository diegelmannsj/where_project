,where
Version: 5.8

A comprehensive command-line network and location information utility for Linux. This script provides a detailed overview of your system's current public and local network status, geolocation data, and connection history.

Features
Public IP Details: Fetches and displays your public IP address, ISP, and geographic location (City, Region, Country).

Advanced VPN Detection: Uses a dual-method approach to detect VPNs/proxies. It first checks against a known hosting provider API and then cross-references against a frequently updated, comprehensive list of VPN IP ranges.

Local Network Info: Lists all active network interfaces, showing their local IP address, MAC address, and default gateway.

Wireless Details: For Wi-Fi connections, it displays the SSID, BSSID, signal strength, and network band (2.4/5/6 GHz).

GPS Integration: Connects to a local gpsd service to provide live, high-precision GPS coordinates, altitude, and a reverse-geocoded approximate street address.

Connection History: Automatically logs every public IP address you connect through. You can list this history, sorted by last seen, to track your connections over time.

Network Speed Test: Includes an optional, secure (HTTPS) speed test to measure your current download/upload speeds and ping.

Highly Configurable: Provides numerous command-line flags to control output, clear caches, and manage the IP history.

Installation
1. Prerequisites
Make sure you have Python 3 and pip installed. You will also need git if you are cloning the repository. The gpsd service is required for the live GPS feature.

2. Get the Script
Save the latest version of the script to a file named ,where.

3. Install Dependencies
The script relies on several external Python libraries. Save the following content into a file named requirements.txt in the same directory as the script.

requirements.txt

requests
geopy
gpsd-py3
psutil
netifaces
argcomplete
speedtest-cli
Now, install these dependencies using pip:

Bash

pip install -r requirements.txt
4. Make the Script Executable
Bash

chmod +x ,where
5. Add to Your PATH (Recommended)
For easy access, move the script to a directory in your system's PATH.

Bash

mv ,where ~/bin/
# Or another directory like /usr/local/bin
# sudo mv ,where /usr/local/bin/
Usage
Simply run the script by name.

Bash

,where
Options
Flag	Alias	Description
--help	-h	Show the help message and exit.
--version	-v	Show the script's version history and exit.
--list	-l	List all known IPs from history, sorted by last seen.
--speedtest	-s	Perform a network speed test.
--add	-A	Add the current IP to the manual VPN list if not already detected.
--no-gps	-G	Skip all GPS-related functions (live and cached).
--verbose	-V	Enable verbose output for debugging.
--update-vpn-list		Force a refresh of the known VPN IP list.
--clear-cache		Clear all cached data (GPS, IP history, results, etc.).
--force-refresh	-f	Force a refresh of the GPS location, ignoring the cache.

Export to Sheets
Example Output
,where v5.8
Using cached GPS location.

## Live GPS Location
  Latitude:                 37.457558
  Longitude:                -77.600796
  Altitude:                 100.00 meters
  GPS Last Updated:         18 hours ago
  Approx. Address:          2236, Providence Creek Road, Chesterfield County, Virginia, 23236, United States

Fetching your IP details...

## IP-Based Location Details
  Public IP:                96.228.41.193
  Country:                  United States
  Region:                   Virginia
  City:                     Richmond

## Connection Details
  Latency:                  3.71 ms
  Distance to ISP Server:   1.19 miles
  VPN List Updated:         08/03/2025 01:18:27 AM (18 hours since)
  VPN/Proxy Detected:       No
  Provider/ISP:             Verizon Business
  Times Seen:               5
  Last Seen:                08/03/2025 07:26:46 PM (0 minutes since)
  First Seen:               08/03/2025 07:20:34 PM (6 minutes since)

## Local Network Details

  Interface: wlan0
    Local IP:         192.168.10.182
    wlan0 MAC:        2c:cf:67:7e:11:4b
    Gateway:          192.168.10.1
    SSID:             acMarley
    BSSID:            be:95:5d:24:7a:2e
    Band:             2.4 GHz
    Signal:           -55.00 dBm
Configuration
The script stores all of its data in a single JSON file located at ~/.where.json. This file contains:

The GPS location cache.

The history of all seen IPs (ip_tally).

The cached list of known VPN IP ranges.

The cached results of previous VPN checks.

Speed test history and records.

You can safely delete this file at any time to reset the script's memory, or use the --clear-cache flag.
