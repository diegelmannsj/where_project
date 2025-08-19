# ,where - Network & Location Analysis Tool

`,where` is a comprehensive command-line tool for network and location analysis. It gathers information about your public and local network connections, performs speed tests, detects VPNs, and can even integrate with a `gpsd` service for precise location tracking.

## Key Features

- **Public IP Geolocation:** Fetches your public IP and provides details like country, city, and ISP using the ip-api.com service.
- **Local Network Details:** Displays information about your local network interfaces, including IP addresses, MAC addresses, and Wi-Fi details (SSID, BSSID, signal strength).
- **Network Speed Testing:** Measures your download/upload speeds and ping latency using `speedtest-cli`. It logs results and tracks personal bests for each IP.
- **VPN/Proxy Detection:** Uses multiple methods to identify VPNs: API-based detection, a crowdsourced list of VPN IP ranges, and a manual list you can manage.
- **GPSD Integration:** Connects to a local `gpsd` service to get live, high-precision GPS coordinates and reverse-geocodes them to a physical address.
- **Persistent History:** Remembers every public IP address you've used, tracking when and how many times each was seen.
- **Caching:** Caches location and VPN results to improve performance and avoid excessive API calls.

## Installation & Dependencies

1.  **Clone the repository or download the script.**
2.  **Make the script executable:**
    ```bash
    chmod +x ,where
    ```
3.  **Install the required Python libraries.** The script has core dependencies and several optional ones for enabling full functionality.

    **Core Dependency:**
    ```bash
    pip install requests
    ```

    **Optional Dependencies:**
    ```bash
    # For GPS functionality
    pip install gpsd-py3

    # For reverse geocoding GPS coordinates to an address
    pip install geopy

    # For local network interface details
    pip install psutil netifaces

    # For network speed tests
    pip install speedtest-cli

    # For command-line tab completion
    pip install argcomplete
    ```

## Usage

The script is invoked from the command line with various flags to control its behavior.

```bash
./,where [OPTIONS]
```

### Main Options

| Flag                | Alias | Description                                                      |
| ------------------- | ----- | ---------------------------------------------------------------- |
| `--speedtest`       | `-s`  | Perform a network speed test.                                    |
| `--list`            | `-l`  | List all known IPs from history, sorted by last seen.            |
| `--fastest`         |       | List known IPs sorted by fastest download speed (implies `--list`).|
| `--quickest_dev`    |       | Display active WiFi devices sorted by band and bit rate.         |
| `--all`             | `-a`  | Show details for all local network interfaces.                   |
| `--source <iface>`  |       | Specify a source interface for tests (e.g., `wlan0`, `eth0`).    |

### GPS Options

| Flag              | Alias | Description                                   |
| ----------------- | ----- | --------------------------------------------- |
| `--no-gps`        | `-G`  | Skip all GPS-related functions.               |
| `--force-refresh` | `-f`  | Force a new GPS reading, ignoring the cache.  |

### VPN & Data Management

| Flag                | Alias | Description                                                  |
| ------------------- | ----- | ------------------------------------------------------------ |
| `--update-vpn-list` |       | Force a refresh of the known VPN IP list from the web.       |
| `--add`             | `-A`  | Add the current IP to the manual VPN list if not detected.   |
| `--clear-cache`     |       | Deletes all cached data, history, and settings.              |

### Other Options

| Flag        | Alias | Description                  |
| ----------- | ----- | ---------------------------- |
| `--verbose` | `-V`  | Enable verbose output for debugging. |
| `--version` | `-v`  | Show the script's version history.   |


## Example Usage

- **Get a standard report:**
  ```bash
  ./,where
  ```

- **Run a speed test using a specific Wi-Fi interface:**
  ```bash
  ./,where --speedtest --source wlan0
  ```

- **See your IP history, sorted by the fastest speeds recorded:**
  ```bash
  ./,where --fastest
  ```

- **Manually flag your current IP as a VPN:**
  ```bash
  ./,where --add
  ```

## Configuration

The script stores its cache and history in a JSON file located at `~/.where.json`. This file is created automatically on the first run. You can clear all stored data by running the script with the `--clear-cache` flag.