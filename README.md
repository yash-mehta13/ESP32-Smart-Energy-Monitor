# ESP32-Smart-Energy-Monitor
The ESP32-powered IoT system provides real-time monitoring of energy consumption. It uses FreeRTOS to monitor voltage, current, and power using the PZEM-004T module. Data is transferred to the Blynk platform through WhatsApp notifications and LED indications if there is any excess in daily or monthly usage.

# Smart Energy Monitoring System using ESP32 & IoT

## Overview
A low-cost, real-time IoT energy monitoring system designed to track voltage, current, active power, and energy consumption. The system uses an ESP32 microcontroller with FreeRTOS to handle simultaneous sensor polling and cloud communication, delivering real-time updates via the Blynk IoT platform.

## Features
* **Dual-Core Processing (FreeRTOS):** Core 1 handles real-time sensor polling while Core 0 manages Wi-Fi and Blynk cloud communications.
* **High Voltage Safety:** Utilizes non-invasive CT coils for AC current measurement.
* **Local Display:** Real-time metrics displayed on a 16x2 I2C LCD.
* **Smart Alerts:** Automated visual alerts (LEDs) and push notifications via Blynk for high-power spikes (configurable threshold).

## Hardware Components
* ESP32 Dev Module (Wi-Fi + Bluetooth enabled)
* PZEM-004T v3.0 AC Sensor Module (UART)
* 16x2 I2C LCD Display 
* 5V Power Supply (Micro USB or Hi-Link AC to DC converter)
* LEDs (Green for Normal, Red for Alert)

## Circuit Connections
**PZEM-004T to ESP32:**
* VCC -> 5V (VIN on ESP32)
* GND -> GND
* RX -> GPIO 17 (TX2)
* TX -> GPIO 16 (RX2)

**⚠️ HIGH VOLTAGE WARNING ⚠️**
* This project involves 220V AC Mains. 
* Pass ONLY the Live (Phase) wire of the appliance/load through the CT hole.
* Connect the AC voltage screw terminals on the PZEM to the Live and Neutral of the mains supply (to measure voltage).
* **Safety Warning:** Do not touch the circuit while plugged into AC mains. Double-check all connections before switching on the power.

## Software Dependencies
* `BlynkSimpleEsp32`
* `PZEM004Tv30`
* `LiquidCrystal_I2C`

## Setup Instructions
1. Clone the repository.
2. Open the `.ino` file in the Arduino IDE.
3. Replace `YOUR_BLYNK_AUTH_TOKEN`, `YOUR_WIFI_SSID`, and `YOUR_WIFI_PASSWORD` with your actual credentials.
4. Upload the code to your ESP32.
5. Set up a Blynk Web Dashboard with Virtual Pins: V0 (Voltage), V1 (Current), V2 (Power), and V3 (Energy).
