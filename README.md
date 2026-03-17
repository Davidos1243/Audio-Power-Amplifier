# High-Fidelity Audio Power Amplifier (Class AB)

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Tools](https://img.shields.io/badge/Tools-LTspice%20%7C%20KiCAD-blue)
![Components](https://img.shields.io/badge/IC-LM3886%20%7C%20OPA2134-orange)

## 📌 Project Overview
This project involves the complete design, simulation, and PCB layout of a **Class AB audio power amplifier** designed specifically for high-frequency speakers (tweeters). The system is built around the Texas Instruments **LM3886** power amplifier IC and features active filtering using the **OPA2134** SoundPlus™ audio operational amplifiers.

### Key Features:
- **Output Power:** 60 W into an 8 Ω load.
- **Amplifier Class:** Class AB.
- **Active Crossover (Filters):**
  - High-Pass Filter (HPF) cutoff frequency: ~400 Hz.
  - Low-Pass Filter (LPF) cutoff frequency: ~20 kHz.
- **Input:** Standard 3.5mm audio jack (PC/Laptop sound card level).
- **Volume Control:** Integrated variable gain stage in the preamplifier.
- **Protection:** Built-in overvoltage, undervoltage, and SPiKe thermal protection (via LM3886).

---

## 📐 Design & Specifications

### Power Calculations
To achieve the target 60 W continuous output power for an 8 Ω speaker:
- Target speaker current: `I_rms ≈ 2.74 A`
- Target speaker voltage: `V_rms ≈ 21.91 V`
- Voltage gain required (for a 1 V input): `G ≈ 21.9 V/V`
- Power Supply: Symmetrical **±35 V** DC.
- Calculated maximum output power: `P_out ≈ 72 W` (providing safe headroom for the 60 W requirement).

### Component Selection
1. **Power Stage (LM3886):** Chosen for its high continuous average output power (up to 68 W), ultra-low distortion (0.03% THD+N), and robust SPiKe protection circuitry.
2. **Pre-amp & Active Filters (OPA2134):** Selected for its true FET-input, extremely low distortion (0.00008%), and excellent dynamic behavior tailored for high-end audio applications.

---

## 💻 LTspice Simulation
Before moving to physical design, the entire circuit was simulated in LTspice to verify stability, frequency response, and power efficiency.

### 1. Frequency Filters (Bode Analysis)
- **High-Pass Filter (Sallen-Key):** 2nd-order active filter. Simulated cutoff frequency (`f_c`) ≈ **399.6 Hz** with a stopband roll-off of -40 dB/decade.
- **Low-Pass Filter:** 2nd-order active filter. Simulated cutoff frequency (`f_c`) ≈ **20.8 kHz** with a stopband roll-off of -40 dB/decade.

### 2. Transient & Power Analysis
- Simulated using a 1 kHz sine wave input.
- Input voltage: `1 V` | Output voltage: `~32 V` (peak).
- Verified the required 60 W average power on the 8 Ω load.
- **Calculated Efficiency:** `η ≈ 71%` (at maximum power output).

*(Note: Add screenshots of LTspice schematic and Bode plots here)*

---

## 🖨️ PCB Design (KiCAD)
The schematic was transferred to KiCAD for PCB layout. The physical layout was designed with strict analog audio guidelines:
- **Signal Flow:** Left-to-right signal path to prevent interference.
- **Trace Widths:** Calculated and adjusted for high-current power and output lines.
- **Grounding:** Large copper ground planes implemented to minimize noise and improve shielding.
- **Thermal Management:** Dedicated space and mounting holes provided for the LM3886 heatsink.
- **I/O:** Strategic placement of the 3.5mm jack, power terminals, and output connectors at the board edges.
- Form Factor: 2-layer FR-4 board, 50.8 x 48.26 mm.

*(Note: Add a 3D render or 2D image of your KiCAD PCB layout here)*

---

## 🛠️ Bill of Materials (BOM)
Key components used in this design (SMD 0805 for passives to maintain a compact footprint):
- **ICs:** 1x LM3886, 2x OPA2134
- **Capacitors (SMD):** 1 nF, 2.2 nF, 100 nF, 120 nF, 220 nF, 1 µF
- **Resistors (SMD):** 100 Ω, 366.9 Ω, 500 Ω, 1.8 kΩ, 2 kΩ, 3.9 kΩ, 6.8 kΩ
- **Connectors:** 3.5mm Audio Jack, Molex SL Screw Terminals
- **Controls:** 10 kΩ THT Potentiometer for volume control

## 📦 Manufacturing
The PCB was cost-analyzed and prepared for fabrication using **JLCPCB** specifications:
- **Material:** FR4-TG135 (1.6mm thickness)
- **Copper Weight:** 1 oz
- **Surface Finish:** HASL

---

## 👨‍💻 Author
**Davyd Tkalich**  
*Electrical and Computer Engineering | Hardware Design Enthusiast*  
[LinkedIn](https://linkedin.com/in/davyd-tkalich-41916b277) | Edmonton, AB, Canada
