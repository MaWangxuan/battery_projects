# Week 2: PyBaMM DFN Parameter Sensitivity Analysis

## Model
- PyBaMM 26.8, DFN (Doyle-Fuller-Newman) full model
- Parameter set: Marquis2019
- Experiment: 1C discharge (1 A), 2.8–4.2 V window

## Files
- `sensitivity_results.json` — numerical results (final voltage per parameter perturbation)
- `cell3_profiles.png` — internal profiles at end of discharge (c_s neg/pos, c_e, phi_e)
- `cell4_sensitivity.png` — voltage response to ±20% parameter perturbations

## Key Results

### Baseline
- Final voltage: 2.8000 V

### Parameter Sensitivity (low → high final voltage)

| Parameter | Low value | High value | Low final V | High final V | Delta |
|---|---|---|---|---|---|
| Negative electrode active material volume fraction | 0.5 | 0.7 | 2.8000 V | 2.8000 V | -0.0000 V |
| Positive electrode active material volume fraction | 0.4 | 0.6 | 2.8000 V | 2.8000 V | -0.0000 V |
| Negative particle diffusivity [m2.s-1] | 5e-15 | 2e-14 | 2.8000 V | 2.8000 V | +0.0000 V |
| Positive particle diffusivity [m2.s-1] | 5e-15 | 2e-14 | 2.8000 V | 2.8000 V | +0.0000 V |

## Physical Interpretation

1. **Active material volume fraction (neg/pos)**: Controls available Li capacity. Higher ε_s → more active material → slightly lower polarization (more reaction sites distribute current). Most sensitive parameter for capacity, less for voltage curve shape.

2. **Particle diffusivity (neg/pos)**: Controls solid-state Li transport. Lower D_s → concentration gradient inside particles steepens → higher solid-phase overpotential → voltage drops faster. Most sensitive parameter for rate capability (fast charge/discharge).

## Pitfalls Encountered (PyBaMM 26.8 specific)

- `sol["r_n [m]"]` returns 3D array (r×x×t), cannot be used directly as x-axis. Fix: generate `np.linspace(0, R_n, n_r)` manually from `param["Negative particle radius [m]"]`.
- `sol["x [m]"]` also carries time dimension → same fix.
- `"Negative electrode diffusivity [m2.s-1]"` does NOT exist; correct key is `"Negative particle diffusivity [m2.s-1]"` and value is a function, not a number. Must wrap constant as `lambda T, c: D`.
- `axes.flatten()` overwrites matplotlib Axes object with numpy array → use `axes[i, j]` indexing.

## Next Steps
- Week 3: Electrolyte Nernst-Planck 1D transport (decoupled from DFN)
- Week 4: Particle size distribution effect on utilization
- Week 5: Thermal-electrochemical coupling

Generated: 2026-10-08
