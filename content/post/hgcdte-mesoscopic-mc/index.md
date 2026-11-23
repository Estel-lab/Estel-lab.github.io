---
title: "From Microscopic Scattering to Mesoscopic Regulation: Monte Carlo Modeling of HgCdTe APDs"
date: 2026-11-20
summary: "A deep dive into bridging non-parabolic carrier scattering physics with macroscopic excess noise, dark current, and multi-GHz bandwidth in narrow-bandgap HgCdTe avalanche photodiodes."
tags:
  - Device Physics
  - HgCdTe
  - Avalanche Photodiodes
  - Monte Carlo
  - Computational Physics
---

Narrow-bandgap $\text{Hg}_{1-x}\text{Cd}_x\text{Te}$ electron-avalanche photodiodes (e-APDs) occupy a unique position in infrared photonics: because the electron-to-hole impact ionization ratio is extremely asymmetric, they achieve near-noiseless single-carrier multiplication ($F \approx 1\text{–}2$) even at high gain. However, when multiplication regions shrink into the mesoscopic regime, classical local-field models break down. This note summarizes the physics and computational architecture behind our multi-scale modeling efforts.

---

### 1. Where Classical Local Models Fail in Narrow-Bandgap APDs

In McIntyre's classical local-field theory, impact ionization depends solely on the instantaneous local electric field. Real carriers in narrow-bandgap HgCdTe violate this assumption in three coupled ways:

1. **Dead-Space & History Dependence**: An electron must accumulate at least the ionization threshold energy before triggering an impact ionization event. Over a finite multiplication width $W$, this "dead space" regularizes the spatial positions of ionization events and suppresses gain fluctuations below the local-theory limit.
2. **Non-Parabolic Band Dispersion**: Because the conduction band of narrow-bandgap HgCdTe is strongly non-parabolic, carrier effective mass, group velocity, and density of states deviate sharply from parabolic approximations at high kinetic energies.
3. **Neutral Impurity & Polar Optical Phonon (POP) Scattering**: Neglecting neutral impurity (NI) scattering and non-parabolic electron dynamics introduces systematic bias into predicted gain and excess noise (*Optics Letters*, **50**(8), 2723, 2025). Meanwhile, abrupt electric-field spikes trigger intense POP emission that randomizes carrier energy loss and degrades dead-space periodicity.

Combining first-principles band/scattering inputs with stochastic Monte Carlo transport anchors the scattering rates directly to microscopic semiconductor physics rather than empirical fitting parameters.

---

### 2. The Micro–Mesoscopic Coupled Monte Carlo Architecture (MC²)

Simulating thousands of full avalanche chains directly from microscopic scattering for every device geometry is computationally expensive. To bridge microscopic carrier physics with device-scale statistical metrics (gain $M$, excess noise factor $F$, and signal-to-noise ratio $\text{SNR}$), we built **MC²** in C++ with MPI/OpenMP parallelization and an **SQLite carrier-trajectory database** (*IEEE Trans. Electron Devices*, **73**(4), 2038, 2026):

| Layer | Physical Content | Implementation |
|---|---|---|
| **Microscopic Transport** | Non-parabolic dispersion, neutral impurity scattering, POP emission/absorption, impact ionization | C++ stochastic solver (MPI / OpenMP) |
| **Trajectory Database** | Pre-computed and indexed carrier free-flight / ionization statistics across field & energy regimes | SQLite relational store for fast chain sampling |
| **Mesoscopic Avalanche Chain** | Multi-generation stochastic multiplication, spatial ionization distribution, dead-space correlation | Coupled chain generator calibrated against experimental $M(V)$ and $F(M)$ |
| **Macroscopic Device Metrics** | Competing noise budget (Auger, BBT, phonon, excess noise), dark current, SNR, bandwidth | Parameter sweeps & structure optimization |

#### Key Physical Findings
- **2-D Mesoscopic Parameter Space**: Avalanche statistics are governed jointly by the **spatial standard deviation** ($\sigma$) and **mean free path** ($\ell$) of ionization events. Mapping device operating points in $(\sigma, \ell)$ space explains why two structures with similar macroscopic gain can exhibit dramatically different excess noise.
- **High-Gain Noise Competition**: Macroscopic SNR reflects a competition among Auger recombination, band-to-band tunneling (BBT), phonon scattering, and excess noise. At high reverse bias and high gain, **BBT current rapidly becomes the dominant noise source**, fundamentally bounding achievable SNR.
- **Acceleration Meso-Lattice (AML)**: Rather than relying solely on macroscopic geometry tuning, actively engineering the mesoscopic carrier state toward the optimal operating point suppresses stochastic fluctuations at the source—improving SNR from **−8.5 dB (standard ML)** to **−4.2 dB (AML)**.

---

### 3. Electric Field Sculpting: Suppressing Dark Current & Unlocking Multi-GHz Bandwidth

Doping differentials across $p$, $i$, and $n^+$ functional zones strongly shape the electrostatic profile inside an APD (*Infrared Physics & Technology*, **156**, 106608, 2026):

- **The Steep-Field Trap**: Unregulated doping steps create localized high-field peaks. These peaks simultaneously accelerate BBT dark current and trigger excessive POP emission, eroding the dead-space ordering that keeps ENF low.
- **Optimal Sculpted Profile**: A **fully depleted structure with gentle electrostatic gradients** minimizes both statistical gain variance and tunneling dark current—achieving **>10× dark current suppression** compared with unregulated profiles.
- **Bandwidth Scaling**: Full depletion eliminates slow diffusion tails from undepleted regions. Under saturated drift velocity $v_{\text{sat}}$, transit-time-limited bandwidth scales as:

$$f_{3\text{dB}} \approx 0.44\,\frac{v_{\text{sat}}}{W}$$

pushing device bandwidth well into the **multi-GHz** regime for applications in LiDAR, free-space infrared communication, and weak-signal photon counting.

---

### 4. Practical Takeaways for Device Simulation

1. **Always validate both $M(V)$ and $F(M)$**: Matching gain alone is easy to overfit; matching excess noise factor across bias regimes is a much stricter test of scattering and dead-space physics.
2. **Separate transport physics from statistical sampling**: Decoupling microscopic trajectory generation (cached in SQLite) from mesoscopic chain evaluation makes large-scale design sweeps tractable on standard clusters.
3. **Design in mesoscopic coordinates**: Thinking in terms of $(\sigma, \ell)$ and electric-field smoothness turns empirical trial-and-error into a systematic physical design workflow.
