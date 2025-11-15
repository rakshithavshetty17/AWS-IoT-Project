# AWS-IoT-Project
An IoT-driven predictive maintenance project using ESP32 and AWS services. The system streams real-time sensor data to AWS IoT Core, stores it in Timestream, detects anomalies, and triggers SNS alerts for equipment fault prevention.
Project Overview

The ESP32 continuously reads temperature and vibration values from connected sensors and publishes them to AWS IoT Core using MQTT.
Using an IoT Rule, the data is pushed into Amazon Timestream for time-series storage.
If temperature or vibration crosses a predefined threshold, SNS automatically sends an alert to the user, enabling proactive maintenance.

Tech Stack
Hardware

ESP32 Development Board

Temperature Sensor (e.g., DHT22/DS18B20)

Vibration Sensor (e.g., SW-420 or accelerometer)

AWS Services

AWS IoT Core – Secure MQTT communication

IoT Rules Engine – Route data to Timestream & SNS

Amazon Timestream – Time-series database for sensor logs

Amazon SNS – SMS/Email alerts

ESP32 Setup

Install Arduino IDE or PlatformIO

Add ESP32 board support

Install required libraries:

WiFiClientSecure

PubSubClient

Sensor libraries (e.g., DHT, etc.)

Configure:

WiFi credentials

AWS IoT Core endpoint

Certificate paths

Flash the firmware to ESP32

AWS Setup Summary
1. AWS IoT Core

Create IoT Thing

Generate & attach certificate

Attach IoT policy

Configure MQTT topics

2. IoT Rule

Example rule to send data to Timestream and SNS:

SELECT temperature, vibration FROM 'equipment/sensors'

3. Timestream

Create Database

Create Table

Store incoming sensor values with timestamps

4. SNS

Create SNS Topic

Subscribe with email or SMS

Trigger SNS when:

temperature > threshold

vibration > threshold

🔍 Anomaly Detection Logic

Threshold-based detection:

Temperature > 60°C → Alert

Vibration above safe level (value based on sensor output) → Alert

All alerts are routed via SNS.

