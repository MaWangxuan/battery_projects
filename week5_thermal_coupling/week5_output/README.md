# Week 5: Thermo-Electrochemical Coupling

## Model

- 1D thermal conduction + electrochemical heat generation (FTCS explicit)
- Scale: battery length direction ~10 cm
- Heat sources: uniform volumetric q = q_base * C_rate
- Cooling: volume cooling (h_vol = h_conv * A/V)

## Parameters

- L = 100 mm, nx = 50, dx = 2.0 mm
- dt = 2.0 s, nt = 300, t_total = 600.0 s
- Fo = 0.2401 (stable < 0.5)
- rho = 2500.0, Cp = 1200.0, k = 1.5
- T_amb = 298.15 K
- h_conv = 50.0 W/(m2.K)
- q_base = 2e5 W/m3 (1C)
- A/V = 400 m2/m3, h_vol = 20000.0 W/(m3.K)

## Case 1: Adiabatic vs Cooled (1C)

- Cooled max dT: 9.81 K
- Adiabatic max dT: 39.68 K

## Case 2: C-rate sweep

- 0.5C: max dT = 4.91 K
- 1.0C: max dT = 9.81 K
- 2.0C: max dT = 19.62 K

## Notebook Usage

### Cell Responsibility & Execution Order

| Cell   | Responsibility                              | IO                | Usage                                                                                                                 |
| ------ | ------------------------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------- |
| Cell 1 | Parameters, geometry, stability check       | No                | Must run first. Defines all globals. Edit params (h_conv, q_base, C_rates) here, run once.                            |
| Cell 2 | Thermal-electrochemical solver definition   | No                | Depends on Cell 1 globals. Run once to define `solve_thermal_coupled()`. Edit model (cooling mode, heat source) here. |
| Cell 3 | Case 1 compute + plot (adiabatic vs cooled) | No                | Depends on 1+2. Auto-calls solver and pops 3 figures. Re-run this cell only to refresh.                               |
| Cell 4 | Case 2 compute + plot (C-rate sweep)        | No                | Depends on 1+2. `C_rates` list defined in Cell 1; edit and re-run to change rates.                                    |
| Cell 5 | Export: mkdir, save figs, JSON, README      | **Yes (sole IO)** | Depends on Cell 3/4 `fig_c3`, `fig_c4` etc. Must run last. Overwrites existing outputs.                               |

### Minimum Execution Flow

## Key Physics

1. Heat generation scales linearly with C-rate
2. Volume cooling (h_vol) dominates over boundary-only convection
3. Steady-state dT = q_total / h_vol (balance of generation and removal)
4. Thermal diffusion is ~10^7x faster than Li diffusion

## Files

- cell3_adiabatic_vs_cooled.png
- cell4_crate_comparison.png
- week5_results.json

Generated: 2026-10-10
