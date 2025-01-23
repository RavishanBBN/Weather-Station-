# Weather-Station-
A weather monitoring system with Node-RED and ThingSpeak integration for mobile alerts.

# Weather Station Project

A comprehensive weather station project that collects environmental data using sensors connected to a Raspberry Pi, processes the data with Node-RED, and visualizes it through ThingSpeak. This project includes error handling, data visualization, and integration with mobile notifications for alerts.

## Table of Contents

- [Introduction](#introduction)
- [System Components](#system-components)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
  - [1. Hardware Requirements](#1-hardware-requirements)
  - [2. Software Requirements](#2-software-requirements)
  - [3. Installation Steps](#3-installation-steps)
- [Flow Diagram](#flow-diagram)
- [Common Errors and Resolutions](#common-errors-and-resolutions)
- [See Documentation Folder](#see-documentation-folder)
- [Contributing](#contributing)

## Introduction

The Weather Station project provides real-time environmental monitoring by collecting data such as temperature, humidity, pressure, and air quality. It uses Raspberry Pi, various sensors, and cloud platforms for visualization and notifications.

## System Components

1. **Raspberry Pi**: Central hub for connecting sensors and processing data.
2. **Sensors**:
   - BMP280: Measures temperature and pressure.
   - MQ7: Detects CO levels.
   - MQ135: Detects air quality.
3. **Node-RED**: For data processing and routing.
4. **ThingSpeak**: For visualizing data.
5. **MQTT Broker**: Facilitates data communication.

## Features

- Real-time data collection from multiple sensors.
- Cloud integration with ThingSpeak for data visualization.
- Error handling for robust performance.
- Notifications via email or mobile for threshold breaches.
- Modular and extensible architecture.

## Setup Instructions

### 1. Hardware Requirements

- Raspberry Pi (any model with GPIO support).
- BMP280 sensor.
- MQ7 and MQ135 sensors.
- ADS1115 ADC for handling analog sensors.
- Breadboard and jumper wires.
- Power supply for Raspberry Pi.

### 2. Software Requirements

- Python 3.7+
- Node.js and npm
- Node-RED
- ThingSpeak account
- MQTT broker (e.g., Mosquitto)

### 3. Installation Steps

#### On Raspberry Pi

1. Update the system:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. Install Python dependencies:
   ```bash
   sudo apt install python3-pip
   pip3 install paho-mqtt requests adafruit-circuitpython-bmp280 adafruit-circuitpython-ads1x15
   ```
3. Install Mosquitto MQTT broker:
   ```bash
   sudo apt install mosquitto mosquitto-clients
   sudo systemctl start mosquitto
   ```
4. Install Node-RED:
   ```bash
   sudo apt install nodejs npm
   sudo npm install -g --unsafe-perm node-red
   ```
5. Start Node-RED:
   ```bash
   node-red
   ```
6. Deploy the Node-RED flow using the provided JSON file.

#### ThingSpeak Setup

1. Create a ThingSpeak account at [ThingSpeak](https://thingspeak.com/).
2. Create a new channel and note the API write key.
3. Configure the Python script to send data to ThingSpeak:
   ```python
   api_key = "YOUR_API_KEY"
   ```

## Flow Diagram

The system flow diagram illustrates the interaction between components. For detailed guidance, refer to the documentation folder.

## Common Errors and Resolutions

1. **Sensor Read Errors**: Ensure proper connections and power supply.
2. **Missing Python Libraries**: Install missing libraries using pip.
3. **Node-RED Not Starting**: Resolve port conflicts or reinstall Node-RED.
4. **MQTT Issues**: Verify broker status and network connectivity.
5. **ThingSpeak Data Not Updating**: Check API keys and URL formatting.
6. **Permission Errors**: Ensure proper file and GPIO permissions.

For a complete list of errors and resolutions, see the documentation folder.

## See Documentation Folder

For more detailed guidance, troubleshooting steps, and additional resources, refer to the `documentation` folder in this repository. The folder includes:

- Detailed LaTeX guides.
- Sample data for testing.
- Advanced error handling instructions.
- Flow diagrams and architectural overviews.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with detailed explanations of your changes.


Happy Monitoring!
