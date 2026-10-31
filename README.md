# ⚡ SmartMeter – IoT-Based Energy Monitoring and Anomaly Detection

An IoT-based smart energy monitoring system designed to monitor electrical parameters, visualize energy consumption, and identify abnormal operating conditions through telemetry analysis.

## 📌 Project Overview

SmartMeter is an IoT-based energy monitoring system that combines embedded hardware, wireless communication, and software-based data analysis to provide insights into electrical energy consumption.

The system uses a **PZEM-004T energy measurement module** interfaced with an **ESP32 microcontroller** to collect electrical parameters. The ESP32 transmits the measurements over Wi-Fi using MQTT communication. A gateway processes the received telemetry, identifies suspicious or abnormal conditions, and makes the information available through a monitoring dashboard.

In addition to monitoring electrical parameters, the system considers telemetry freshness and communication status to distinguish between actual zero-power readings and missing or stale data.

## 🎯 Project Objectives

- Monitor electrical parameters in real time.
- Transmit measurement data wirelessly using Wi-Fi.
- Enable communication between embedded devices and the monitoring application using MQTT.
- Visualize electrical measurements and energy consumption trends.
- Identify unusual power consumption patterns.
- Detect missing, stale, or delayed telemetry.
- Provide alerts and status information to support energy monitoring.

## 🛠️ Hardware Components

| Component | Purpose |
|---|---|
| ESP32 Development Board | Reads measurements and handles wireless communication |
| PZEM-004T Energy Meter Module | Measures electrical parameters |
| Electrical Load | Provides the load under observation |
| Power Supply | Powers the system |
| Connecting Wires | Establish electrical connections |

*Note: Confirm the exact PZEM-004T variant and electrical ratings used in your implementation before publishing the final hardware specifications.*

## 💻 Technologies Used

- **Embedded Systems:** ESP32
- **Energy Measurement:** PZEM-004T
- **Communication:** Wi-Fi, MQTT
- **Messaging Architecture:** MQTT publisher–broker–subscriber model
- **Data Processing:** Gateway-based telemetry processing
- **Visualization:** SmartMeter monitoring dashboard
- **Anomaly Detection:** Telemetry validation and abnormal-condition detection

*The technologies listed describe the project's architecture. Add specific programming languages, frameworks, and broker software only if they were used in your implementation.*

## 🏗️ System Architecture

```text
       Electrical Load
              │
              ▼
       ┌──────────────┐
       │  PZEM-004T   │
       │ Energy Meter │
       └──────┬───────┘
              │
              ▼
       ┌──────────────┐
       │     ESP32    │
       │ Data Reading │
       └──────┬───────┘
              │
         Wi-Fi + MQTT
              │
              ▼
       ┌──────────────┐
       │ MQTT Broker  │
       └──────┬───────┘
              │
              ▼
       ┌──────────────┐
       │   Gateway    │
       │ Telemetry    │
       │ Processing   │
       └──────┬───────┘
              │
       ┌──────┴────────┐
       ▼               ▼
┌──────────────┐ ┌──────────────┐
│   Anomaly    │ │  Monitoring  │
│  Detection   │ │  Dashboard   │
└──────────────┘ └──────────────┘
```

*The diagram represents the intended logical data flow. Adapt it if your actual implementation uses a different arrangement.*

## ⚙️ How It Works

### 1. Electrical Parameter Measurement

The PZEM-004T measures electrical parameters associated with the connected load. Depending on the module variant, these may include:

- Voltage
- Current
- Active power
- Energy consumption
- Frequency
- Power factor

### 2. Data Acquisition Using ESP32

The ESP32 communicates with the energy meter, retrieves the measurements, and prepares the data for transmission.

### 3. Wireless Data Transmission

The ESP32 connects to a Wi-Fi network and transmits telemetry using MQTT.

MQTT provides a publish–subscribe communication mechanism that allows the embedded device and monitoring software to exchange data without being directly coupled.

### 4. Gateway-Based Processing

