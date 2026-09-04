# Screenshot Upload Guide for GitHub Repository

This file lists every screenshot you need to capture from your PDFs and upload to the repository.
Each entry includes: the PDF source, page number, what to screenshot, and where to save it.

---

## 📁 Folder: images/pdf1_final_report/
### Source: BGR_FINAL_REPORT.pdf

| Filename | PDF Page | What to Screenshot |
|----------|----------|--------------------|
| `page1_cover.png` | Page 1 | Full cover page — NIE logo, title, team members, supervisor |
| `page3_intro_circuit.png` | Page 3 | Introduction page — embedded circuit diagram with SBCM, startup, CTAT, PTAT blocks |
| `page4_circuit_diagram.png` | Page 4 | Large CMOS Self-Biased BGR circuit diagram (M3-M12, R1-R3, Q1-Q3) |
| `page5_startup_circuit.png` | Page 5 | Startup Circuit section text description |
| `page6_ptat_ctat_blocks.png` | Page 6 | PTAT block + Reference voltage generation equations |
| `page7_components.png` | Page 7 | Full component table with W/L values and component summary table |
| `page8_schematic.png` | Page 8 | Cadence Virtuoso schematic screenshot (dark background with colored wires) |
| `page8_test_circuit.png` | Page 8 | Test circuit below schematic — BGR block with VDD, VSS, Vs, Vref nodes |
| `page10_dc_temp_analysis.png` | Page 10 | DC temperature analysis plot — V_REF vs temperature (-40 to 125°C) |
| `page11_vref_va_vb_vs.png` | Page 11 | Multi-curve temperature plot — VOUT, Va, Vs, Vb all on one graph |
| `page11_ctat_ptat_analysis.png` | Page 11 | CTAT and PTAT voltage analysis — Va and Vb crossing at 31.4°C |
| `page12_parametric_analysis.png` | Page 12 | Parametric analysis — multiple VREF curves for VDD 0.8V to 11.8V |
| `page13_layout.png` | Page 13 | Full layout screenshot in Cadence Virtuoso (blue/black layout view) |
| `page14_pex.png` | Page 14 | PEX/AV extraction layout view (zoomed in showing parasitic view) |
| `page15_post_layout.png` | Page 15 | Overlay plot — vref_schematic vs vref_layout temperature comparison |

---

## 📁 Folder: images/pdf2_reference/
### Source: BGR.pdf (IISc Mini Project — 45nm)

| Filename | PDF Page | What to Screenshot |
|----------|----------|--------------------|
| `page3_handwritten_notes1.png` | Page 3 | Full handwritten page — BGR intro, CTAT/PTAT diagrams, block diagram, α₁PTAT + α₂CTAT |
| `page4_derivation.png` | Page 4 | Full handwritten page — Mathematical derivation of ∂V_BE/∂T with I_S dependence |
| `page5_ptat_design.png` | Page 5 | PTAT design derivation — two BJT branches, ΔV_BE = V_T ln(n) derivation |
| `page6_combining_ptat_ctat.png` | Page 6 | Combining PTAT and CTAT — α₁ = 18.82 calculation, V_ref = 1.2V |
| `page8_alpha_design.png` | Page 8 | Design of α₁ and α₂ — slope graphs, α₁(85μV) = α₂(1.6mV), V_ref = 1.189V |
| `page9_opamp_bgr.png` | Page 9 | BGR with op-amp design — negative feedback circuit, V₀ = 1.2V derivation |
| `page11_startup_opamp.png` | Page 11 | Startup circuit for op-amp BGR — two operating regions, step-by-step explanation |
| `page12_design_specs.png` | Page 12 | Design specifications — I₀=5μA, R1=3.6kΩ, R2=97.74kΩ, V_ref = α₁PTAT + α₂CTAT |
| `page13_current_mirror_result.png` | Page 13 | Current mirror BGR schematic (45nm) + R2 parametric sweep + BGR slope plot |
| `page14_current_mirror_final.png` | Page 14 | Final 45nm BGR result — CTAT/PTAT/BGR output labeled, 1.014V to 1.005V |
| `page15_dc_operating.png` | Page 15 | DC operating points annotated on schematic — currents, voltages at each node |
| `page16_opamp_result.png` | Page 16 | Op-amp BGR schematic with parametric R2 sweep (96kΩ to 101kΩ) |
| `page17_opamp_final.png` | Page 17 | Op-amp BGR final result — 1.164V to 1.163V, DC operating points |

---

## 📁 Folder: images/pdf3_workshop_notes/
### Source: BGR_VSD_Written_notes_workshop.pdf (VSD Workshop)

