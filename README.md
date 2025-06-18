# Watertank Monitor

Monitors water level in cylindrical tanks using an A02YYUW ultrasonic sensor. Features runtime-adjustable tank geometry, OLED display, LED and buzzer alerts, and web interface for real-time monitoring and calibration. Integrates with Home Assistant.

## Features

- A02YYUW (sen0312) waterproof ultrasonic sensor (UART, 3–450 cm range)
- Runtime-configurable tank dimensions (height, diameter, offset)
- OLED display with multi-page data view and timeout control
- LED status indicators (color-coded + blinking for alerts)
- Buzzer alert with night mode and melody control
- Web interface with grouped values and calibration tools
- Home Assistant integration via encrypted API
- OTA firmware updates via ESPHome

## Hardware

- ESP32-C6 (Seeed Studio XIAO)
- A02YYUW (sen0312) ultrasonic distance sensor (UART)
- SSD1306 128x64 OLED display (I2C)
- Neopixel RGB LED (WS2812 or compatible)
- Passive piezo buzzer (PWM control)
- Calibration buttons (2x digital input)

## Wiring

| Component               | ESP32-C6 Pin | Notes                      |
|------------------------|--------------|----------------------------|
| Ultrasonic Sensor (TX) | GPIO4        | UART RX (9600 baud)        |
| Ultrasonic Sensor (RX) | GPIO5        | UART TX (not used)         |
| OLED Display (I2C)     | GPIO6 / 7    | SDA/SCL — Addr: `0x3C`     |
| RGB LED (Neopixel)     | GPIO8        | Data line                  |
| Buzzer (PWM)           | GPIO9        | Passive buzzer (square wave) |
| Calibrate Button 1     | GPIO10       | Set offset height          |
| Calibrate Button 2     | GPIO11       | Reset offset / test alert  |

> Sensor powered at 5V. All other components powered at 3.3V.

## Getting Started

1. Flash the ESP32-C6 with `watertank_monitor.yaml` using ESPHome.
2. Update `!secret` values for Wi-Fi, API, and OTA credentials.
3. Power the device (5V barrel jack recommended).
4. Access the web interface at `http://<device-ip>` to view water level, configure tank dimensions, or run calibration.
5. Integrate with Home Assistant using ESPHome’s encrypted API.

## License

MIT License  
© 2025 John Camm
