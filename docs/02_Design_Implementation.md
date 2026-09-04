# Design Implementation Guide — 180nm CMOS BGR

## 1. Tools & Environment

| Tool | Purpose |
|------|---------|
| Cadence Virtuoso IC617+ | Schematic entry, layout, simulation |
| Spectre Simulator | DC, transient, parametric analysis |
| Cadence Assura / Pegasus | DRC and LVS verification |
| Cadence Quantus (QRC) | Parasitic Extraction (PEX/AV) |
| GPDK 180 nm PDK | Device models, design rules |

---

## 2. Schematic Entry Steps

### 2.1 Create Library
```
Virtuoso → CIW → File → New → Library
Library Name: BGR_Project
Technology: gpdk180
```

### 2.2 Create Schematic Cellview
```
Library Manager → BGR_Project → New → Cell View
Cell Name: BGR_Core
View: schematic
```

### 2.3 Place Transistors
- PMOS: `gpdk180 → pmos1v` (for 1.8V devices)
- NMOS: `gpdk180 → nmos1v`
- Resistors: `gpdk180 → rpoly2` or `polyhres`

**Key W/L settings per component:**

```
MP1, MP2, MP3 (main mirror):  W=20μm, L=1μm
MP4, MP5 (startup PMOS):      W=5μm,  L=1μm
MN1, MN2 (NMOS mirror):       W=20μm, L=1μm
MN3, MN4, MN5 (startup NMOS): W=10μm, L=1μm
MN6 (degeneration):           W=50μm, L=2μm, m=8
R1 (PTAT resistor):           35.1313 kΩ (polyh)
R2 (reference resistor):      45.316  kΩ (polyh)
R0 (extra):                   20.326  kΩ (polyh)
```

---

## 3. Simulation Setup

### 3.1 DC Temperature Analysis
```
ADE L → Analysis → Choose → DC
  Sweep: Temperature
  Start: -40
  Stop:  125
  Step:  1
Outputs: /VOUT, /Va, /Vb, /Vs
```

### 3.2 Parametric Analysis (Line Regulation)
```
ADE L → Tools → Parametric Analysis
  Variable: VDD
  From: 0.8  To: 11.8  Step: 1
  Inner sweep: Temperature -40 to 125
Output: /VOUT (VREF)
```

### 3.3 Expected Results Summary

| Parameter | Expected Value |
|-----------|---------------|
| V_REF @ 25°C | ~1.20 V |
| V_REF variation (-40 to 125°C) | < 30 mV |
| CTAT/PTAT crossover | ~31°C |
| Startup time | < 2 μs |

---

## 4. Layout Guidelines

### 4.1 Device Placement Strategy

```
[Startup]  [SBCM: MP1,MP2]  [Reference: MP3]
    |            |                  |
   MN4,3      MN1,MN2           [R2, Q3]
              |      |
             [Q1]  [Q2,R1]
```

### 4.2 Matching Techniques
- **PMOS mirrors (MP1, MP2, MP3):** Place in a row, same orientation
- **BJTs (Q1, Q2):** Common-centroid arrangement; Q2 = 8 units of Q1
  ```
  Q2 Q2 Q2 Q2
  Q2 Q1 Q1 Q2    ← Common-centroid for Q1 surrounded by Q2 units
  Q2 Q2 Q2 Q2
  ```
- **Resistors:** Same orientation, same temperature zone

### 4.3 Guard Rings
- Add n-well guard ring around PMOS transistors
- Add p-substrate guard ring (tied to VSS) around NMOS transistors

### 4.4 Metal Routing
- VDD rail: Metal 2 (horizontal) — thick line at top
- VSS rail: Metal 2 (horizontal) — thick line at bottom
- Signal nets: Metal 1 for short connections, Metal 2 for long runs
- Avoid routing signal lines under power rails

---

## 5. DRC Rules (GPDK 180nm Key Rules)

| Rule | Minimum Value |
|------|--------------|
| Poly width | 0.18 μm |
| Diffusion width | 0.22 μm |
| Metal 1 width | 0.23 μm |
| Metal 1 spacing | 0.23 μm |
| Metal 2 width | 0.28 μm |
| Contact size | 0.22 × 0.22 μm |
| Via1 size | 0.26 × 0.26 μm |

---

## 6. LVS Procedure

```
Assura → Run LVS
  Layout: BGR_Project/BGR_Core/layout
  Schematic: BGR_Project/BGR_Core/schematic
  
Check:
  - All device instances match
  - All nets are correctly connected
  - No shorts or opens
```

---

## 7. PEX (Parasitic Extraction)

```
Quantus → Run Extraction
  Mode: RC (extract resistances + capacitances)
  Output: extracted netlist (.spi or .cdl)
  
Post-extraction:
  ADE → Change view from "schematic" to "av_extracted"
  Re-run temperature simulation
  Compare with schematic results
```

---

## 8. Troubleshooting Common Issues

| Issue | Likely Cause | Fix |
|-------|-------------|-----|
| V_REF = 0 V | Startup circuit not working | Check MN3 connection; increase W of startup NMOS |
| V_REF too high/low | R2 value not tuned | Sweep R2 in parametric analysis |
| V_REF varies with VDD | SBCM not working | Check gate connection of MP1, MP2 |
| DRC errors on metal | Minimum spacing violation | Increase spacing in crowded areas |
| LVS mismatch | Missing connection in layout | Compare schematic net names with layout labels |

---

*Source: BGR_FINAL_REPORT.pdf (NIE Mysuru, 180nm implementation)*  
*Reference: BGR_VSD_Written_notes_workshop.pdf (SKY130 workshop)*
