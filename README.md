# ⏱️ ESP32 Sprint Core Engine & Wireless Telemetry System

An open-source, ultra-portable wireless timing gate designed for automated, hands-free split-second tracking. Built on the ESP32 platform, this system eliminates the frustration of expensive commercial timing setups and tedious hardware alignment, delivering real-time telemetry straight to your smartphone or laptop browser.

---

## 🎯 Project Overview & Use Cases

This project transforms a standard microcontroller into an automated, high-precision **wireless stopwatch**. By leveraging smart proximity sensors, the system captures performance metrics instantly—completely removing human reaction error from the equation.

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
* **Indicators:** 5V Active Piezo Buzzer & Dual Status LEDs (Red/Green)

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
<img width="458" height="504" alt="Screenshot 2026-07-11 215000" src="https://github.com/user-attachments/assets/c0d644e0-a07a-48a5-999b-a4ed13cb136f" />
<img width="482" height="401" alt="Screenshot 2026-07-11 215123" src="https://github.com/user-attachments/assets/033428da-e4b9-4058-839c-deacd521b433" />
<img width="484" height="684" alt="Screenshot 2026-07-11 215030" src="https://github.com/user-attachments/assets/a17ba496-8cac-466c-8a45-425c16e2aa59" />
<img width="246" height="200" alt="image" src="https://github.com/user-attachments/assets/457e1095-969e-479e-9f46-db9a55376be9" />


## 🔮 Future Development & Sensor Evolution

While the initial build leveraged a laser-based trigger system, I am currently transitioning the core sensing mechanism to ultrasonic sonar to resolve ongoing alignment frustrations and improve real-world usability in outdoor environments.

### Roadmap for Sensor Upgrades:
* **Refining Sonar Precision:** Developing software-side signal filtering to compensate for the "detection cone" and minimize latency caused by the speed of sound.
* **Transitioning to ToF (Time-of-Flight):** My long-term plan is to migrate from basic sonar to high-precision Laser Time-of-Flight sensors (like the VL53L1X). This will provide the accuracy of a light-based system without the headache of manual, sub-millimeter receiver alignment.
* **Environmental Hardening:** Engineering a modular, weather-resistant housing for the JSN-SR04T waterproof sonar probe to allow for permanent outdoor track installations.
* **Multi-Gate Synchronization:** Implementing an ESP-NOW mesh network so multiple gate modules can communicate wirelessly, allowing for complex multi-split timing across an entire agility course.

