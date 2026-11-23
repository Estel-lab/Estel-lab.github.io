---
title: MC² — Mesoscopic Monte Carlo Simulation Framework
date: 2024-09-01
tags:
  - C/C++
  - Monte Carlo
  - HgCdTe
  - Avalanche Photodiodes
  - Device Simulation
---

A microscopic–mesoscopic coupled Monte Carlo simulation framework for narrow-bandgap semiconductor avalanche processes, validated against experimental multiplication gain and excess noise factor (ENF) measurements.

Developed in C++ with MPI/OpenMP parallelization and an SQLite carrier-trajectory database, the framework implements:

- Non-parabolic band dispersion with neutral impurity scattering, impact ionization, Auger recombination, and polar optical phonon scattering
- 2-D parameter-space analysis (spatial standard deviation $\sigma$ × mean free path $\ell$) governing avalanche chain statistics
- Quantitative modeling of competing noise mechanisms (Auger, band-to-band tunneling, phonon scattering, and excess noise)
- Acceleration meso-lattice (AML) structure design, achieving significant SNR improvement (AML −4.2 dB vs. ML −8.5 dB)

Published in *IEEE Transactions on Electron Devices* (2026) and *Optics Letters* (2025), and registered as a national software copyright (`2023SR0426369`).

<!--more-->
