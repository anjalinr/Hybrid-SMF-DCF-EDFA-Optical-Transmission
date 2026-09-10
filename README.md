# Hybrid-SMF-DCF-EDFA-Optical-Transmission

MATLAB-based numerical simulation of a hybrid SMF-DCF-EDFA optical transmission system for long-distance submarine communication.

## Project Overview

This project presents the design and numerical evaluation of a hybrid Single-Mode Fiber (SMF)–Dispersion-Compensating Fiber (DCF)–Erbium-Doped Fiber Amplifier (EDFA) optical transmission system.

The system is evaluated with respect to chromatic dispersion, fiber attenuation, and Kerr nonlinear effects in a long-distance optical link.

## System Architecture

Tx → 100 km SMF → 17 km DCF → 0.5 dB Interconnection Loss → 29 dB EDFA → 40 GHz OBPF → 100 km SMF → 17 km DCF → 0.5 dB Interconnection Loss → 29 dB EDFA → 40 GHz OBPF → Rx

## Main Parameters

- Data rate: 10 Gbps
- Operating wavelength: 1550 nm
- SMF length per span: 100 km
- DCF length per span: 17 km
- SMF dispersion: +17 ps/(nm·km)
- DCF dispersion: −100 ps/(nm·km)
- SMF attenuation: 0.20 dB/km
- DCF attenuation: 0.50 dB/km
- EDFA operating gain: 29 dB
- EDFA noise figure: 5 dB
- Interconnection loss: 0.5 dB/span
- Number of spans: 2

## Analytical Design

For the selected SMF parameters:

- Numerical Aperture (NA) ≈ 0.132
- V-number ≈ 2.19

Since V < 2.405, the selected fiber satisfies the conventional single-mode condition.

The DCF length is calculated using the zero-net-dispersion condition:

100(17) + L_DCF(−100) = 0

giving:

L_DCF = 17 km per span.

The calculated loss per span is:

20 dB (SMF) + 8.5 dB (DCF) + 0.5 dB (interconnection) = 29 dB.

A 29 dB EDFA operating gain is used to compensate this calculated span loss.

## MATLAB Simulation

The optical link is simulated using the Split-Step Fourier Method (SSFM), which numerically models linear and nonlinear fiber propagation over small propagation steps.

The model includes:

- SMF and DCF propagation
- Chromatic dispersion
- Fiber attenuation
- Kerr nonlinear effects
- EDFA gain and ASE noise
- Optical band-pass filtering
- Interconnection loss
- Receiver evaluation

## Simulation Cases

### Case 1 — SMF-only Baseline

Two 100 km SMF spans are simulated without DCF and EDFA.

### Case 2 — Proposed Hybrid System

Each span consists of 100 km SMF, 17 km DCF, 0.5 dB interconnection loss, 29 dB EDFA, and optical band-pass filtering.

The two cases are compared using Q-factor, Q-estimated BER, average received power, and eye diagrams.

## Baseline vs Proposed System

At 0 dBm launch power:

| Metric | SMF-only | Hybrid SMF-DCF-EDFA |
|---|---:|---:|
| Q-factor | 0.633 | 7.110 |
| Q-estimated BER | 2.633e-1 | 5.795e-13 |
| Average received power | −43.35 dBm | −3.23 dBm |

## Launch-Power Evaluation

The official launch-power sweep is from −4 dBm to +8 dBm in 2 dB steps.

The evaluation examines Q-factor, Q-estimated BER, average received power, and analytical nonlinear phase as launch power is varied.

An additional higher-power diagnostic is included to observe the reduction in Q-factor at higher launch powers and the increasing influence of nonlinear effects.

## Results

The generated simulation figures are available in the `Report_Figures` folder.

The figures include:

- Eye diagrams
- Pulse propagation and dispersion compensation
- Launch-power sweep results
- Extended-power diagnostic

## Scope and Limitations

This repository contains a numerical MATLAB model of the proposed optical transmission system.

The simulation assumes that the physical fiber link is operational. The SMF-DCF-EDFA system does not prevent or repair physical submarine cable severing caused by earthquakes.

Environmental mechanical strain is not explicitly modeled.

The reported BER is Q-estimated BER derived from the extracted Q-factor, rather than BER obtained through direct bit-error counting or Monte Carlo simulation.

The extended high-power sweep is used as a diagnostic to observe nonlinear performance degradation and is not presented as a universal operating limit.

## Software

- MATLAB R2021a
- Base MATLAB
- Split-Step Fourier Method (SSFM)