The gateway receives the published measurements and checks the incoming telemetry.

The processing logic considers data validity and freshness so that missing or outdated measurements are not automatically interpreted as zero electrical consumption.

### 5. Anomaly Detection

The system analyses incoming telemetry to identify potentially abnormal conditions, including:

- Missing or stale measurement data
- Unusual power consumption
- Sustained high-load conditions
- Unexpected changes in electrical measurements

These detections indicate conditions that may require investigation; they do not independently establish that an electrical fault has occurred.

### 6. Dashboard Visualization

The monitoring dashboard presents available electrical measurements and system status information. Depending on the implemented features, it can support the visualization of consumption trends, estimated energy costs, peak demand, and anomaly alerts.

## ✨ Key Features

- **Electrical Parameter Monitoring:** Collects electrical measurements from the energy meter.
- **Wireless Communication:** Transfers telemetry through Wi-Fi.
- **MQTT-Based Messaging:** Uses a publish–subscribe architecture for device-to-application communication.
- **Energy Consumption Visualization:** Helps users understand electrical usage patterns.
- **Telemetry Freshness Validation:** Identifies missing or outdated measurements.
- **Abnormal-Condition Detection:** Flags unusual power patterns and sustained high-load conditions.
- **System Status Monitoring:** Helps distinguish communication problems from genuine measurement values.

## 💡 What Makes This Project Different?

A key feature of SmartMeter is its attention to **telemetry quality as well as electrical measurements**.

In a conventional monitoring system, a missing measurement could be mistaken for a zero-power reading if communication failures are not handled properly.

SmartMeter incorporates telemetry freshness checks to help distinguish between:

- A valid zero-power measurement
- A stale measurement
- Missing or interrupted telemetry

This improves the reliability of monitoring and helps prevent misleading interpretations of energy consumption.

## 🔬 Testing and Validation

The prototype should be evaluated under different operating conditions, such as:

- No-load and normal-load conditions
- Changes in electrical load
- Sustained high-load conditions
- Interrupted Wi-Fi or MQTT communication
- Missing or stale telemetry
- Recovery after communication is restored

Measurement accuracy should be validated against an appropriate reference energy meter. Anomaly-detection performance should also be evaluated using documented test cases.

## ⚠️ Limitations

- Measurement accuracy depends on the energy meter module and requires validation against a reference instrument.
- Wi-Fi or MQTT interruptions may delay telemetry delivery.
- Anomaly detection identifies suspicious conditions but does not automatically confirm electrical faults.
- Dashboard reliability depends on the availability of the communication and data-processing components.
- The prototype's physical enclosure and final packaging may require further development.

## 🚀 Future Improvements

- Add historical data storage and long-term energy analysis.
- Introduce configurable power-consumption thresholds.
- Improve anomaly detection using statistical or machine-learning techniques.
- Add notifications for abnormal conditions.
- Implement secure MQTT communication and device authentication.
- Improve the dashboard with detailed reports and downloadable energy-consumption records.
- Validate performance across different loads and operating conditions.

## 📚 Applications

- Home energy monitoring
- Small-office electricity monitoring
- Laboratory energy measurement
- Load-pattern analysis
- IoT-based energy management
- Educational demonstrations of embedded systems and MQTT communication

## 👨‍💻 Skills Demonstrated

- Embedded systems development
- ESP32 interfacing
- Electrical parameter measurement
- Wi-Fi communication
- MQTT messaging
- Telemetry processing
- Anomaly detection
- Dashboard-based monitoring
- Hardware–software integration

## ⚡ Safety Notice

Electrical energy measurement can involve hazardous mains voltages. Use appropriately rated equipment, follow the manufacturer's wiring instructions, and ensure proper insulation and protection. Mains wiring and testing should be performed by a qualified person.

## 📄 Project Status

**Prototype developed; further validation and refinement may be required.**

This project demonstrates the integration of embedded energy measurement, wireless telemetry, data processing, and dashboard-based monitoring.

---
