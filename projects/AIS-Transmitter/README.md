# IoT-Enabled AIS Receiver & Gateway 
An AIS (Automatic Identification System) receiver that passes the data to the data-collecting server. The receiver is based on an ESP32 microcontroller and web-configurable. 

_This is a simplified personal duplication/re-creation project of my previous job._

## Background
To build situational-awareness and help navigation in the sea, the port authority needs to "know" where the vessels are located. Each vessel should be equipped with an AIS transmitter/transponder. Therefore, the corresponding AIS receiver is needed to receive and to plot the location of the vessels on a map. 

## Architectural Design
1. **VHF Receiver**: ADF7021 IC to receive VHF AIS signals on 161.975 & 162.025 MHz.
2. **AIS Decoder**: STM32F4 MCU to decode the raw binary data into an **_!AIVDM_** frame and send it through the serial port.
3. **Internet Gateway**: ESP32 MCU is used to pass the **_!AIVDM_** frame to either marinetraffic or aprs.fi mapping platform.

## Web Configurer
The parameters are user-configurable using a Web Server hosted directly by the ESP32 MCU. Once the config mode is triggered, it provides a Web interface for configuring user data and updating the firmware via OTA.

## Testing Result
..
