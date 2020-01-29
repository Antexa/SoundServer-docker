# SoundHoleAutomation

## Services
* balenaSound (AirPlay, Bluetooth, Spotify)
* PiHole
* WireGuard
* HomeAssistant

## Instructions
```
git submodule init
git submodule update
```

## Environment variables
| Name                     | Purpose                   | Service |
| ------------------------ | ------------------------- | ------- |
| DISABLE_MULTI_ROOM       | Disables multiroom audio  | Sound   |
| SYSTEM_OUTPUT_VOLUME     | Defaults to 100           | Sound   |
| CONNECTION_NOTIFY_VOLUME | Defaults to 100           | Sound   |
| BLUETOOTH_PIN_CODE       | Legacy pairing PIN        | Sound   |
| BLUETOOTH_SCRIPTS        | Set to "true" to enable   | Sound   |
| SPOTIFY_LOGIN            | Spotify username          | Sound   |
| SPOTIFY_PASSWORD         | Spotify password          | Sound   |
| TZ                       | TZ (e.g. "Europe/Berlin") | PiHole  |
| DNS1                     | e.g. "127.0.0.1#5053"     | PiHole  |
| DNS2                     | e.g. "127.0.0.1#5053"     | PiHole  |
| DNSMASQ_LISTENING        | Listening interface "eth0"| PiHole  |
| INTERFACE                | same as above             | PiHole  |
| WEBPASSWORD              | Webif password (!set OOB!)| PiHole  |

## Device variables
| Name                     | Purpose                   | Service |
| ------------------------ | ------------------------- | ------- |
| BLUETOOTH_DEVICE_NAME    | Change device name        | Sound   |
