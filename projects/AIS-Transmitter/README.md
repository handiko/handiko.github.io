# Low-cost AIS Transmitter for Small Boat 
A low-cost Class-B AIS transmitter to track small boats to provide situational awareness in a marine environment. The transmitter is based ona  common MCU and other components to ensure supply chain availability.

## Project Background
Small boats are often "not visible" to the other vessels due to their lack of vessel tracking equipment. They do not install any AIS transmitter because its high price and not economical for their business. Therefore, a low-cost AIS transmitter solution is needed for this necessity.

## Technical Challenges
* Low-cost: The equipment should be as low-cost as possible while still maintaining the required specifications for the marine environment.
* Compliance: The transmitter should comply with the AIS protocol standard and national regulations.
* Self-contained: AIS transmitter, GPS, internal battery, and the solar charger should be contained in the same box.

## Architectural Design
1. AIS Protocol Processor: An ESP32 is used to read the GPS data and construct the AIS frames.
2. VHF AIS Transmitter: ADF7021 is used to transmit the data into a VHF GMSK burst.
3. VHF RF Power Amplifier: Class-B AIS should transmit with an RF power output of 2.5 watts. The AFT04MS005 RF LDMOS is used for this job.

## Web Configurer
The parameters are user-configurable using a Web Server hosted directly by the ESP32 MCU. Once the config mode is triggered, it provides a Web interface for configuring user data and updating the firmware via OTA.

## Testing Result
..
