# Physics-Informed Neural Networks for Heat Conduction and Electrical Circuits

CS6012 Deep Learning, IIT Bombay: open project, Submission 2 (code-based project).

**Team:** Manish Desai · Yug Milind Thosar

## Problem statement

We train physics-informed neural networks (PINNs) using only the governing equations and their boundary and initial conditions, with no labelled solution data:

1. **2D transient heat conduction** (Manish): `∂u/∂t = α(∂²u/∂x² + ∂²u/∂y²)` on a square plate with prescribed boundary temperatures and initial condition.
2. **Electrical circuit** (Yug): a series RLC circuit, `L·d²q/dt² + R·dq/dt + q/C = V(t)`. Extension: a transmission line governed by the telegrapher's equation.

Results are validated against reference solutions (finite-difference or analytical), and we study when and why the PINN fails.

## Repository layout

| Folder | Contents | Owner |
|---|---|---|
| `heat/` | 2D heat-equation PINN notebook | Manish |
| `rlc_circuit/` | RLC circuit PINN and transmission-line extension | Yug |
| `results/` | Plots and figures (NO results yet) | Both |

## How to run

```bash
pip install -r requirements.txt
jupyter notebook heat/pinn_2d_heat.ipynb
```

The code selects CUDA, Apple MPS or CPU automatically.

## Evaluation plan

- Relative L2 error and maximum absolute error against the reference solution
- Error maps and error-vs-time plots
- PDE/ODE residual and boundary/initial-condition loss curves; training time
- Circuit: current `i = dq/dt`, oscillation frequency and decay rate compared with theory

## Failure-mode analysis (planned)

- Heat: loss weighting (PDE vs boundary terms), sharp gradients (high diffusivity), long time windows
- Circuit: lightly damped high-frequency oscillation (spectral bias), stiff parameters with widely separated time scales, long time horizons, initial-condition weighting

## Status

| Item | Status |
|---|---|
| Network and training-loop scaffold for 2D heat PINN | In progress |
| 2D heat: sampling, PDE residual, loss | In progress |
| Finite-difference reference solution for 2D heat | Planned |
| RLC circuit PINN and analytical reference | Planned |
| Transmission-line extension | Planned |
| Failure-mode analysis | Planned |

## References

- M. Raissi, P. Perdikaris, G. E. Karniadakis, "Physics-informed neural networks," *J. Comput. Phys.* 378, 2019.
- G. E. Karniadakis et al., "Physics-informed machine learning," *Nature Reviews Physics* 3, 2021.
- A. Krishnapriyan et al., "Characterizing possible failure modes in physics-informed neural networks," NeurIPS 2021.
- S. Wang, Y. Teng, P. Perdikaris, "Understanding and mitigating gradient flow pathologies in physics-informed neural networks," *SIAM J. Sci. Comput.* 43, 2021.
