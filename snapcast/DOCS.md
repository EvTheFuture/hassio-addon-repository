# Snapcast add-on for Home Assistant

This add-on allows you to run a Snapcast server and/or client on Home Assistant to get synchronized audio in multiple rooms.

[Snapcast](https://github.com/badaix/snapcast) is a multiroom client-server audio player developed by [badaix](https://github.com/badaix), where all clients are time synchronized with the server to play perfectly synced audio. It is not a standalone player, but an extension that turns your existing audio player into a Sonos-like multiroom solution.

[Read more about Snapcast here](https://github.com/badaix/snapcast)

## Features
- Synchronized multiroom playback across all connected Snapcast clients.
- Spotify source via librespot (Spotify Connect).
- AirPlay source via shairport-sync, so any audio from an iPhone, iPad or Mac can be streamed into Snapcast.
- Built-in Snapweb web interface for controlling clients and switching sources.
- The last selected source per group is remembered across restarts.

## Installation
- In the Home Assistant Apps Store, add the repository: https://github.com/EvTheFuture/hassio-addon-repository
- Search for Snapcast and install the app.
- Start the app. On first start it builds the image, which can take a while on slower hardware.

## Web interface
When `enable_web` is on, the Snapweb interface is available on port 1780. Use the "Open Web UI" button on the add-on page, or browse to `http://<your-ha-ip>:1780/` directly.

Snapcast plays one source per client group at a time and does not switch automatically. To hear a given source, open Snapweb and set the group's source to the stream you want (for example AirPlay or Spotify). The selection is remembered across restarts.

## Streaming from an Apple device (AirPlay)
With `enable_stream_airplay` on, the add-on advertises an AirPlay receiver on the network. Pick it from the AirPlay output picker on your iPhone, iPad or Mac and start playback, then set a client group's source to the AirPlay stream in Snapweb.

Discovery relies on mDNS, so the add-on runs on the host network. If the receiver does not appear on your device, make sure no other mDNS responder is conflicting on the network.

## Configuration
The following configuration options exist.

### Server
- `enable`: true|false. Enable the Snapcast server.
- `enable_web`: true|false. Enable the Snapweb web interface on port 1780.
- `enable_stream_librespot`: true|false. Enable the Spotify (librespot) source.
- `librespot_name`: The name of the Spotify stream as shown in Snapcast.
- `librespot_device_name`: The name to present in Spotify Connect.
- `librespot_initial_volume`: Initial volume, 0-100 percent.
- `librespot_bitrate`: Bitrate, one of 96, 160 or 320.
- `librespot_normalize`: true|false. Use Spotify volume normalization.
- `librespot_killall`: true|false. Terminate any other running librespot instances on start.
- `librespot_disable_audio_cache`: true|false. Do not cache downloaded audio to disk.
- `librespot_params`: Value passed to the librespot source params option.
- `librespot_extra_params`: Any extra parameters to send to librespot.
- `enable_stream_airplay`: true|false. Enable the AirPlay (shairport-sync) source.
- `airplay_name`: The name of the AirPlay stream as shown in Snapcast.
- `airplay_device_name`: The name shown in the AirPlay picker on your Apple device.
- `airplay_port`: RTSP listening port for shairport-sync. Default is 5000.
- `custom_streams`: Additional raw snapserver source lines, one per stream.

### Client
- `enable`: true|false. Enable the Snapcast client.
- `host`: Address of the Snapcast server to connect to.
- `port`: Control port of the Snapcast server. Leave empty for the default.
- `extra_params`: Any extra parameters to use when starting the client process.

## Support my work
[![buy-me-a-coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/EvTheFuture)
