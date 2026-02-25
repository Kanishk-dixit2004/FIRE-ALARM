# Fire Alarm & Smoke Detection System

**Short description:** Arduino-based system that detects smoke (MQ-2) and flame, displays status on LCD, and triggers buzzer/LED alerts.

## Components
- Arduino Uno
- MQ-2 gas/smoke sensor
- Flame sensor
- 16x2 LCD (I2C)
- Buzzer
- Power supply (9V)
- Breadboard, jumper wires

## Wiring
(brief wiring instructions or image reference)

## How to run
1. Open `Fire_Alarm_Smoke.ino` in Arduino IDE.
2. Select **Arduino Uno** as board and the correct COM port.
3. Upload.

## Features
- Smoke level on LCD
- Flame detection with immediate alarm
- Visual and audible alert

## Future improvements
- Blynk/ESP8266 for mobile alerts
- GSM SMS alerts
- Relay to cut power to appliance

## License
MIT
