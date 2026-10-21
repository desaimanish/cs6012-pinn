# RLC circuit PINN (Yug)

Work in progress.

- Main problem: series RLC circuit, `L·d²q/dt² + R·dq/dt + q/C = V(t)`, with initial charge `q(0)` and current `i(0) = dq/dt(0)`.
- Reference: analytical solution (under-, critically and over-damped cases).
- Extension: transmission line (telegrapher's equation) `∂²V/∂x² = LC·∂²V/∂t² + (RC + GL)·∂V/∂t + RG·V`.
