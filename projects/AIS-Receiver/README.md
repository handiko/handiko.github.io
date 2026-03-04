# IoT-Enabled AIS Receiver & Gateway

This project is an IoT-based Automatic Identification System (AIS) Receiver designed to capture marine vessel data and relay it to centralized monitoring servers. Built around an ESP32 and an STM32F4, the system features a web-based configuration interface for easy deployment and management.

_**Note:** This project is a personal recreation and simplified duplication of a professional system I developed in a previous role._

## Project Background
For port authorities and maritime operators, situational awareness is critical for safe navigation. Vessels are equipped with AIS transponders that broadcast real-time data; this project provides the necessary infrastructure to receive those signals and forward them to mapping platforms (like MarineTraffic or APRS.fi) for visual tracking. 

## Technical Challenges
* **GMSK Demodulation:** AIS signals utilize Gaussian Minimum Shift Keying (GMSK). Extracting data requires a deep understanding of this modulation scheme to ensure signal integrity.
* **Frame Decoding:** The raw binary stream captured from the radio frequency must be parsed and decoded into standardized, readable data frames.
* **Data Integration:** Decoded frames must be formatted and transmitted over the internet to third-party servers for map plotting.
* **Processing Efficiency:** AIS decoding is a computationally intensive, interrupt-heavy process. To ensure stability, the decoding logic is decoupled from the internet gateway functions using a dual-MCU architecture.

## Architectural Design
The system is divided into three functional layers to ensure high performance and reliability:
1. **RF Front-End (VHF Receiver):** Uses the ADF7021 transceiver IC to monitor AIS frequencies at 161.975 MHz and 162.025 MHz.
2. **AIS Decoder:** An STM32F4 microcontroller handles the heavy lifting—decoding raw binary data into standard _**!AIVDM**_ frames and outputting them via UART.
3. **Internet Gateway:** An ESP32 microcontroller receives the serial data and acts as the bridge, pushing the frames to mapping platforms via Wi-Fi.

## Web Configurer
The ESP32 hosts a local Web Server, providing an intuitive interface for:
* **User Parameter Configuration:** Set server credentials and network settings without recompiling code.
* **OTA Updates:** Wirelessly update the firmware to add features or refine decoding logic.

## Testing Result
..
