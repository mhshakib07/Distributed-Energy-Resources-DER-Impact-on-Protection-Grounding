# ⚡ DER Impact on Protection & Grounding

## 📘 Overview
This project was developed as part of **ENEL 676 – Distributed Energy Resources** at the University of Calgary. It investigates the impact of integrating Distributed Energy Resources (DER), specifically synchronous generators, on **power system protection and grounding performance**.

The study focuses on evaluating:
- **Relay Desensitization Index (DI)**
- **Coefficient of Grounding (CoG)**  
before and after DER integration, and applying mitigation techniques to meet utility requirements.

---

## 🎯 Objectives
- Analyze system behavior without DER (baseline case)
- Evaluate protection performance after DER integration
- Identify protection issues (e.g., relay desensitization)
- Implement mitigation using **Neutral Grounding Resistors (NGR)**
- Ensure compliance with **FortisAlberta DER standards**


## ⚙️ System Description
- **Voltage Level:** 25 kV distribution system  
- **Transformer:** 5 MVA, 25 kV / 480 V (Yg–Δ)  
- **DER Type:** Synchronous generators (parallel configuration)  
- **Analysis Base:** 100 MVA  


## 🔍 Methodology

### 1. Base Case (Without DER)
- Computed sequence impedances (Z₁, Z₂, Z₀)
- Calculated fault current using Thevenin equivalent  
- **Fault Current:** 1031 A  

---

### 2. With DER Integration
- Modeled generator and transformer impedances
- Combined parallel DER branches
- Evaluated system using sequence networks

**Results:**
- Fault Current: 528 A  
- DI: 48.8% ❌ (Fails requirement)  
- CoG: 0.605 ✅  


### 3. Mitigation (NGR Implementation)
- Added **14 Ω Neutral Grounding Resistor (NGR)**
- Updated zero-sequence network

**Results After Mitigation:**
- Fault Current: 931 A  
- DI: 9.69% ✅  
- CoG: 0.773 ✅  


## ⚡ Protection Design

### Breaker Failure Protection (ANSI 50BF)
- Pickup Time: ≤ 0.3 s  
- Backup Trip Time: < 2 s  
- Ensures isolation if primary breaker fails  

Includes:
- Current supervision after trip
- Retrip logic
- Upstream isolation (transfer trip if required)


## 📡 SCADA & Communication

### DNP3 Points Implemented
**Binary Inputs:**
- Breaker status (52A)
- Trip/Fault indication
- Phase A/B/C faults
- Ground fault
- Close block
- RTU health
- Local/Remote status

**Analog Inputs:**
- Voltage (PCC)
- Current (PCC)
- Real Power (MW)
- Reactive Power (MVAr)
- Frequency
- Power Factor

✔ Designed based on **FortisAlberta DER-02 v6.1**


## 🧠 Tools & Software
- **ETAP** – Short circuit analysis & system modeling  
- **MATLAB / Analytical Calculations** – Per-unit and sequence analysis  


## 📊 Key Insights
- DER integration significantly reduces fault current contribution from the grid
- This leads to **relay desensitization**, risking protection failure
- Proper grounding (via NGR) restores:
  - Fault detectability (DI ≤ 10%)
  - Acceptable grounding conditions (CoG ≤ 0.8)

## 📜 References
- FortisAlberta DER-02 (Version 6.1)  
- Interconnection Protection Settings & Commissioning (IPSC Rev. 09)  
- IEEE Standards for DER Interconnection  


## 🚀 Conclusion
DER integration introduces challenges in protection coordination and grounding. However, with proper analysis and mitigation (such as NGR implementation), systems can meet utility standards and maintain reliable operation.
