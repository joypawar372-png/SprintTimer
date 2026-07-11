# ⏱️ ESP32 Sprint Core Engine & Wireless Telemetry System

An open-source, ultra-portable wireless timing gate designed for automated, hands-free split-second tracking. Built on the ESP32 platform, this system eliminates the frustration of expensive commercial timing setups and tedious hardware alignment, delivering real-time telemetry straight to your smartphone or laptop browser.

---

## 🎯 Project Overview & Use Cases

This project transforms a standard microcontroller into an automated, high-precision **wireless stopwatch**. By leveraging lazer sensors, the system captures performance metrics instantly—completely removing human reaction error from the equation.

* **🏃‍♂️ Athletic Performance & Conditioning:** Track 40-yard dashes, agility drills, or track split times automatically during solo or team training sessions.
* **🤖 Robotics & Rover Benchmarking:** Measure autonomous vehicle lap times, path-following efficiency, or obstacle course performance dynamically.
* **⏱️ Solo Practice Optimization:** Initiate runs using a built-in automated audio buzzer countdown sequence, allowing you to train completely alone while data streams safely to the cloud.

---

## 👥 Target Audience

* **The Smart Maker & Hobbyist:** Built for developers who want to experiment with physical telemetry without spending their entire session squinting in the dirt trying to align temperamental sensors.
* **Coaches & Athletes:** Perfect for sports enthusiasts looking for a highly portable, budget-friendly alternative to commercial timing gates that easily cost hundreds of dollars.
* **Embedded Systems Learners:** A comprehensive, real-world blueprint showcasing how physical sensors, local OLED displays, and mobile web dashboards seamlessly communicate in real-time.

---

## 🚀 Key Technical Features

* **Dual Tracking Diagnostics:** Features a standard gate-crossing trigger mode alongside a specialized automated countdown ignition configuration.
* **Responsive Single-Page Application (SPA):** Hosts a local web server directly from the ESP32 memory chip, featuring live lap split tables and persistent historical database logging using browser local storage.
* **Bulletproof Over-The-Air (OTA) Updates:** Includes a connection-stabilized binary upload stream that actively manages internal flash latency to prevent network socket drops during wireless firmware updates.
* **Intelligent Power Management:** Monitors battery depth metrics with live dashboard overlays and triggers an automated hardware deep-sleep sequence after 10 minutes of inactivity.

---

## 🛠️ Hardware Architecture

### Component Inventory
* **Microcontroller:** ESP32 Development Module (e.g., Node32S)
* **Display:** 128x64 I2C SSD1306 OLED Display Screen
* **Primary Sensor Options:** HC-SR04 / JSN-SR04T Ultrasonic Sonar *or* Active Laser Receiver Module
* **Inputs:** TTP223 Capacitive Touch Sensor (or physical tactile push-button)
* **Indicators:** 5V passive Piezo Buzzer & Dual Status LEDs (Red/Green)

### Default Pin Mapping Reference
| Hardware Component | ESP32 GPIO Pin | Direction / Mode |
| :--- | :--- | :--- |
| **Start Button / Touch Sensor** | GPIO 4 | Input (Wakeup Interrupt) |
| **Sensor Trig / Laser Receiver** | GPIO 13 | Input / Output |
| **Sensor Echo (For Sonar Setup)**| GPIO 12 | Input |
| **Status LED (Red)** | GPIO 18 | Output |
| **Status LED (Green)** | GPIO 19 | Output |
| **Active Piezo Buzzer** | GPIO 26 | Output (PWM Tone) |
| **Battery Voltage Divider** | GPIO 34 | Analog Input (ADC) |

---

## 💻 Getting Started & Deployment

1. **Flash the Core:** Open `SprintTimer.ino` inside the Arduino IDE, install the required `Adafruit SSD1306` library dependencies, and upload the code to your ESP32.
2. **Connect to the Network:** Turn on your hardware module, open your phone's Wi-Fi settings, and connect to the password-free **SprintTimer** hotspot network.
3. **Open the Dashboard:** Launch any mobile web browser and navigate to `http://192.168.4.1` to access your local live telemetry control panel.
