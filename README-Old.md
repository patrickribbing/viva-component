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
The region can be found at Sjöfartsverket (https://geokatalog.sjofartsverket.se/kartvisarefyren/), select a station and view the "stationsid" parameter. Some examples: Vinga/Göteborg is 114 and Gubben/Sundsvall is 153. scan_interval is the number of seconds between requests to ViVa, please do not poll too often. The selected station must have a value for "Medelvind", otherwise the component will not receive any data.

If you want to make an automation, e.g. a warning if the wind is high, do something like the following in ```automations.yaml```:
```
- id: '1585597720358'
  alias: Notify if high wind
  trigger:
    platform: numeric_state
    entity_id: sensor.Vind
    above: 18
  action:
    service: notify.mailsender
    data:
      title: Warning!
      message: The wind is now {{ states('sensor.Vind') }} m/s.  
```
