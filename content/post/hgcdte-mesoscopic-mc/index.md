---
title: "From Microscopic Scattering to Mesoscopic Regulation: Monte Carlo Modeling of HgCdTe APDs"
date: 2026-11-20
summary: "Notes on bridging non-parabolic carrier scattering physics with macroscopic excess noise and bandwidth in narrow-bandgap HgCdTe avalanche photodiodes."
tags:
  - Device Physics
  - HgCdTe
  - Avalanche Photodiodes
  - Monte Carlo
  - Computational Physics
---

Narrow-bandgap $\text{Hg}_{1-x}\text{Cd}_x\text{Te}$ electron-avalanche photodiodes (e-APDs) stand out among infrared photodetectors for their near-noiseless single-carrier multiplication. Yet conventional phenomenological impact-ionization models often fail to capture the true excess noise factor (ENF) and signal-to-noise ratio (SNR) as device dimensions shrink toward the mesoscopic scale.

### 1. Why Microscopic Scattering Corrections Matter
In narrow-bandgap semiconductors, high-energy electrons experience strong **non-parabolic band dispersion** alongside **neutral impurity scattering** and **polar optical phonon (POP) emission**. Neglecting non-parabolic electron dynamics introduces systematic errors in predicted multiplication gain and noise stability. By combining first-principles parameters with Monte Carlo transport simulations (*Optics Letters*, 2025), the microscopic scattering rates can be anchored directly to physical band structure rather than empirical fitting.

### 2. Coupling Microscopic Trajectories to Mesoscopic Avalanche Chains
To bridge carrier-level stochastic transport with device-level statistics, we developed a **microscopic–mesoscopic coupled Monte Carlo framework (MC²)** in C++ backed by an SQLite carrier-trajectory database and MPI/OpenMP parallelization (*IEEE Trans. Electron Devices*, 2026):

- **2-D Parameter Space**: Avalanche chain statistics are governed jointly by the spatial standard deviation ($\sigma$) and mean free path ($\ell$) of ionization events.
- **Competing Noise Mechanisms**: Macroscopic SNR is determined by the competition among Auger recombination, band-to-band tunneling (BBT), phonon scattering, and excess noise—with BBT rapidly dominating at high gain.
- **Acceleration Meso-Lattice (AML)**: Instead of relying solely on macroscopic geometry tuning, actively engineering the mesoscopic carrier state suppresses stochastic gain fluctuations from the source, improving SNR from −8.5 dB (ML) to −4.2 dB (AML).

### 3. Electric Field Sculpting for Low Noise and Multi-GHz Bandwidth
Abrupt doping junctions generate steep local electric fields that trigger intense POP emission, disrupting dead-space periodicity and inflating ENF. By quantifying doping differentials across p/i/n⁺ functional zones (*Infrared Physics & Technology*, 2026), a **fully depleted structure with gentle electrostatic gradients** suppresses tunneling dark current by over an order of magnitude (>10×) while leveraging saturated drift velocity to push bandwidth into the multi-GHz regime.
