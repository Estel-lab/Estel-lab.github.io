---
title: "Practical Alignment & Commissioning Checklist for a Type-II PPKTP Sagnac SPDC Source"
date: 2026-11-12
summary: "A quantitative, step-by-step experimental guide for aligning a 405 nm pumped Type-II PPKTP polarization-entangled Sagnac interferometer photon-pair source and commissioning Time Tagger coincidences."
tags:
  - Quantum Optics
  - SPDC
  - PPKTP
  - Sagnac Interferometer
  - Experimental Physics
---

Building a polarization-entangled photon-pair source via spontaneous parametric down-conversion (SPDC) in a **405 nm pumped Type-II PPKTP Sagnac interferometer** is a classic exercise in turning nonlinear-optics equations into millimeter- and milliradian-level bench discipline. This checklist distills the quantitative alignment and commissioning sequence we use in practice.

---

### 1. Quasi-Phase Matching (QPM): Separate Spec, Model, and Measurement

For collinear Type-II SPDC ($e \to o + e$ or $y \to y + z$ in KTP principal axes), energy and momentum conservation require:

$$\frac{1}{\lambda_p} = \frac{1}{\lambda_s} + \frac{1}{\lambda_i}, \qquad \Delta k(T) = k_p(T) - k_s(T) - k_i(T) - \frac{2\pi}{\Lambda(T)} = 0$$

where $k_j(T) = 2\pi n_j(\lambda_j, T)/\lambda_j$ is computed from the Sellmeier equations combined with thermo-optic ($\partial n/\partial T$) coefficients, and $\Lambda(T)$ accounts for crystal thermal expansion.

**Practical lab rule**: Never treat a single temperature number as ground truth. Always record three separate values in your notebook:
1. **Manufacturer nominal value**: Specified poling period $\Lambda_0$ and nominal degeneracy temperature.
2. **Sellmeier model prediction**: Calculated $\Delta k(T) = 0$ curve across your pump wavelength (measure the actual 405 nm diode wavelength if possible—a 0.5 nm pump shift noticeably moves the degeneracy temperature).
3. **Measured coincidence peak**: The actual oven setpoint where degenerate signal/idler coincidence counts maximize.

---

### 2. Why the Polarization Sagnac Loop Works — and What Breaks It

In a polarization Sagnac interferometer, a **dual-wavelength polarizing beam splitter (dPBS)** splits a diagonally polarized 405 nm pump into counter-propagating horizontal (H) and vertical (V) beams. Inside the loop, a **dual-wavelength half-wave plate (dHWP)** set to rotate polarization by $90^\circ$ ensures that both clockwise (CW) and counter-propagating (CCW) pump beams enter the Type-II PPKTP crystal with the required pump polarization, while rotating the orthogonally polarized down-converted pair on one side so both directions recombine coherently at the dPBS into a Bell state:

$$|\Psi\rangle = \frac{1}{\sqrt{2}}\left(|H_s V_i\rangle + e^{i\phi}|V_s H_i\rangle\right)$$

Because CW and CCW paths traverse the exact same mirrors and crystal in opposite directions, low-frequency mechanical drift cancels out automatically. However, **spatial mode mismatch** between the two directions destroys indistinguishability and collapses entanglement visibility in the diagonal/anti-diagonal (D/A) basis.

---

### 3. Quantitative Optical Alignment Rules

#### A. Two-Iris Collinearity & Waist Placement
- Establish the primary optical axis with **two separated irises** before placing focusing lenses or the PPKTP crystal.
- Confirm that CW and CCW beams overlap cleanly at both irises and that the focused pump waist sits symmetrically at the crystal center within tight longitudinal tolerance (e.g., $\pm 5\text{ mm}$).
- Use back-reflection / counter-propagating alignment lasers (810 nm alignment beam from the collection fibers) to overlap the signal/idler collection modes directly onto the 405 nm pump path.

#### B. Unified Waveplate Angle Reference (Critical Pitfall)
One of the easiest ways to lose hours during commissioning is mixing up waveplate angle conventions. Always separate **three distinct references**:
1. **Optic axis marking**: The engraved line on the waveplate (check the vendor datasheet to confirm whether it marks the fast or slow axis).
2. **Mount mechanical 0°**: The arbitrary zero tick on the rotation stage.
3. **Calibrated optical 0°**: Defined **strictly relative to the horizontal (H) polarization axis of the corresponding PBS** (found by minimizing/maximizing transmission through the PBS with a power meter).

Once calibrated, log the mechanical offset for every HWP/QWP in the setup so every experimental angle refers unambiguously to the PBS H-axis.

---

### 4. Five-Step Time Tagger Commissioning Sequence

When the geometry is aligned but photon pairs are not yet confirmed, **never rotate multiple waveplates simultaneously**. Follow this strict single-variable sequence:

| Step | Action | Verification Criterion |
|---|---|---|
| **1. Safety & Filtering** | Verify 405 nm pump-blocking long-pass / bandpass filters before unmasking single-photon detectors | Dark counts normal; zero pump leakage under low-power check |
| **2. Unidirectional Pair Check (CW)** | Set pump HWP so power enters one loop direction only; sweep PPKTP temperature and fiber coupling | Clean coincidence peak above accidental background $C_{\text{acc}} \approx R_1 R_2 \tau$ on Time Tagger |
| **3. Reverse Direction (CCW)** | Switch pump HWP by $45^\circ$ to pump only the opposite direction | Comparable single-channel rates and coincidence-to-accidental ratio (CAR) |
| **4. Bidirectional Balancing** | Set pump HWP to $22.5^\circ$ (equal H/V pump); verify both paths contribute equally | Matched CW and CCW singles & coincidences within target tolerance |
| **5. Polarization Correlation** | Only after Steps 1–4 pass, sweep analyzer polarizers in H/V and D/A bases | High visibility in both H/V and D/A bases confirming coherent superposition |

Separating unidirectional pair generation from bidirectional phase/mode overlap turns a frustrating multi-parameter search into a predictable, repeatable commissioning procedure.
