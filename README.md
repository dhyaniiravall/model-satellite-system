# 🛰️ Model Satellite System with Telemetry, GPS & FPV Transmission

> A scaled-down implementation of real satellite subsystems including telemetry, sensing, communication, and live video transmission — with a complete guide to building a similar system.

---

## 🏆 Achievement

* 🌏 **Ranked 7th Internationally**
* 🥇 **1st in Asia**
* Team Dyaus | Institute of Technology, Nirma University

---

## Overview

This project presents the design and development of a fully functional model satellite system with real-time data acquisition using customised PCB and data handling, telemetry, GPS tracking, live FPV video transmission and visualisation at the ground control station, long range communication using transceiver and task execution such as dual mechanical filter and error code alert system during and throughout flight.

This repository is structured not only to showcase the project, but also to **help others understand and replicate a similar system step-by-step**.

---

# How to Approach Building This System

If you want to build a model satellite, follow this roadmap:

### Start with System Design

* Divide your system into:
  * Payload (sensor data collection + communication)
  * Container (deployment + backup sensor)
* Define:
  * What data you want (altitude, orientation, temp)
  * How you will transmit it

---

### Select Components (Based on Requirements)

| Function        | Component Used | Why                      |
| --------------- | -------------- | ------------------------ |
| Microcontroller | RP2040         | Low power, flexible      |
| Orientation     | BNO055         | Built-in sensor fusion   |
| Pressure        | BMP390         | High accuracy altitude   |
| Temperature     | TMP117         | ±0.1°C precision         |
| Telemetry       | LoRa SX1278    | Long-range communication |
| GPS             | L89            | Reliable positioning     |
| Storage         | OpenLog + SD   | Easy logging             |
| Video           | TX800 FPV      | Real-time transmission   |

---

### Design Custom PCB

* Integrate:

  * RP2040
  * Sensor interfaces (I2C)
  * RF module connections
  * Power regulation (3.3V / 5V)
* Keep:

  * Noise isolation in mind
  * Proper grounding

---

### Implement Communication

* Use:

  * **I2C** → Sensors
  * **UART/SPI** → RF modules
* Design telemetry packet:

```text
<ALT, TEMP, ROLL, PITCH, YAW, GPS_LAT, GPS_LON>
```

---

### Develop Flight Software (Core Logic)

Divide into stages:

1. Calibration
2. Ascent (data collection)
3. Deployment
4. Separation (trigger at altitude)
5. Landing

Use **state machine logic** for clean implementation

---

### Integrate Ground Station

* Receive telemetry via LoRa
* Visualize:

  * Graphs
  * GPS location
  * Orientation
* Send commands (for filters / control)

---

### Add FPV System

* Use separate power line (avoid noise)
* Ensure:

  * Proper antenna placement
  * Minimal interference with RF module

---

### Test in Iterations 

* Test sensors individually
* Then communication
* Then full integration

---

## System Architecture

### Science Payload

* Controlled by **RP2040-based custom PCB**
* Handles sensing, telemetry, GPS, and FPV

### Container

* Handles deployment and altitude-triggered separation
* Sends data to payload

---

## Hardware Components

### Core System

* Custom PCB (RP2040 + EEPROM + OpenLog)

### Sensors

* BMP390 → Altitude
* BNO055 → Orientation
* TMP117 → Temperature

###  Communication

* LoRa SX1278 (433 MHz)

### Navigation

* L89 GPS

### Imaging

* CMOS Camera + SpeedyBee TX800 (5.8 GHz)

### Power

* Buck converters (3.3V & 5V)

---

##  Working Principle

1. System calibrates on ground
2. Data collection begins during ascent
3. Deployment at ~600–700m
4. Separation triggered at 400m
5. Payload activates telemetry + FPV
6. Landing → buzzer indication

---

##  Communication System

* **Protocols:** I2C, UART, SPI
* **Frequencies:**

  * 433 MHz → Telemetry
  * 5.8 GHz → Video
* **Range:** ~950m

---

##  Flight Software (FSW)

* State-based execution
* Command validation
* Error handling system (IAS)

---

##  Mechanical Filtering System

* Servo-based dual filter system
* Controlled via ground commands

---

##  Data & Output

* Altitude, Pressure
* Temperature
* Roll, Pitch, Yaw
* GPS coordinates
* Live video

---

##  Testing & Validation

* Sensor compatibility
* Power analysis
* RF range (~950m)
* Flight stage validation

---

##  Key Learnings (Important if you’re building this)

* RF + FPV interference must be managed
* Power stability is critical
* Sensor calibration affects everything
* Always test modules independently before integration

---

##  Project Structure

Model-Satellite/
│── code/
│── pcb_design/
│── results/
│── images/
│── README.md

---




