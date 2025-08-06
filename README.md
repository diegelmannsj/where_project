1. Title

Start the file with the main title on the first line:
# ,where v7.5

2. Summary

On a new line, write a short, one-sentence description of the script.

Example: "A command-line utility to display public and local network and location information."

3. Features Section

Create a "Features" heading: ## Features

Below it, create a bulleted list. Each feature should be a new bullet point (*).

Make sure to list the features we've discussed:

Public IP details (ISP, location)

Local network info (IP, MAC, vendor)

WiFi details (SSID, band, signal)

GPS integration (gpsd)

VPN/Proxy detection

Connection history (--list)

Network speed test (--speedtest)

Export/Import of IP history

Interactive mode (-i)

4. Installation Section

Create an "Installation" heading: ## Installation

Mention the prerequisites: Python 3, pip, and gpsd.

Mention that the Python dependencies (requests, geopy, psutil, etc.) should be in a requirements.txt file and installed with pip install -r requirements.txt.

Include the command to make the script executable: chmod +x ,where

5. Usage Section

Create a "Usage" heading: ## Usage

Show the basic command: ,where

Add an "Options" subheading: ### Options

List the most important command-line flags and what they do (e.g., -v, -l, -s, -G, -c, -f). You can do this as a simple bulleted list to keep it easy.

6. Configuration Section

Create a "Configuration" heading: ## Configuration

Add a sentence explaining that the script stores its cache and history in the ~/.where.json file.

7. License Section

Create a "License" heading: ## License

State that the project is under the MIT License.
