# 📡 Infrared Proximity Sensor System
### *Non-Contact Object Detection using LM358 Operational Amplifier Circuitry*

---

> ### ⚠️ Project Status
> **This system has been successfully simulated, practically prototyped, and validated.**

---

## 📋 Project Overview

Object tracking and automated hazard detection are core parts of industrial automation and smart infrastructure. Traditional physical limit switches suffer from mechanical wear and tear, reducing their operational lifetime. Non-contact sensing fixes this issue by tracking nearby environments without any physical contact.

This project introduces an autonomous **Infrared (IR) Proximity Sensor System** engineered to detect nearby objects using infrared reflection mechanics. When an object crosses the sensing field, reflected infrared light trips an analog comparator network to activate visual and audible warning indicators.

### Why This Design?
By using an analog operational amplifier instead of an expensive microcontroller or specialized sensor module, this architecture demonstrates an optimal, highly cost-effective hardware approach. It delivers real-time hazard detection with minimal power consumption, a tiny circuit footprint, and zero code execution delays.

---

## ⚡ Key Features & System Specifications

Below is a summary of the technical specifications and hardware behaviors of the proximity sensor:

| System Parameter | Specification & Implementation Details |
| :--- | :--- |
| **Central Processor** | LM358 Dual Operational Amplifier (Pure Analog Comparator Config) |
| **Sensing Architecture** | High-sensitivity IR Transmitter LED & Photodiode Receiver Pair |
| **Output Indicators** | High-brightness Status LED & Audible Warning Buzzer Array |
| **Calibration Interface** | Manual sensitivity and detection range adjustment via a 10kΩ Potentiometer |
| **Actuation Speed** | Instantaneous pure hardware response time (0ms code propagation delay) |
| **Power Network** | Standard low-voltage operational threshold powered by a 9V DC source |

---

## 🛠️ System Architecture & Mechanics

### 1. Detection Overview
The sensor operates on the principle of infrared light reflection. The IR transmitter LED continuously outputs an invisible light beam into the monitoring zone. Under normal conditions, this light travels forward into open space.

When an object moves into the detection range, it reflects the infrared light beam directly back toward the system. This reflected light strikes the photodiode receiver, lowering its internal resistance and generating an immediate shift in the input signal voltage. The analog comparator captures this divergence, matches it against a pre-calibrated reference threshold, and switches its output state to activate the warning array.

### 2. System Hardware Breakdown
* **LM358 IC:** The brain of the circuit, configured as a high-gain analog comparator to evaluate voltage differentials between the receiver and reference paths.
* **IR Pair (Transmitter & Photodiode):** The optical sensory front-end responsible for emitting infrared flux and detecting bounce-back light levels.
* **10kΩ Potentiometer:** A variable voltage divider that alters the comparator input pin threshold, giving users control over detection distance and noise tolerances.
* **Buzzer & LED Indicators:** Combined audible and visual output devices that toggle simultaneously to signal an object alert.

---

## 📐 Circuit Network Analysis & Calibration

### The Input Voltage Divider Network
To convert optical infrared reflections into a clear voltage signal for the comparator pins, the photodiode is wired into a series network alongside a fixed precision resistor. 

By applying **Kirchhoff’s Voltage Law (KVL)** and performing **Nodal Analysis** across the sensor nodes, the target voltage input ($V_{\text{in}}$) routed to the non-inverting terminal of the LM358 op-amp is governed by the changing resistance of the photodiode ($R_{\text{photo}}$):

$$V_{\text{in}} = V_{\text{cc}} \times \frac{R_{\text{fixed}}}{R_{\text{photo}} + R_{\text{fixed}}}$$

When an object reflects infrared waves onto the photodiode, $R_{\text{photo}}$ drops sharply. This causes the node voltage $V_{\text{in}}$ to climb toward $V_{\text{cc}}$ ($9\text{V}$). 

### Threshold Calibration Using the Potentiometer
To prevent false alarms caused by shifting ambient sunlight or room lighting, the inverting terminal of the LM358 is tied to a variable $10\text{k}\Omega$ potentiometer network. This potentiometer establishes a stable reference voltage ($V_{\text{ref}}$). 

The operational amplifier functions as a high-gain difference calculator following this logic layout:
* When $V_{\text{in}} < V_{\text{ref}}$ (No object present), the output sits at Low ($\sim 0\text{V}$), keeping indicators inactive.
* When $V_{\text{in}} > V_{\text{ref}}$ (Object detected), the output shifts to High ($\sim V_{\text{cc}}$), instantly powering the warning buzzer and LED.

---

## 📊 Simulations and Engineering Validation

The electronic threshold parameters and switching capabilities of this circuit were fully simulated and validated using **Proteus** CAD software.

The simulation testing environment confirmed that the analog network functions reliably under varying lighting conditions. When an object reflection is triggered within the software, the LM358 comparator shifts clean voltage transitions without erratic oscillations or output chattering. This stable step response verifies that the potentiometer layout handles calibration adjustments perfectly, ensuring sharp switching profiles.

---

## 📈 Performance & Empirical Results

The system was fully built on a breadboard and subjected to environmental and distance field tests to compare practical behavior against the software baselines:

* **Simulation vs. Prototyping Baseline:** The physical prototype matched the Proteus circuit logic closely, turning on the visual and audible tracking alarms immediately when objects crossed into the line of sight.
* **Environmental Adaptability:** Small variations were noted between the simulated models and the real-world breadboard circuit. These minor differences stem from background ambient light pollution, component manufacturing tolerances, and minor alignment angles of the IR lenses.
* **Range Management:** The system achieved a stable, adjustable detection range. Adjusting the manual $10\text{k}\Omega$ potentiometer successfully compensated for background lighting noise, restoring consistent sensing behavior.

---

## 👥 Project Metadata & Contributors

### Project Lead & Core Contributors

* **Rayyan Ali Khan** (Project Lead & Core Analytics)
  * *Primary Focus:* **System Evaluation, Validation, Telemetry Modeling & Field Operations.** Led the empirical research and testing pipeline. Designed the comprehensive experimental testing protocols to evaluate practical circuit response times and tracking thresholds. Orchestrated the final hardware system integration review, transformed raw hardware sensor logs into validation baselines, and authored the performance yield analytical models.
* **Ibrahim Asad**
  * *Primary Focus:* **Hardware Engineering & Prototyping.** Managed the physical breadboard layout, component layout optimization, and physical connection integrity. Tracked wire route validation across input/output nodes and verified power delivery from the 9V supply.
* **Wasi ul Murtaza Alvi**
  * *Primary Focus:* **Signal Integration & System Testing.** Verified input signals from the optoelectronic stage, monitored output logic stability under different test scenarios, and compiled sensory response parameters during practical optimization.
* **Hafiz Sharjeel Abdullah**
  * *Primary Focus:* **Network Analysis & Mathematical Modeling.** Conducted the foundational Kirchhoff’s Voltage Law (KVL) calculations and node voltage assessments for the dual voltage divider matrices, mapping light-to-resistance parameters.

### Academic Profile
* **Institution:** National University of Science and Technology (NUST)
* **School:** School of Electrical Engineering and Computer Science (SEECS)
* **Course & Code:** Linear Circuit Analysis (EE-111)

---

## 📄 License
This project is licensed under the **MIT License**. You are free to modify, distribute, and implement this codebase and hardware configuration for personal, academic, or commercial platforms provided that explicit attribution to the original author group is maintained.
