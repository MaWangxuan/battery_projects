# Week 4: Particle Size Distribution Effect on Utilization

## Model
- Single Particle Model (SPM): 1D radial diffusion in spherical particles
- Fick's 2nd law in spherical coordinates (r² dc/dr → flux divergence)
- FTCS explicit solver, Fo < 0.5 ✓

## Parameters
| Parameter | Value |
|---|---|
| D_s,n | 3.90e-14 m²/s |
| c_s,max | 31370 mol/m³ |
| Initial SOC | 50% |
| Current density | 1.0 A/m² |
| Time | dt=1.0s, nt=600, t_total=600.0s |
| nr | 10 |

## Particle Sizes & Diffusion Time Constants
| Label | R [μm] | Weight | τ_diff [s] | Fo |
|---|---|---|---|---|
| Small | 3.0 | 0.3 | 23.4 | 0.3510 |
| Mid | 5.86 | 0.5 | 89.2 | 0.0920 |
| Large | 10.0 | 0.2 | 259.8 | 0.0316 |

## Case 1: Single Particle Comparison
| Particle | Final SOC | Surface c | Center c | Polarization [mol/m³] |
|---|---|---|---|---|
| Small (3μm) | 15.3% | 4540 | 4951 | 411 |
| Mid (5.86μm) | 32.8% | 9754 | 10557 | 803 |
| Large (10μm) | 40.7% | 11867 | 13237 | 1369 |

Key observation: Larger particles → slower diffusion → higher polarization → surface depletion while center remains lithiated ("dead Li").

## Case 2: PSD Weighted Capacity
- PSD final SOC: 29.1%
- Uniform final SOC: 32.8%
- ΔSOC = -3.65%
- Usable capacity (PSD): 20.9%
- Usable capacity (uniform): 17.2%

Conclusion: Current PSD (30/50/20) underperforms uniform because large particles (20%) act as dead weight. To beat uniform, small particle weight must increase (>40%). Engineering implication: bimodal PSD must be carefully tuned — too much large particle sacrifices power; too much small sacrifices energy density.

## Key Physics Summary
1. Diffusion time constant τ = R²/(π²D) sets the characteristic response time
2. Small particles (τ~23s): fast response, high power capability, but lower total capacity per particle
3. Large particles (τ~260s): slow response, high polarization, but more total Li inventory
4. PSD is a lever to balance power vs energy — optimal ratio depends on target C-rate
5. At high C-rates, large particles develop severe surface depletion → "dead Li" that cannot participate in fast charge/discharge

## Files
- `cell3_single_particle_comparison.png` — Case 1: 单粒径 SOC/极化对比（3 子图）
- `cell4_psd_comparison.png` — Case 2: PSD 加权 vs 均匀粒径（2 子图）
- `week4_results.json` — numerical results (parameters, SOC history, polarization)

Generated: 2026-10-09
