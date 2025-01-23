# Weather Station Project

This repository contains the Weather Station Project, which integrates sensors, Node-RED, ThingSpeak, and Python scripts for real-time environmental data monitoring and visualization.

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Setup Instructions](#setup-instructions)
   - [Dependencies](#dependencies)
   - [Installation](#installation)
4. [Usage](#usage)
5. [Mobile Alert Integration](#mobile-alert-integration)
6. [Troubleshooting](#troubleshooting)
7. [Documentation](#documentation)

## Introduction

The Weather Station Project collects data such as temperature, pressure, and hazardous gas levels using sensors connected to a Raspberry Pi. The data is processed using Python scripts, visualized with Node-RED dashboards, and uploaded to ThingSpeak for remote monitoring.

### Node-RED Dashboard Example
![Node-RED Dashboard](./Images/NoderedDash.jpg)

## Features

- Real-time monitoring of environmental parameters.
- Integration with ThingSpeak for cloud-based visualization.
- Local dashboards using Node-RED.
- Mobile notifications for threshold alerts.

### Node-RED Flow Overview
![Node-RED Flow](./Images/Noderedflow.jpg)

## Setup Instructions

### Dependencies

Ensure you have the following:

- Raspberry Pi with Raspbian OS.
- Sensors: BMP280, MQ7, MQ135.
- Python 3.7 or above.
- Node-RED installed.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/RavishanBBN/Weather-Station.git
   cd Weather-Station
   ```
2. Install Python dependencies:
   ```bash
   sudo apt update
   sudo apt install python3-pip
   pip3 install -r requirements.txt
   ```
3. Set up Node-RED:
   ```bash
   sudo npm install -g --unsafe-perm node-red
   node-red
   ```
4. Configure ThingSpeak:
   - Create a ThingSpeak channel.
   - Note the API key for data uploads.

### ThingSpeak Dashboard Example
![ThingSpeak Dashboard 1](./Images/ThingspeakDash1.jpg)

## Usage

1. Run the Python script to collect and send data:
   ```bash
   python3 weather_station.py
   ```
2. Open Node-RED to view local dashboards.
3. Check ThingSpeak for real-time cloud visualizations.

### ThingSpeak Dashboard Output
![ThingSpeak Output](./Images/thingspeakout.jpg)

---

## Mobile Alert Integration

To ensure mobile alerts for high thresholds, we configured notifications using Pushbullet and ThingSpeak React. The system automatically sends notifications to your mobile device whenever hazardous levels cross a predefined threshold.

### Steps:
1. Configure a ThingSpeak React:
   - Go to the "React" section of ThingSpeak.
   - Set up a condition for when hazardous levels exceed a certain threshold.
   - Use the ThingHTTP action to send a POST request to Pushbullet.
2. Link with Pushbullet:
   - Use your API key to authenticate the notification service.
   - Format the request body with the alert title and message.

### Mobile Notification Example
![Mobile Notification Example 1](./Images/mobile_alert_1.jpg)

### Pushbullet Configuration
![Pushbullet Example](./Images/mobile_alert_2.jpg)

---

## Troubleshooting

- **Sensor Read Errors**: Check wiring and sensor connections.
- **Missing Libraries**: Ensure all dependencies in `requirements.txt` are installed.
- **Node-RED Issues**: Restart Node-RED and check logs for errors.
- **ThingSpeak Upload Errors**: Verify the API key and channel configurations.

## Documentation

For detailed setup instructions, error handling, and system diagrams, refer to the [Documentation](./Documentation) folder.

---
### Node-RED Code
![Node-RED Code](./Images/noderedcode.jpg)

### ThingSpeak Code
![ThingSpeak Code](./Images/thingspeakcode.jpg)

### ThingSpeak Dashboard 2
![ThingSpeak Dashboard 2](./Images/ThingspeakDash2.jpg)

### Errors
![Errors](./Images/error.jpg)