| Filename | PDF Page | What to Screenshot |
|----------|----------|--------------------|
| `page1_design_specs.png` | Page 1 | SKY130 design specifications — supply=1.8V, power<60μW, NFET/PFET device datasheet |
| `page2_bjt_resistor.png` | Page 2 | PNP BJT specs (area=11.56μm², β≈12) and RPOLY4H resistor specs for SKY130 |
| `page3_bgr_intro.png` | Page 3 | BGRintroduction — PTAT/CTAT characteristic graphs, BGR block diagram |
| `page4_why_bgr.png` | Page 4 | Why BGR — power fluctuation, battery vs supply vs zener comparison |
| `page5_applications.png` | Page 5 | BGR applications — LDO diagram, ADC block, DAC R-2R ladder with BGR |
| `page6_dc_dc_adc_dac.png` | Page 6 | DC-DC Buck converter and ADC using BGR as reference |
| `page7_bgr_types_architecture.png` | Page 7 | BGR principle (V_BE + KV_T), BGR types — architecture wise and application wise |
| `page8_bgr_types.png` | Page 8 | Self-biased current mirror vs op-amp BGR — advantages/disadvantages + 5 BGR components |
| `page9_ctat_bjt.png` | Page 9 | Why BJT used instead of diode, CTAT generation, three CMOS BJT structures |
| `page9_bjt_cmos_structures.png` | Page 9 | N-well diode, diode-connected NMOS, parasitic PNP BJT cross-sections |
| `page10_ctat_why_vbe_decreases.png` | Page 10 | Why V_BE decreases with temperature — diode current equation derivation, second-order effect |
| `page11_ctat_slopes.png` | Page 11 | CTAT slope variation — Q1=1 (less negative), Q1=8 (more negative), slope vs current |
| `page11_startup_circuit.png` | Page 11 | Startup circuit for BGR — two operating regions, zero current vs normal |
| `page12_ptat_circuit.png` | Page 12 | PTAT voltage generation — current mirror/op-amp/UCVS, V-V₁=V_T×ln(N), slope=0.085mV/°C |
| `page13_design_calc.png` | Page 13 | Design calculations — I_total=33.3μA, I=10μA, R1 formula, SBCM diagram |
| `page14_r1_r2_calc.png` | Page 14 | R1=5.4kΩ derivation, R2 design, CTAT slope = -2mV/°C, PTAT slope = +0.176mV/°C |
| `page15_current_mirror_types.png` | Page 15 | Current mirror analysis — normal vs self-biased analogy ("boss salary vs self-set salary") |
| `page16_sbcm.png` | Page 16 | Self-biased current mirror circuit diagram — MP1, MP2, MN1, MN2, Iref replica of Iout |
| `page17_sbcm_resistor.png` | Page 17 | SBCM with Rs — degenerate bias point issue, stability, I_out equation without VDD |
| `page18_reference_branch.png` | Page 18 | Reference branch circuit — Q3, R2, MP3, Vref = PTAT + CTAT, full BGR circuit |
| `page19_r2_design.png` | Page 19 | Design of R2 — Tempco = ΔVref/Vref/ΔT, condition dVR2/dt + dVQ3/dt = 0, α=9.05, R2=48.9kΩ |
| `page20_design_summary.png` | Page 20 | Summary table — Vt=26mV, I_branch=10μA, R1=5.4kΩ, α=9.05, R2=49kΩ + startup description |
| `page21_startup_steps.png` | Page 21 | Step-by-step startup sequence — net2=VDD→MN3 pulls net6→MPS ON→net1 rises→BGR starts |
| `page22_summary.png` | Page 22 | Complete BGR summary — CTAT/PTAT/SBCM/startup all described, key design equations |
| `page23_tempco_corners.png` | Page 23 | Tempco explanation — TT=21.7ppm, FF=10ppm, SS=45ppm, umbrella shape, second-order effect |
| `page24_mosfet_sizing.png` | Page 24 | MOSFET sizing reasons — PMOS L=2μm (channel-length modulation), NMOS L=7μm (startup), N=8 BJTs |

---

## 📋 How to Take Screenshots

### Using Adobe Acrobat / PDF viewer:
1. Open the PDF file
2. Navigate to the required page
3. Use **Snipping Tool** (Windows) or **Screenshot** (Mac) to capture
4. Save as PNG with the filename specified above
5. Place in the correct folder

### Quick method (Windows):
```
Win + Shift + S → Select area → Save as PNG
```

### Quick method (Mac):
```
Cmd + Shift + 4 → Select area → auto-saved to Desktop
```

### For Cadence screenshots (already in PDF):
The simulation plots in BGR_FINAL_REPORT.pdf pages 10-15 are already screenshots from Cadence Virtuoso — just crop and save those.

---

## 📊 Total Screenshots Required

| Source PDF | Screenshots |
|------------|-------------|
| BGR_FINAL_REPORT.pdf | 15 |
| BGR.pdf (IISc reference) | 13 |
| BGR_VSD_Written_notes_workshop.pdf | 24 |
| **Total** | **52** |
