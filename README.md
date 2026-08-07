# Wifi_Switch

A simple ESP32-based Wi-Fi switch project that exposes a small web server to turn a GPIO pin on or off over the network.

## What it does

This sketch runs on an ESP32 and:
- connects to a Wi-Fi network using a predefined SSID and password
- assigns a fixed local IP address
- starts a simple web server on port 80
- controls GPIO 16 through the following endpoints:
  - `/on` → turns the output pin HIGH
  - `/off` → turns the output pin LOW
  - `/` → returns a simple status message

## Hardware

- ESP32 development board based on the board linked here: https://ja.aliexpress.com/i/1005005597999376.html?gatewayAdapt=glo2jpn
- This board does not include a USB port, so it is flashed using the onboard pin headers.
- The onboard relay is used to drive a 51V relay.
- One output load connected to GPIO 16 (defined as `IO_Pin`)
- Power supply for the ESP32

## Features

- Wi-Fi connectivity using `WiFi.h`
- Lightweight web server using `WebServer.h`
- Basic remote control from any device on the same network

## Setup

1. Open the sketch in the Arduino IDE or PlatformIO.
2. Make sure the ESP32 board package is installed.
3. Update the Wi-Fi credentials in the sketch:
   - `ssid`
   - `password`
4. Optionally change the static IP configuration if needed:
   - `local_IP`
   - `gateway`
   - `subnet`
5. Upload the sketch to the ESP32.

## Usage

After the ESP32 connects to Wi-Fi, open the serial monitor to find the assigned IP address.

Then use a browser or any HTTP client to navigate to:
- `http://<ESP32_IP>/` for the status page
- `http://<ESP32_IP>/on` to turn the output ON
- `http://<ESP32_IP>/off` to turn the output OFF

## Notes

- Currently, the device connects to the Wi-Fi network named `txLogiMesh`.
- A static IP address of `192.168.50.139` is configured for the ESP32.
- The current code uses hardcoded Wi-Fi credentials and a static IP, so it is best suited for a personal or test setup.
- GPIO 16 is used as the output pin in this example.

## Example

```text
http://192.168.50.139/
http://192.168.50.139/on
http://192.168.50.139/off
```
