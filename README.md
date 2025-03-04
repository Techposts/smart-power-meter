# Smart Energy Monitoring System

An IoT-based system to monitor energy usage in real-time using ESP8266/ESP32 and SCT013 current sensors integrated with Home Assistant.

![Smart Energy Monitoring System](https://raw.githubusercontent.com/Techposts/smart-power-meter/refs/heads/main/DIY-Energy-Monitoring-Device-home-Assistant.png)

## 📊 Overview

This project allows you to build a smart electricity meter from scratch that:
- Tracks energy usage in real-time
- Displays data in meaningful visualizations
- Sends alerts when power usage exceeds thresholds
- Helps conserve energy and prevent wastage
- Integrates with Home Assistant for smart home automation

## 🛠️ Hardware Requirements

| Component | Details |
|-----------|---------|
| **Microcontroller** | NodeMCU (ESP8266), D1 Mini, or ESP32 |
| **Current Sensor** | SCT013 30A 1V Non-Invasive AC Current Clamp Sensor |
| **Other Components** | • MicroUSB Cable<br>• General-purpose PCB<br>• 10µF 16V capacitor<br>• Two 10K resistors (1/4 watt)<br>• One 33 Ohm resistor (1/4 watt)<br>• 3.5mm female audio jack (optional) |

> [!CAUTION]
> This DIY project involves AC voltage/current, which can be lethal. If you are not experienced with electrical work, seek professional assistance.

## 🔧 Installation Guide

### Step 1: Set Up Home Assistant
Install Home Assistant on a Raspberry Pi or other supported device. Follow the [official installation guide](https://www.home-assistant.io/installation/).

### Step 2: Install ESPHome Add-On
1. In Home Assistant, go to **Configuration > Add-ons, Backups & Supervisor**
2. Click **Add-On Store**
3. Search for "ESPHome" and install it
4. Start the add-on and enable:
   - ✅ Watchdog
   - ✅ Auto-update
   - ✅ Show in sidebar
5. Open the ESPHome Dashboard

### Step 3: Create and Flash the Firmware
1. In ESPHome Dashboard, click **+ New Device > Continue**
2. Name your device (e.g., "smart-power-meter") and click **Next**
3. Select your microcontroller type (ESP8266 for NodeMCU/D1 Mini or ESP32)
4. Click **Skip** to edit the YAML directly
5. Replace the default configuration with the `Smart-Energy-Monitoring.yaml` file from this repository
6. Modify the WiFi credentials and voltage settings (change from 230V to 110/120V if needed for your country)
7. Click **Save** and then **Install > Plug into this computer**
8. Download the compiled firmware
9. Flash the firmware using [ESPHome-Flasher](https://github.com/esphome/esphome-flasher) tool

### Step 4: Hardware Assembly
Connect the SCT013 sensor to your ESP8266/ESP32 following the circuit diagram:

![Circuit Diagram](https://github.com/Techposts/smart-power-meter/blob/main/Circuit-Diagram.png)

### Step 5: Sensor Calibration
1. Clamp the SCT013 sensor on the phase wire (usually red) from your electricity meter
2. In ESPHome Dashboard, click **Logs** under your device name
3. Note down several "Measured Current" values and take the average
4. Edit your YAML file to add calibration under the sensor section:
   ```yaml
   filters:
     - calibrate_linear:
         - 0 -> 0
         - [average_value] -> [actual_current]
   ```
5. Save and install the updated firmware wirelessly

### Step 6: Configure Home Assistant
1. Go to **Configuration > Devices & Services > Add Integration**
2. Search for and select **ESPHome**
3. Enter the IP address of your sensor (found in ESPHome logs)
4. Select the appropriate area for your device
5. Add the device to your dashboard

## ⚡ Automations

The `Automation.yaml` file in this repository contains example automations for:
- 📱 Sending notifications when energy usage exceeds thresholds
- 🔌 Turning off non-essential devices during peak usage
- 📊 Logging energy consumption data
- 📈 Creating daily/weekly/monthly reports

Add these automations to your Home Assistant configuration or modify them to suit your needs.

## 📊 Energy Dashboard

Use Home Assistant's built-in Energy Dashboard to:
- Monitor daily, monthly, or yearly energy usage
- View hourly breakdowns of consumption
- Track energy costs (with proper configuration)
- Identify trends and optimize usage

## 🔄 Expanding the System

To monitor individual appliances:
1. Build additional sensors with the same configuration
2. Clamp them on the power cord of specific devices
3. Integrate them into Home Assistant for granular monitoring
4. Create appliance-specific automations

## ❓ Troubleshooting

| Issue | Solution |
|-------|----------|
| **Inaccurate Readings** | Double-check calibration using a multimeter |
| **Connection Issues** | Verify WiFi signal strength where the sensor is installed |
| **Sensor Not Detecting** | Ensure the SCT013 is properly clamped and oriented correctly |

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- ESPHome project for making firmware creation simple
- Home Assistant community for integration support
- All contributors and testers who provided feedback

---

<details>
<summary>Project Status</summary>

- [x] Initial documentation
- [x] Circuit design
- [x] ESPHome configuration 
- [ ] Sample automations
- [ ] Advanced usage tutorial

</details>
