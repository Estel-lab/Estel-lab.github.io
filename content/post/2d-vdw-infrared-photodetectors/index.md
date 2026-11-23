---
title: "Interface Physics & Architecture Trade-offs in Infrared Photodetectors: Bulk HgCdTe vs. 2D van der Waals Systems"
date: 2026-11-15
summary: "Comparing narrow-bandgap bulk semiconductors and 2D van der Waals heterostructures across Fermi-level pinning, dark current suppression, avalanche noise, and local-field characterization."
tags:
  - Infrared Photodetectors
  - 2D Materials
  - van der Waals Contacts
  - Device Physics
  - HgCdTe
---

Modern infrared optoelectronics spans two very different material paradigms: **mature narrow-bandgap bulk semiconductors** (led by HgCdTe and III-V superlattices) and **emerging two-dimensional (2D) van der Waals (vdW) layered materials**. Rather than viewing them as mutually exclusive competitors, analyzing them through a unified device-physics lens reveals complementary strengths and shared interface bottlenecks (*Infrared Physics & Technology*, **137**, 102114, 2024).

---

### 1. The Contact Bottleneck: Fermi-Level Pinning & van der Waals Contacts

In low-dimensional semiconductors such as violet phosphorus, conventional high-energy metal evaporation damages the fragile surface lattice and introduces dense metal-induced gap states (MIGS). The resulting **Fermi-level pinning** locks the Schottky barrier height independent of the metal work function, inflating contact resistance and capping photoresponse.

By introducing **van der Waals-assisted contacts** (*Science China: Physics, Mechanics & Astronomy*, **66**, 297311, 2023), the metal–semiconductor interface remains atomically sharp and defect-free:
- Fermi-level pinning is effectively suppressed, restoring work-function tunability of the Schottky barrier;
- Carrier extraction efficiency rises without introducing interface trap-assisted recombination;
- Device photoresponse and operational stability improve substantially compared with directly evaporated contacts.

---

### 2. Bulk Narrow-Bandgap APDs vs. 2D/3D Hybrid Architectures

| Physical Metric | Bulk HgCdTe e-APD | 2D / 2D–3D vdW Photodetectors |
|---|---|---|
| **Bandgap & Wavelength** | Continuously tunable across SWIR–MWIR–LWIR via Cd composition $x$ | Tunable via material choice, layer thickness, and band alignment |
| **Multiplication & Noise** | Single-carrier electron avalanche with near-unity excess noise ($F \approx 1\text{–}2$) | High photogating gain possible, though often traded against response speed |
| **Dark Current & Cooling** | Dominated by SRH, Auger, and BBT; requires cryogenic cooling at longer wavelengths | Suppressed thermal generation in select heterostructures; strong potential for room-temperature operation |
| **Integration & Functionality** | Proven focal-plane array (FPA) maturity | Lattice-mismatch-free stacking enables on-chip optoelectronic logic gates (*Nature Photonics*, **18**, 60, 2024) |

---

### 3. Why Local-Field Characterization Connects Both Worlds

Whether optimizing a bulk HgCdTe $p$-$i$-$n$ junction or a 2D vdW heterojunction, macroscopic $I\text{–}V$ curves only tell half the story—device failure, dark-current hotspots, and gain non-uniformity almost always originate from **microscopic local electric-field and interface inhomogeneities** (*Infrared and Laser Engineering*, **51**, 20220277, 2022).

Linking spatially resolved local characterization (such as scanning photocurrent microscopy and local electrical/optical probes) with multi-scale device simulation (TCAD + Monte Carlo) provides a closed loop:
1. Map local material and interface inhomogeneities;
2. Correlate spatial photocurrent/field maps directly to electrical transport and noise mechanisms;
3. Feed diagnosed bottlenecks back into electrostatic field sculpting and contact engineering.
