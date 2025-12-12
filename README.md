# ESP32-CAM withFreeRTOS

Cam project made with ESP32-S and FreeRTOS.

## History

This project is an adaptation of a project made by [DanielStoelzner](https://github.com/DanielStoelzner) adapted to be copiled in Unix Systems and with some custom default values. As [DanielStoelzner](https://github.com/DanielStoelzner) himself has said it's a continuos project:

> A combination of the excellent ESP32 MJPEG Multiclient Streaming Server by arkhipenko ([arkhipenko/esp32-cam-mjpeg-multiclient](https://github.com/arkhipenko/esp32-cam-mjpeg-multiclient)), the default ESP32-CAM Web Server Example sans the Face Detection, and including WebOTA ([scottchiefbaker/ESP-WebOTA](https://github.com/scottchiefbaker/ESP-WebOTA)). Settings are stored in NVS via the Preferences library.

Look at the project that originated this one: [https://github.com/DanielStoelzner/ESP32-CAM-FreeRTOS](https://github.com/DanielStoelzner/ESP32-CAM-FreeRTOS) 

## Handlers

Handler                         | URL                        | Note
------------------------------- | -------------------------- | -------------
Stream                          | `/mjpeg/1`                 |
Capture                         | `/jpg`                     |
Set a variable                  | `/set?var=<var>&val=<val>` |
Get the values of all variables | `/get`                     |
Activate WebOTA                 | `/activatewebota`          | Sets a flag that changes the FreeRTOS-delay to `webota.delay(...)`
Restart                         | `/restart`                 |
Fatory defaults                 | `/reset`                   |
WebOTA                          | `:8080/webota`             |

## Run

### 1. Rename `home_wifi_multi_template.h` to `home_wifi_multi.h`

Inside `src/` is a file with name `home_wifi_multi_template.h`. Rename it to `home_wifi_multi.h`. It is a included file and will contain your network information to allow the device to connect to your router.

From root directory run:

```sh
cp ./src/home_wifi_multi_template.h ./src/home_wifi_multi.h
```

### 2. Edit `home_wifi_multi.h`

Change the values of `SSID1` and `PWD1` to your SSID and WiFi Password.

```c
#define SSID1 "" // <- WiFi name
#define PWD1  "" // <- WiFi password
```

### 3. Compile and run

Is highly recommended to use [PlatformIO](https://platformio.org/) with [VS Code](https://code.visualstudio.com/). Remember to compile at last one time before upload. The Board needs to be on download mode to the upload to work.

### 4. Recommendations

Right after the compilation/upload the board is expected to be in high temperature, at last higher than it will be during normal usage. It will surly affect the performance. Wait a moment before using it to allow the board to dissipate the heat.

## Board settings for Arduino IDE:

- Board: ESP32 Dev Module
- CPU Frequency: 240MHz
- Flash Frequency: 40MHz
- Flash Mode: QIO
- Flash Size: 4MB
- Partition Scheme: Minimal SPIFFS
- PSRAM: Enabled
