# Week 3: 1D Electrolyte Nernst-Planck Transport

## Model
- 1D Nernst-Planck equation (decoupled from DFN)
- FTCS explicit solver
- Domain: L = 100 μm, nx = 50, dx = 2.041 μm
- Time: dt = 1.666e-03 s, nt = 5000, t_total = 8329.9 ms
- Stability: r = D·dt/dx² = 0.1000 (< 0.5 ✓)

## Cases

### Case 1: Pure Diffusion (D only)
- Initial: c(0) = 1050, c(L) = 1000 mol/m³
- Final polarization: c[0]-c[L] = 0.05 mol/m³
- Uniformization time: ~131.6 ms

### Case 2: Diffusion + Migration
- Electric field: E ≈ 100 V/m (leftward)
- Final polarization: c[0]-c[L] = 167.75 mol/m³
- Migration amplifies polarization (vs Case 1 pure diffusion: 0.05)
- Migration flux: 1.052e-03 mol/(m²·s)
- Diffusion flux: -0.000e+00 mol/(m²·s)
- Migration dominated: YES

## Key Physics
1. Pure diffusion alone cannot explain concentration polarization at high C-rates
2. Migration (electric field coupling) significantly modifies Li+ transport
3. In fast-charge scenarios, migration opposes diffusion and amplifies non-uniformity
4. FTCS explicit scheme is stable and accurate for this parameter range (r=0.1)

## Files
- `case1_vs_case2_comparison.png` — 4-panel comparison figure
- `week3_results.json` — numerical results for report

Generated: 2026-10-09
