# Solar-Powered Water Level Sensor for Home Assistant

A wireless, solar-powered water level sensor using ESP32-C3 Supermini and AJ SR04M waterproof ultrasonic sensor. Integrated with Home Assistant for real-time monitoring.

## 🌟 Features
- **Solar-Powered**: Uses an MPPT 6V module and Li-ion battery.
- **Wireless Connectivity**: ESP32-C3 Supermini with ESP-NOW protocol.
- **Waterproof Ultrasonic Sensor**: AJ SR04M for accurate level measurement.
- **Home Assistant Integration**: Sends data wirelessly.
- **3D-Printed Enclosure**: Protects electronics from the environment.

## 🛠️ Components Used
- ESP32-C3 Supermini
- AJ SR04M Waterproof Ultrasonic Sensor
- MPPT 6V Solar Charging Module
- 1S Li-ion Cell with BMS
- 3D-Printed Enclosure

## ⚡ Wiring Diagram
```
ESP32-C3       AJ SR04M
----------------------
3.3V          VCC
GND           GND
GPIO4         TRIG
GPIO5         ECHO
```
MPPT Solar Module is connected to the Li-ion cell and ESP32-C3 power input.

## 🔧 Installation & Setup
1. **Flash Firmware**: 
   - Use PlatformIO or Arduino IDE to upload firmware.
   - Install required libraries (ESP-NOW, WiFi, etc.).
2. **Connect Components**:
   - Wire ESP32-C3, Ultrasonic Sensor, and Solar Module.
3. **Home Assistant Setup**:
   - Add ESP-NOW receiver.
   - Configure MQTT or ESPHome for integration.
4. **Mount the Sensor**:
   - Ensure the sensor is positioned correctly to measure water level.
   - Secure inside a waterproof 3D-printed case.

## 🏡 Home Assistant Integration
Example YAML configuration:
```yaml
sensor:
  - platform: mqtt
    name: "Water Level"
    state_topic: "home/sensor/water_level"
    unit_of_measurement: "%"
```

## 📷 Project Demonstration
[![Watch the Video](https://img.youtube.com/vi/YOUR_VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)

## ⚠️ Safety Notes
- Ensure proper waterproofing for outdoor use.
- Handle Li-ion batteries with care to avoid overcharging.
- Place solar panel in an optimal sunlight position.

## 📝 License
This project is open-source under the [MIT License](LICENSE).

## 🤝 Contributions
Feel free to submit issues or pull requests to improve this project!

---
Made with ❤️ by Ravi Singh
