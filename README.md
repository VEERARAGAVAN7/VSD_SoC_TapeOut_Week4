# ⚡ CMOS Circuit Design (Sky130-style) — Week 4

<div align="center">

![RISC-V](https://img.shields.io/badge/RISC--V-SoC%20Tapeout-blue?style=for-the-badge&logo=riscv)
![VSD](https://img.shields.io/badge/VSD-Program-orange?style=for-the-badge)
![India](https://img.shields.io/badge/Made%20in-India-saffron?style=for-the-badge)

</div>

<div align="center">

🧩 Device Physics → 🔋 CMOS Inverter → ⚙️ Dynamic Behavior → 🧪 SPICE Simulation → 🎯 Robustness Evaluation

</div>

---

## 📅 Week 4 — CMOS Circuit Design (Sky130-style)

This week focused on **transistor-level CMOS circuit design and simulation** using the **Sky130 PDK**.  
The tasks involved studying **device behavior**, **inverter characteristics**, **dynamic response**, and **robustness** under various process and supply conditions.  
All experiments and simulations were performed using **Smart SPICE**, **Ngspice**, and **Sky130 model files**.

---

### 🧪 Day 1 — Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)

#### 📘 Objective
Understand the **drain current characteristics** of an NMOS transistor with respect to **Vds** and **Vgs**, and differentiate between **linear**, **saturation**, and **cutoff regions**.

#### ⚙️ Key Concepts
- **Linear Region:** Id increases linearly with Vds for small Vds.
- **Saturation Region:** Id becomes constant when Vds > (Vgs − Vth).
- **Cutoff Region:** Id ≈ 0 when Vgs < Vth.

#### 🧰 Lab Work
- Performed **Smart SPICE simulation** for Id–Vds characteristics.
- Used **Sky130 NMOS model** (`sky130_fd_pr__nfet_01v8`) for the simulation.
- Extracted **threshold voltage (Vth)** and identified **region transitions**.

#### 📈 Observations
- Clear transition from **linear** to **saturation** region observed.
- **Saturation current (Id_sat)** increases with **Vgs**.
- Demonstrates how **channel length modulation** affects drain current.

---

### 🧪 Day 2 — Velocity Saturation and Basics of CMOS Inverter VTC

#### 📘 Objective
Analyze **velocity saturation** in short-channel devices and understand the **Voltage Transfer Characteristic (VTC)** of a CMOS inverter.

#### ⚙️ Key Topics
- **SPICE simulation for lower nodes** (deep submicron effects)
- **Drain current vs gate voltage** for long and short-channel devices
- **Velocity saturation model** at higher electric fields
- **VTC characteristics** of a CMOS inverter
- **Lab Experiments:** Id–Vgs and Vt extraction

#### 🧩 CMOS Inverter VTC Summary
- The **VTC curve** shows how Vout changes with Vin.
- **PMOS and NMOS load curves** are merged to get the switching behavior.
- Key parameters include **VIL**, **VIH**, **VOL**, **VOH**, and **Vm** (switching threshold).

#### 📈 Observations
- Short-channel devices show **saturation of carrier velocity** earlier.
- **Inverter VTC** obtained from combined PMOS and NMOS curves.
- Switching threshold shifts with mobility and velocity saturation effects.

#### ✅ Conclusion
Velocity saturation significantly impacts **drain current modeling** and **switching speed** at advanced nodes.  
The **CMOS inverter VTC** effectively demonstrates the balance between **pull-up** and **pull-down** network strengths.

---

### 🧪 Day 3 — CMOS Switching Threshold and Dynamic Simulations

#### 📘 Objective
To determine the **switching threshold voltage (Vm)** and analyze the **dynamic performance** of a CMOS inverter under transient conditions.

#### ⚙️ Key Concepts
- **Switching Threshold (Vm):** Input voltage where Vin = Vout.
- **Rise Time (tr)** and **Fall Time (tf)** measurements.
- **Propagation Delay (tp):** Average delay between 50% input and 50% output transition.

#### 🧰 Simulation Steps
1. Apply a **pulsed input** using `VPULSE` in SPICE.
2. Observe output waveform for **delay** and **transition times**.
3. Measure **tpLH** and **tpHL**.

#### 📈 Observations
- Output follows input with a finite delay due to load capacitance.
- **Rise and fall times** depend on PMOS/NMOS sizing ratio.
- **Switching threshold** remains near Vdd/2 for symmetrical design.

#### ✅ Conclusion
Dynamic simulations validate the **timing behavior** of CMOS inverters.  
Accurate extraction of **delays** is essential for **timing closure** in larger digital circuits.

---

### 🧪 Day 4 — CMOS Noise Margin Robustness Evaluation

#### 📘 Objective
To evaluate the **noise margin** of a CMOS inverter and its effect on static robustness.

#### ⚙️ Key Topics
- **Noise margin voltage parameters (NMH, NML)**
- **Voltage Transfer Characteristic (VTC)** and undefined region
- **Impact of PMOS width variation** on noise margins
- **SPICE-based Noise Margin Extraction**

#### 📈 Observations
- **Noise margins** are determined from VTC slope = −1 points.
- Increasing **PMOS width** enhances **NMH** but may reduce **NML**.
- **Symmetrical design** offers balanced noise robustness.

#### ✅ Conclusion
Noise margins define the **static stability** of digital logic circuits.  
Designers must balance **NMH and NML** by proper transistor sizing to ensure reliable switching under noise disturbances.

---

### 🧪 Day 5 — CMOS Power Supply and Device Variation Robustness Evaluation

#### 📘 Objective
To study the **impact of power supply and process variations** on CMOS inverter robustness.

#### ⚙️ Topics Covered
- **Power Supply Variation:**
  - Effect of reducing `Vdd` on switching threshold and noise margin.
  - Advantages: Power saving, better efficiency.
  - Disadvantages: Reduced noise tolerance and slower switching.
- **Device Variation:**
  - **Etching variation** — deviation in transistor width/length.
  - **Oxide thickness variation (Tox)** — impacts Id and threshold voltage.
- **Smart SPICE Simulation:**  
  Simulated multiple inverter instances under different `Vdd`, `Wp`, and `Wn` conditions using **Sky130 models**.

#### 📈 Observations
- Lower `Vdd` → reduced noise margin and drive current.
- Device variation causes mismatched switching points.
- Wider PMOS → stronger pull-up and delayed high-to-low transition.

#### ✅ Conclusion
Maintaining CMOS inverter robustness requires a balance between **low-power operation** and **process tolerance**.  
Variations in `Vdd`, `W/L`, and `Tox` directly affect circuit performance.  
Proper transistor sizing and voltage-aware design are essential for **reliable CMOS circuits**.

---

## 🌟 Key Learnings from Week 4

- Simulated **Id–Vds** and **Id–Vgs** characteristics of MOSFETs using Sky130 PDK.  
- Observed **velocity saturation** effects and **short-channel behavior**.  
- Extracted **VTC**, **switching threshold**, and **noise margins** from SPICE plots.  
- Understood **dynamic delays** and inverter **timing analysis**.  
- Analyzed **robustness** under **power supply** and **device variations**.

---

## 🙏 **Acknowledgment**

<div align="center">

### 🏆 **Program Leadership & Support**

I sincerely thank [**Kunal Ghosh**](https://github.com/kunalg123) and Team **[VLSI System Design (VSD)](https://vsdiat.vlsisystemdesign.com/)** for their guidance and mentorship throughout **Week 4 — CMOS Circuit Design (Sky130-style)** of the **RISC-V SoC Tapeout Program**.

</div>

---

## 📈 **Weekly Progress Tracker**

![Week 1](https://img.shields.io/badge/Week%201-RTL%20Foundations-success?style=flat-square)
![Week 2](https://img.shields.io/badge/Week%202-SoC_Design%20Flow-success?style=flat-square)
![Week 3](https://img.shields.io/badge/Week%203-STA-success?style=flat-square)
![Week 4](https://img.shields.io/badge/Week%204-CMOS%20Design-brightgreen?style=flat-square)

### 🚀 **Journey Continues...**

In the upcoming weeks, I will explore **physical design**, **floorplanning**, **timing closure**, and finally prepare the **RISC-V SoC for tapeout readiness** 🚀

---

**🔗 Program Links:**

[![VSD Website](https://img.shields.io/badge/VSD-Official%20Website-blue?style=flat-square)](https://vsdiat.vlsisystemdesign.com/)  
[![RISC-V](https://img.shields.io/badge/RISC--V-International-green?style=flat-square)](https://riscv.org/)  
[![Efabless](https://img.shields.io/badge/Efabless-Platform-orange?style=flat-square)](https://efabless.com/)

**👨‍💻 Participant:** [VEERARAGAVAN7](https://github.com/VEERARAGAVAN7)

