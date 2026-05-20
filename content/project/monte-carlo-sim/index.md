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

A microscopic-mesoscopic coupled Monte Carlo simulation framework for narrow-bandgap semiconductor avalanche processes.

Developed in C++ with MPI/OpenMP parallelization, the framework implements:

- Full-band carrier transport under non-parabolic dispersion
- Impact ionization, Auger recombination, polar optical phonon scattering
- Sparse sampling algorithms for computational efficiency
- SQLite-based database management for large-scale simulation data

The framework bridges first-principles carrier scattering theory with macroscopic device performance, enabling predictive design of ultra-low-noise HgCdTe avalanche photodiodes.

<!--more-->
