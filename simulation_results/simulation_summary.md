# Simulation Results — CMOS Self-Biased BGR (180 nm)

All simulations performed using Cadence Virtuoso / Spectre Simulator  
Technology: GPDK 180 nm CMOS | Supply: 1.8 V

---

## 1. DC Temperature Analysis

**Purpose:** Verify temperature stability of V_REF from -40°C to +125°C

**Setup:**
- Analysis: DC sweep
- Variable: Temperature
- Range: -40°C to +125°C (step: 1°C)
- Monitor: /VOUT (= V_REF)

**Results:**

| Temperature (°C) | V_REF (V) |
|-----------------|-----------|
| -40 | 1.214 |
| -20 | 1.213 |
| 0 | 1.211 |
| 25 | 1.207 |
| 40 | 1.204 |
| 60 | 1.201 |
| 80 | 1.197 |
| 100 | 1.194 |
| 125 | 1.190 |

**Total variation:** 24 mV over 165°C range

> 📷 Screenshot: `images/pdf1_final_report/page10_dc_temp_analysis.png`

---

## 2. Node Voltages vs Temperature (VREF, Va, Vb, Vs)

**Purpose:** Confirm correct operation of CTAT, PTAT, and bias nodes

| Node | Behavior | Physical Meaning |
|------|----------|-----------------|
| VOUT (V_REF) | Nearly flat ~1.2 V | Temperature-compensated output |
| Va | Decreasing with T | CTAT node — V_BE of Q1 |
| Vb | Increasing with T | PTAT node — ΔV_BE across R1 |
| Vs | Decreasing with T | Bias node — source voltage of NMOS |

> 📷 Screenshot: `images/pdf1_final_report/page11_vref_va_vb_vs.png`

---

## 3. CTAT and PTAT Analysis

**Purpose:** Verify individual PTAT and CTAT components are correctly generated

**Key observation:** Va (CTAT) and Vb (PTAT) intersect at **31.4°C**

```
At 31.4°C:
  - PTAT contribution = CTAT contribution
  - This is the point of optimum temperature compensation
  - V_REF is flattest at this temperature
```

**Voltage ranges (approximate):**

| Node | At -40°C | At +125°C | Change |
|------|---------|---------|--------|
| Va (CTAT) | ~640 mV | ~520 mV | -120 mV |
| Vb (PTAT) | ~520 mV | ~640 mV | +120 mV |

> 📷 Screenshot: `images/pdf1_final_report/page11_ctat_ptat_analysis.png`

---

## 4. Parametric Analysis — Line Regulation

**Purpose:** Evaluate V_REF stability across supply voltage range

**Setup:**
- Parameter: VDD
- Range: 0.8 V to 11.8 V (step: 1 V)
- For each VDD: temperature sweep -40°C to +150°C

**Result:** V_REF remains nearly constant for all VDD values above minimum operating voltage (~0.8 V). This demonstrates **good line regulation**.

> 📷 Screenshot: `images/pdf1_final_report/page12_parametric_analysis.png`

---

## 5. Post-Layout Simulation Results

**Purpose:** Verify that layout parasitics don't significantly affect circuit performance

![Post-Layout vs Schematic DC Response](../images/simulation_results/post_layout_dc_vref_vs_temp.png)

| Parameter | Schematic (`/Vref_schematic`) | Post-Layout (`/Vref_layout`) | Difference |
|-----------|-------------------------------|-------------------------------|------------|
| V_REF @ low temp | ≈ 1.205 V | ≈ 1.203 V | ≈ 2 mV |
| V_REF @ 150°C | ≈ 1.182 V | ≈ 1.181 V | ≈ 1 mV |
| Overall shape | Monotonically decreasing | Same, tracks closely | Negligible |

**Conclusion:** Layout is correctly implemented. Extracted parasitics cause only ~1–2 mV deviation, and the curves converge further at high temperature.

---

## 6. Reference: IISc 45nm Simulation Results

### Current Mirror BGR (45nm, GPDK)
- R2 optimized at 45 kΩ (minimum temperature slope)
- V_BGR: 1.014 V @ -30°C → 1.005 V @ +150°C
- Total variation: ~9 mV

### Op-Amp BGR (45nm, GPDK)
- R2 optimized at 99.2 kΩ (minimum temperature slope)
- V_BGR: 1.164 V @ -30°C → 1.163 V @ +150°C  
- Total variation: ~1 mV (excellent — op-amp provides much better matching)

> 📷 Screenshots: `images/pdf2_reference/page14_current_mirror_final.png`  
> 📷 Screenshots: `images/pdf2_reference/page17_opamp_final.png`

---

## 7. Performance Summary

| Parameter | This Work (180nm) | IISc CM (45nm) | IISc OA (45nm) |
|-----------|------------------|----------------|----------------|
| Technology | 180 nm | 45 nm | 45 nm |
| V_REF | ~1.20 V | ~1.01 V | ~1.16 V |
| Variation | 24 mV | 9 mV | 1 mV |
| Temp Range | -40 to 125°C | -30 to 150°C | -30 to 150°C |
| Architecture | Self-biased | Self-biased | Op-Amp |
| DRC/LVS | ✅ Passed | N/A | N/A |
| Post-Layout | ✅ Verified | N/A | N/A |
