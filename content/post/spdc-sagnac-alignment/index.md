---
title: "Practical Alignment & Commissioning Checklist for a Type-II PPKTP Sagnac SPDC Source"
date: 2026-11-12
summary: "A step-by-step experimental workflow for aligning a 405 nm pumped polarization-entangled Sagnac interferometer photon-pair source and verifying coincidences."
tags:
  - Quantum Optics
  - SPDC
  - PPKTP
  - Sagnac Interferometer
  - Experimental Physics
---

Building a polarization-entangled photon-pair source based on spontaneous parametric down-conversion (SPDC) in a **405 nm pumped Type-II PPKTP Sagnac interferometer** bridges textbook nonlinear optics with strict tabletop tolerances. Below is a practical, quantitative workflow distilled from hands-on alignment and commissioning.

### 1. Quasi-Phase Matching: Distinguish Spec, Model, and Measurement
Before touching mirror mounts, verify the crystal operating point using Sellmeier dispersion relations and the quasi-phase-matching (QPM) condition ($\Delta k = k_p - k_s - k_i - 2\pi/\Lambda(T) = 0$). Always distinguish three values in your lab notebook:
- Manufacturer nominal poling period and degeneracy temperature
- Sellmeier-calculated temperature tuning curve
- Experimentally measured peak coincidence temperature

### 2. Quantitative Optical Alignment Rules
- **Two-Iris Collinearity**: Establish a strict reference axis using two irises separated across the optical path before inserting focusing lenses or the PPKTP crystal, keeping beam waist placement within millimeter-level tolerances around the crystal center.
- **Unified Waveplate Angle Reference**: Never rely blindly on mechanical rotation-stage zero ticks. Define every waveplate angle relative to the **horizontal (H) polarization axis of its corresponding PBS**, and explicitly separate three references: the optic's marked fast/slow axis, the mount's mechanical 0°, and the calibrated optical 0°.

### 3. Sequential Commissioning Order (Never Tune Everything at Once)
Once the loop is geometrically aligned but photon pairs are not yet confirmed, follow a strict one-variable-at-a-time sequence with a Time Tagger:

1. **Detection & Filtering Safety**: Verify pump-rejection filters and dark counts before exposing single-photon detectors.
2. **Unidirectional Pumping (CW or CCW)**: Block one loop direction, optimize crystal temperature and fiber coupling until clean single-direction coincidences appear.
3. **Reverse Direction Verification**: Switch to the counter-propagating direction independently and match coupling efficiency.
4. **Bidirectional Balancing**: Equalize CW and CCW pump amplitudes and collection rates using the input half-wave plate.
5. **Polarization Correlation Measurement**: Only after both paths are individually verified and balanced, sweep analyzer angles to measure visibility in the H/V and D/A bases.
