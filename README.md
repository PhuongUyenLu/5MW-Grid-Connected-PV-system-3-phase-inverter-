# ☀️ 5 MW Grid-Connected PV System (3-Phase Inverter)

This project models and simulates a **5 MW grid-connected photovoltaic (PV) system** using a **3-phase voltage-source inverter (VSI)** in **MATLAB/Simulink**.  
It demonstrates PV power generation, MPPT control, inverter operation, and grid synchronization under variable irradiance and temperature conditions.

---

## ⚙️ System Overview

The system consists of the following main subsystems:
1. **PV Array** – Generates DC power based on solar irradiance and temperature.
2. **MPPT Control** – Uses a perturb-and-observe algorithm to extract maximum power from the PV array.
3. **DC-Link Converter** – Stabilizes DC voltage before feeding the inverter.
4. **3-Phase Inverter** – Converts DC to AC using sinusoidal PWM (SPWM).
5. **LCL Filter** – Reduces switching harmonics and ensures smooth current waveform.
6. **Grid Connection** – Synchronizes inverter output with the grid to export real power.

---
## ☀️ PV Array Information

**Module:** Newpowa 5 W / 12 V  
**Number of Modules:** 12  

| Parameter | Symbol | Value |
|------------|---------|-------|
| Power Rating | P<sub>mp</sub> | 6.0795 W |
| Short-Circuit Current | I<sub>sc</sub> | 0.37 A |
| Max-Power Current | I<sub>mp</sub> | 0.35 A |
| Open-Circuit Voltage | V<sub>oc</sub> | 20.04 V |
| Max-Power Voltage | V<sub>mp</sub> | 17.37 V |

---

### 🔋 String Configuration
*(4 modules per string)*  

| Parameter | Expression | Value |
|------------|-------------|--------|
| String V<sub>oc</sub> | 4 × 20.04 V | ≈ 80.16 V |
| String V<sub>mp</sub> | 4 × 17.37 V | ≈ 69.48 V |
| String I<sub>mp</sub> | — | ≈ 0.35 A |

---

### ⚡ Parallel Strings
*(3 parallel strings)*  

| Parameter | Expression | Value |
|------------|-------------|--------|
| Array I<sub>sc</sub> | 3 × 0.37 A | = 1.11 A |
| Array I<sub>mp</sub> | 3 × 0.35 A | = 1.05 A |
| Array V<sub>mp</sub> | — | 69.48 V (same as string V<sub>mp</sub>) |
| Array V<sub>oc</sub> | — | 80.16 V (same as string V<sub>oc</sub>) |

---

### ⚙️ Total PV Array Power

$$
P_{\text{array}} = V_{\text{mp,array}} \times I_{\text{mp,array}}
$$

$$
P_{\text{array}} = 69.48 \times 1.05 \approx \mathbf{72.95\ \text{W}}
$$

---


## 🧩 Simulink Model


![Simulink Model Screenshot](Screenshot%202025-10-21%20234707.png)


**Figure 1.** *Simulink model of the 5 MW grid-connected photovoltaic system with MPPT, DC-link control, and 3-phase inverter.*

The model operates in the **continuous simulation mode** and includes key measurements such as:
- PV voltage, current, and power  
- Inverter current and voltage  
- Grid current and voltage  
- DC-link voltage  
- Real and reactive power flow  

---

## 📊 Simulation Parameters

| Parameter | Symbol | Value |
|------------|---------|-------|
| PV Rated Power | P<sub>PV</sub> | 5 MW |
| DC Link Voltage | V<sub>dc</sub> | 800 V |
| Grid Voltage (L-L RMS) | V<sub>ac</sub> | 400 V |
| Switching Frequency | f<sub>sw</sub> | 10 kHz |
| Fundamental Frequency | f<sub>grid</sub> | 60 Hz |
| Filter Type |  | LCL |

---

## 🧠 Control Strategy

- **MPPT Algorithm:** Perturb and Observe (P&O)  
- **DC-Link Voltage Regulation:** PID controller  
- **Inverter Control:** Sinusoidal PWM  
- **Grid Synchronization:** Phase-locked loop (PLL)

---

## 📈 Key Results

The simulation verifies:
- Stable DC-link voltage regulation at 800 V  
- Effective MPPT tracking for changing irradiance  
- Smooth 3-phase grid current with low THD  
- Real power transfer from PV array to the grid  

---



