# CFD Validation & Aerodynamic Stall Study: NACA 2412 Airfoil

Two-dimensional numerical investigation of a cambered NACA 2412 airfoil using ANSYS Fluent across angles of attack $\alpha$ = 0°, 5°, 10°, and 15° at $Re \approx 3.42 \times 10^5$, with validation against viscous-inviscid coupled panel method predictions from XFLR5.

## Problem Overview & Simulation Setup

- **Domain:** Upward-tilted farfield domain (Case A) with normal freestream boundary conditions
- **Airfoil Geometry:** NACA 2412, chord length $c$ = 0.1 m (100 mm), unit span $b$ = 1.0 m
- **Flow Conditions:** $V_\infty$ = 50.0 m/s, $\rho$ = 1.225 kg/m³, $\mu$ = 1.7894 × 10⁻⁵ kg/(m·s)
- **Reynolds Number:** $Re \approx 3.42 \times 10^5$
- **Mach Number:** $M_\infty \approx 0.146$
- **Solver:** ANSYS Fluent, steady-state RANS
- **Turbulence Model:** $k$-$\omega$ SST
- **Near-Wall Treatment:** Boundary-layer-resolved mesh with $y^+ \leq 1$
- **Force Accounting:** Freestream-aligned monitor unit vectors for true wind-axis lift and drag decomposition

## Parametric Aerodynamic Performance & Findings

The study tracks lift development, pressure/suction peak evolution, boundary-layer behavior, drag characteristics, and the transition from attached flow to aerodynamic stall.

### $\alpha$ = 0°

- **$C_L$ = 0.2827**
- **$C_D$ = 0.01490**
- **Maximum Velocity:** 62.1 m/s
- **Minimum $C_p$:** ≈ −0.56
- Camber-induced positive lift is observed at zero geometric angle of attack.
- The boundary layer remains largely attached.
- Higher drag is observed in Fluent compared with XFLR5, primarily due to the fully turbulent RANS treatment compared with XFLR5's laminar-to-transition prediction.

### $\alpha$ = 5°

- **$C_L$ = 0.8235**
- **$C_D$ = 0.01970**
- **Maximum Velocity:** 70.0 m/s
- **Minimum $C_p$:** ≈ −1.84
- The airfoil remains in the attached, approximately linear lift regime.
- Fluent predicts a lift coefficient within approximately 1.83% of the XFLR5 prediction ($C_L$ = 0.8087).
- The leading-edge suction peak becomes significantly stronger.
- XFLR5 predicts an upstream movement of the transition location to approximately $x/c$ = 0.426.

### $\alpha$ = 10°

- **$C_L$ = 1.2287**
- **$C_D$ = 0.03520**
- **Maximum Velocity:** 120.0 m/s
- **Minimum $C_p$:** ≈ −5.51
- The airfoil remains in a pre-stall operating regime.
- Fluent predicts a lift coefficient within approximately 2.79% of the XFLR5 prediction ($C_L$ = 1.1954).
- A strong leading-edge suction spike develops within the first 2% of the chord.
- The localized acceleration produces a peak local Mach number of approximately 0.35.
- The wake shear layers become significantly thicker as the angle of attack increases.

### $\alpha$ = 15°

- **$C_L$ range:** 0.360–1.540
- **$C_D$ range:** 0.105–0.350
- **Mean $C_D$:** ≈ 0.228
- **Flow Regime:** Fully separated / stalled
- Massive leading-edge boundary-layer separation occurs.
- The steady-state solution exhibits persistent limit-cycle oscillations of approximately 23 iterations.
- The oscillatory behavior is associated with periodic vortex shedding and indicates the breakdown of the steady-state assumption.
- The flow has transitioned from predominantly attached aerodynamic behavior to a strongly unsteady separated regime.

## Key Conclusion

The $k$-$\omega$ SST RANS model demonstrates good agreement with XFLR5 predictions throughout the attached and pre-stall operating regime, with lift coefficient agreement within approximately 3% from $\alpha$ = 0° to 10°. The simulations successfully capture the progressive intensification of the leading-edge suction peak, increasing drag, boundary-layer development, and wake thickening with increasing angle of attack.

At $\alpha$ = 15°, widespread separation and persistent flow oscillations indicate the onset of aerodynamic stall and the limitations of a steady-state RANS formulation for accurately representing the resulting unsteady vortex dynamics. A time-accurate transient simulation would therefore be more appropriate for detailed investigation of the post-stall flow field and vortex shedding.

## Repository Contents

- `NACA2412_Aerodynamic_Study.tex` — Complete LaTeX source code for the technical report.
- `NACA2412_Aerodynamic_Study.pdf` — Compiled technical report containing methodology, governing equations, solver settings, validation results, and aerodynamic analysis.
- `assets/` — High-resolution velocity magnitude contours, pressure coefficient distributions, surface plots, and monitor convergence histories for all simulated angles of attack.
