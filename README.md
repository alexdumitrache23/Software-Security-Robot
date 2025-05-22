Security Robot - Rust Embassy Project
A smart security robot built with Rust Embassy framework for Raspberry Pi Pico2 W, featuring obstacle avoidance, motion detection, and emotional LED display.

Features
Obstacle Avoidance: Ultrasonic sensor detects obstacles and triggers avoidance maneuvers
Motion Detection: PIR sensor detects human presence for security monitoring
Emotional Display: 8x8 LED matrix shows happy/angry faces based on threat level
Telegram Alerts: Sends security notifications via Telegram bot
Smart Behavior: Friendly when safe, alert when motion detected near obstacles

Hardware Requirements
Raspberry Pi Pico W
HC-SR04 Ultrasonic Sensor (Trig: PIN_16, Echo: PIN_17)
PIR Motion Sensor (PIN_22)
MAX7219 LED Matrix (DIN: PIN_12, CLK: PIN_10, CS: PIN_11)
Motor Driver (L298N or similar, Pins 6-9)
WiFi connection for Telegram integration
2x DC Motors

Pin Configuration
Ultrasonic: PIN_16 (Trig), PIN_17 (Echo)
PIR Sensor: PIN_22
LED Matrix: PIN_12 (DIN), PIN_10 (CLK), PIN_11 (CS)
Motors: PIN_6-9 (Motor driver inputs)
Project Structure
├── main.rs          # Main application logic
├── ultrasonic.rs    # HC-SR04 sensor driver
├── pir.rs           # PIR motion sensor
├── matrix.rs        # MAX7219 LED matrix driver
├── motor.rs         # Motor control
└── telegram.rs      # Telegram bot integration
Robot Behavior
Normal Operation (No Motion)

🙂 Happy face on LED matrix
Moves forward until obstacle detected
Performs avoidance maneuvers (backward + turn)

Threat Detection (Motion + Obstacle)
😠 Angry face on LED matrix
Stops all movement immediately
Sends Telegram alert: "Threat detected by Security Robot!"

Error States
Sensor timeout triggers angry face and alert
System continues monitoring after errors

Setup Instructions
Hardware: Wire components according to pin configuration
WiFi: Update credentials in main.rs:
rustwifi_controller.set_credentials("YOUR_SSID", "YOUR_PASSWORD").await;

Telegram: Set bot token and chat ID in main.rs:
rustlet mut telegram_bot = TelegramBot::new("YOUR_BOT_TOKEN", "YOUR_CHAT_ID");

Build: cargo build --release
Flash: Deploy to Pico W using your preferred method

Code Highlights
Async/Await: Full Embassy async framework usage
Modular Design: Clean separation of hardware drivers
Error Handling: Sensor timeouts and recovery
Smart Logic: Context-aware threat detection

Current Status
✅ Core functionality implemented
✅ Hardware drivers complete
⚠️ Telegram integration needs HTTP client implementation
⚠️ WiFi error handling could be improved
