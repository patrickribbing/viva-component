# viva-component
A custom component to Home Assistant that read Swedish weather stations (ViVa). The component fetch the average wind data for a selected station.

## Installation
Inside the configuration folder in Home Assistant create folder ```custom_components``` if it's not already created. Create a new folder, e.g. ```viva``` in that folder and copy the files to the folder.

## Usage
Set up the sensor using yaml in the configuration file (```configuration.yaml```).
```
sensor vind:
  platform: viva
  name: Vind
  region: 114
  scan_interval: 60
```
The region can be found at Sjöfartsverket (http://www.sjofartsverket.se/sv/Snabblankar/Kartviewers/ViVa/), select a station and view the stationsid parameter. Some examples: Vinga/Göteborg is 114 and Gubben/Sundsvall is 153. scan_interval is the number of seconds between requests to ViVa, please do not poll too often.