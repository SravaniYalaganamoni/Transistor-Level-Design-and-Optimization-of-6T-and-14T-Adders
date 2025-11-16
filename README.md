# Transistor-Level Design and Optimization of 6T and 14T Adders  

---

##  Project Overview
This project focuses on the **design, simulation, layout, and performance optimization** of two transistor-level full adders:

- **6-Transistor (6T) Full Adder**
- **14-Transistor (14T) Full Adder**

The goal is to compare their performance in terms of:

- Power consumption  
- Propagation delay  
- Area utilization  
- Noise robustness  
- Impact of transistor resizing  

The project uses **Cadence Virtuoso** for schematic and layout design and **Synopsys tools** for post-layout simulation and performance analysis.  
Results and methodology are based on the full project document. :contentReference[oaicite:1]{index=1}

---

##  Objectives

- Design transistor-level schematics for 6T and 14T full adders.
- Create layouts using Cadence Virtuoso with proper DRC and LVS checks.
- Perform transient simulations to obtain power and delay.
- Apply **transistor resizing optimization** to improve speed and power.
- Compare both architectures to determine which is better for **low-power VLSI** applications.

---

##  Background

Adders are essential arithmetic building blocks used in:

- Microprocessors  
- DSP systems  
- AI accelerators  
- Cryptographic processors  

The **6T adder** focuses on minimum transistor usage and area reduction.  
The **14T adder** uses a hybrid PTL–CMOS approach to improve speed and reduce threshold loss.

**Trade-offs:**
- 6T → Lower area, possibly higher delay  
- 14T → Higher speed, lower power, slightly larger design  

---

##  Tools & Technologies

| Task | Tools Used |
|------|------------|
| Schematic & Layout | Cadence Virtuoso (GPdk045 45nm PDK) |
| Simulation | Cadence ADE L / Spectre |
| Optimization | Transistor sizing in Virtuoso |
| Post-Layout Analysis | Synopsys Design Compiler / PrimeTime |
| Modeling | Verilog HDL |
| Testbenching | Cadence + Verilog TB |

---

##  Methodology

### **1️ Schematic Design**
- Designed 6T and 14T adders in Virtuoso using CMOS transistors.
- Ensured proper logic for XOR, SUM, and CARRY.
- Verified connectivity using **Check & Save**.

### **2️ Symbol Creation**
- Generated symbols for hierarchical simulation.
- Defined inputs: X, Y, Cin  
- Outputs: Sum, Cout

### **3️ Simulation Setup (ADE L)**
- Used `vpulse` inputs with defined rise/fall times.
- Supply = **1.2V**  
- Performed **transient analysis** for 100 ns.
- Extracted SUM and COUT waveforms and verified truth table.

### **4️ Performance Calculations**
Measured:

- **Propagation Delay (tpdr, tpdf → tp_avg)**
- **Average Dynamic Power (Pavg = VDD × Iavg)**

### **5️ Layout Design**
- Created layouts in Layout XL for both adders.
- Routed using Metal1, Metal2 based on DRC rules.
- Performed:
  - **DRC**
  - **LVS**
  - **Post-layout simulation**

### **6️ Optimization**
- Improved performance using **transistor resizing**.
- Reduced delays and improved power efficiency.

---

##  Results Summary

###  6T Full Adder
| Metric | Value |
|--------|-------|
| Transistors | 6 |
| Avg Delay | ~15.00 ns (after combining tpdf & tpdr) |
| Power | ~72 nW |
| Area | Very small |
| Notes | Good for compact low-power designs |

---

###  14T Full Adder
| Metric | Value |
|--------|-------|
| Transistors | 14 |
| Avg Delay (pre-opt) | ~25.04 ns |
| Avg Delay (optimized) | ~15.02 ns |
| Power | Lower than 6T after optimization |
| Area | Moderate |
| Notes | Best speed–power tradeoff |

---

##  Final Comparison

| Feature | 6T | 14T | Winner |
|--------|----|-----|--------|
| Transistor Count | **6** | 14 |  6T |
| Speed (Delay) | Higher | **Lower after optimization** |  14T |
| Power Consumption | Low | **Lower after optimization** |  14T |
| Area | **Smallest** | Moderate |  6T |
| Noise Margin | Lower | **Higher** |  14T |

###  Final Verdict  
The **14T adder is superior** for **high-performance, low-power VLSI systems** due to better speed and power efficiency.  
The **6T adder** is ideal for **area-constrained ultra-low-power designs**.

---

## 📁 Repository Structure

