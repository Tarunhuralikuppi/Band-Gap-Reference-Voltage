# BGR Theory: Complete Mathematical Analysis

## 1. CTAT Full Derivation

### 1.1 Basic CTAT Circuit
A constant current I₀ flows through a diode-connected BJT (base shorted to collector):

```
I₀ = I_S × e^(V_BE / V_T)

Solving for V_BE:
V_BE = V_T × ln(I₀ / I_S)
```

### 1.2 Temperature Dependence of V_BE

To find ∂V_BE/∂T, we need the temperature dependences of V_T and I_S:

**V_T temperature dependence:**
```
V_T = kT/q
∂V_T/∂T = k/q = V_T/T
```

**I_S temperature dependence:**
```
I_S ∝ b × T^(4+m) × e^(-Eg/kT)    where m ≈ -3/2

∂I_S/∂T = I_S × [(4+m)/T + Eg/(kT²)]
```

**Full derivation:**
```
V_BE = V_T × ln(I₀/I_S)

∂V_BE/∂T = (∂V_T/∂T) × ln(I₀/I_S) + V_T × ∂/∂T[ln(I₀/I_S)]

Since I₀ is constant w.r.t. T (∂I₀/∂T = 0):

∂V_BE/∂T = (V_T/T) × ln(I₀/I_S) - V_T × (1/I_S) × (∂I_S/∂T)

Substituting:
∂V_BE/∂T = V_D/T - V_T × (4+m)/T - V_T × Eg/(kT²)
           = V_D/T - V_T(4+m)/T - Eg/(qT)

∂V_BE/∂T = [V_D - (4+m)V_T - Eg/q] / T    ← CTAT equation
```

**Numerical evaluation at T = 300 K:**
```
V_D ≈ 0.7 V
m ≈ -3/2
V_T = 26 mV
Eg/q ≈ 1.2 V

∂V_BE/∂T = [0.7 - (4-1.5)×0.026 - 1.2] / 300
          = [0.7 - 0.065 - 1.2] / 300
          = -0.565 / 300
          ≈ -1.88 mV/°C

(Some textbooks use -1.6 mV/°C or -1.5 mV/°C — depends on operating point)
```

---

## 2. PTAT Full Derivation

### 2.1 Two-BJT Configuration

Use two BJTs: Q₁ (single, area A₁) and Q₂ (N parallel, area N×A₁)

Both carry the same current I₀:

```
V_D = V_T × ln(I₀ / I_S)           [for Q₁, current density = I₀/A₁]

V_D₁ = V_T × ln(I₀ / (N×I_S))     [for Q₂, current density = I₀/(N×A₁)]
```

### 2.2 Extracting PTAT

```
V_D - V_D₁ = V_T × ln(I₀/I_S) - V_T × ln(I₀/(N×I_S))
            = V_T × [ln(I₀/I_S) - ln(I₀/(N×I_S))]
            = V_T × ln[(I₀/I_S) / (I₀/(N×I_S))]
            = V_T × ln(N)

∴ ΔV_BE = V_T × ln(N)    ← PTAT (I_S terms cancel)
```

Since V_T = kT/q is directly proportional to T:
```
∂(ΔV_BE)/∂T = (k/q) × ln(N) = (V_T/T) × ln(N)

At T = 300 K, N = 8:
∂(ΔV_BE)/∂T = (26 mV / 300) × ln(8)
             = 0.0867 × 2.079
             ≈ 0.176 mV/°C    ← Positive temperature coefficient (PTAT)
```

---

## 3. Cancellation Condition

For zero temperature coefficient of V_ref:

```
V_ref = α₁ × PTAT + α₂ × CTAT
       = α₁ × V_T×ln(N) + α₂ × V_BE

∂V_ref/∂T = 0

→ α₁ × ∂(V_T×ln(N))/∂T + α₂ × ∂V_BE/∂T = 0

→ α₁ × (k/q)×ln(N) + α₂ × (∂V_BE/∂T) = 0

→ α₁ × 85 μV/°C + α₂ × (-1.6 mV/°C) = 0

Setting α₂ = 1:
    α₁ = 1.6 mV / 85 μV = 18.82
```

### 3.1 Final Reference Voltage

```
V_ref = α₁ × V_T + V_D
       = 18.82 × 26 mV + 0.7 V
       = 0.489 V + 0.7 V
       ≈ 1.189 ≈ 1.2 V
```

---

## 4. Self-Biased Current Mirror Analysis

### 4.1 Basic Principle

In a normal current mirror: I_ref is externally set.
In a self-biased current mirror: I_ref is derived from I_out itself.

```
MP1 and MP2 have the same V_GS
∴ I₁ (through MP1) mirrors I₂ (through MP2)
I_ref is a replica of I_out
```

### 4.2 Adding Degeneration Resistor R_S

To uniquely define the operating current:

```
I_out = [μn × Cox × (W/L)_N / 2] × (1/R_S²) × [1 - 1/√k]²

where k = (W/L)_MP2 / (W/L)_MP1

Note: VDD does not appear → supply independent
```

### 4.3 Stability Analysis

Loop gain of the SBCM:
```
A_loop = gm × (r_o || r_o) < 1 (by proper sizing)
∴ Circuit is always stable
```

---

## 5. Tempco Calculation

```
Tempco (ppm/°C) = (ΔV_ref / V_ref) / ΔT × 10⁶

Example:
ΔV_ref = 1.214 V - 1.190 V = 24 mV   (over -40°C to 125°C)
V_ref_avg ≈ 1.202 V
ΔT = 165°C

Tempco = (24 mV / 1.202 V) / 165 × 10⁶
       = 0.01996 / 165 × 10⁶
       ≈ 121 ppm/°C

Note: Actual Tempco depends on the curvature shape.
A better estimate uses the bow of the curve, not just endpoints.
```

---

## 6. PSRR (Power Supply Rejection Ratio)

```
PSRR = ΔV_ref / ΔVDD   (in dB: 20 log₁₀(ΔV_ref / ΔVDD))

Good BGR: PSRR > 40–60 dB at DC
```

The self-biased architecture achieves VDD independence because:
- Both I_ref and I_out come from diode-connected devices
- If VDD changes, both change equally → ratio stays constant

---

*Reference: BGR_FINAL_REPORT.pdf, BGR.pdf (IISc), BGR_VSD_Written_notes_workshop.pdf*
