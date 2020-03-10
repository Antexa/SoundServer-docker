# SoundHoleAutomation

## Services
* balenaSound (AirPlay, Bluetooth, Spotify)
* PiHole
* HomeAssistant
* Eclipse-Mosquitto (MQTT)
* Zigbee2Mqtt

## Environment variables
| Name                     | Purpose                   | Service |
| ------------------------ | ------------------------- | ------- |
| SYSTEM_OUTPUT_VOLUME     | Defaults to 100           | Sound   |
| SPOTIFY_LOGIN            | Spotify username          | Sound   |
| SPOTIFY_PASSWORD         | Spotify password          | Sound   |
| TZ                       | TZ (e.g. "Europe/Berlin") | PiHole  |

## Device variables
| Name                     | Purpose                   | Service |
| ------------------------ | ------------------------- | ------- |
| BLUETOOTH_DEVICE_NAME    | Change device name        | Sound   |
