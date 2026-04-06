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
* [cite_start]ESP32 Dev Module (Wi-Fi + Bluetooth enabled) [cite: 17]
* [cite_start]PZEM-004T v3.0 AC Sensor Module (UART) [cite: 18]
* 16x2 I2C LCD Display 
* [cite_start]5V Power Supply (Micro USB or Hi-Link AC-to-DC converter) [cite: 21]
* LEDs (Green for Normal, Red for Alert)

## Circuit Connections
**PZEM-004T to ESP32:**
* [cite_start]VCC -> 5V (VIN on ESP32) [cite: 26]
* [cite_start]GND -> GND [cite: 27]
* [cite_start]RX -> GPIO 17 (TX2) [cite: 28]
* [cite_start]TX -> GPIO 16 (RX2) [cite: 29]

**⚠️ HIGH VOLTAGE WARNING ⚠️**
* [cite_start]This project involves 220V AC Mains[cite: 31]. 
* [cite_start]Pass ONLY the Live (Phase) wire of the appliance/load through the CT hole[cite: 33].
* [cite_start]Connect the AC voltage screw terminals on the PZEM to the Live and Neutral of the mains supply (to measure voltage)[cite: 34].
* [cite_start]**Safety Warning:** Do not touch the circuit while plugged into AC mains[cite: 35]. [cite_start]Double-check all connections before switching on the power[cite: 36].

## Software Dependencies
* `BlynkSimpleEsp32`
* `PZEM004Tv30`
* `LiquidCrystal_I2C`

## Setup Instructions
1. Clone the repository.
2. Open the `.ino` file in the Arduino IDE.
3. Replace `YOUR_BLYNK_AUTH_TOKEN`, `YOUR_WIFI_SSID`, and `YOUR_WIFI_PASSWORD` with your actual credentials.
4. Upload the code to your ESP32.
5. [cite_start]Set up a Blynk Web Dashboard with Virtual Pins: V0 (Voltage), V1 (Current), V2 (Power), and V3 (Energy)[cite: 42, 43, 44, 45].
