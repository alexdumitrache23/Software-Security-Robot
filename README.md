# Security Robot - Rust Embassy Project

A smart security robot built with Rust Embassy framework for Raspberry Pi Pico 2W, featuring obstacle avoidance, motion detection, and emotional LED display.

## Features

- **Obstacle Avoidance:** Ultrasonic sensor detects obstacles and triggers avoidance maneuvers  
- **Motion Detection:** PIR sensor detects human presence for security monitoring  
- **Emotional Display:** 8x8 LED matrix shows happy/angry faces based on threat level  
- **Telegram Alerts:** Sends security notifications via Telegram bot  
- **Smart Behavior:** Friendly when safe, alert when motion detected near obstacles  

## Hardware Requirements

- Raspberry Pi Pico 2W  
- HC-SR04 Ultrasonic Sensor (Trig: PIN_16, Echo: PIN_17)  
- PIR Motion Sensor (PIN_22)  
- MAX7219 LED Matrix (DIN: PIN_12, CLK: PIN_10, CS: PIN_11)  
- Motor Driver (L298N, Pins 6-9)  
- WiFi connection for Telegram integration  
- 2x DC Motors

## Project Structure

- `main.rs` — Main application logic  
- `ultrasonic.rs` — HC-SR04 sensor driver  
- `pir.rs` — PIR motion sensor  
- `matrix.rs` — MAX7219 LED matrix driver  
- `motor.rs` — Motor control  
- `telegram.rs` — Telegram bot integration  

## Robot Behavior

### Normal Operation (No Motion)

- Happy face displayed on LED matrix  
- Moves forward until obstacle detected  
- Performs avoidance maneuvers (backward + turn)  

### Threat Detection (Motion + Obstacle)

- Angry face displayed on LED matrix  
- Stops all movement immediately  
- Sends Telegram alert: "Threat detected by Security Robot!"  

### Error States

- Sensor timeout triggers angry face and alert  
- System continues monitoring after errors  

## Setup Instructions

1. Hardware: Wire components according to pin configuration  
2. WiFi Configuration: Update WiFi SSID and password in code  
3. Telegram Bot Setup: Set bot token and chat ID in code  
4. Build the project using cargo  
5. Flash the compiled firmware to the Pico W device  

## Code Highlights

- Uses async/await with the Embassy framework  
- Modular hardware driver design  
- Handles sensor timeouts and errors  
- Implements smart context-aware threat detection  

## Current Status

- Core functionality implemented  
- Hardware drivers complete  
- Telegram integration requires HTTP client implementation  
- WiFi error handling could be improved  

## Future Enhancements

- Add HTTP client for Telegram integration  
- Implement WiFi reconnection logic  
- Add more LED matrix animations  
- Include power management features  
