# SDN Load Balancing via Control-Theoretic AQM Router Selection

**M.Tech (Research), Intelligent Communication Systems — IIT Mandi**
**Advisor:** Dr. Sreelakshmi | **Status:** Conference paper complete, journal expansion in progress

---

## The Problem

Software-Defined Networks route traffic dynamically, but most load-balancing schemes (ECMP, static weighted routing) don't account for *how congestion control itself behaves* under Active Queue Management (AQM). Poor router selection can push a network toward oscillation or instability under load — and existing SDN load-balancing literature rarely analyzes this rigorously with control theory.

## Approach

I modeled the joint TCP/AQM system as a set of coupled differential equations and asked: **which router-selection strategy keeps the network provably stable, and where does stability break down?**

- **Fluid model with adaptive routing gain** — introduced a sigmoidal routing gain κᵢ(t) that smoothly shifts traffic toward better-positioned routers as congestion signals change.
- **Katz centrality-based AQM router selection** — ranked routers using capacity-weighted Katz centrality (K = (I − γRᵀ)⁻¹μ, with baseline μⱼ = ‖C‖∞/Cⱼ), so routing decisions reflect both topology position and link capacity, not just queue length.
- **Hopf bifurcation stability analysis** — derived the linearized system matrices (A, B, G, H) for both Compound TCP and DCTCP variants and solved the characteristic equation to find the critical delay τ_c — the exact point where the system transitions from stable to oscillatory.
- **NS-3 validation** — implemented custom multipath routing (both queue-based and rate-based sigmoidal gain) and validated the theoretical predictions on a six-router DCTCP/Compound TCP topology.

## Key Technical Contributions

- Proved the routing matrix update rule preserves row-sum invariance and non-negativity — meaning the adaptive routing scheme stays a valid probability distribution under continuous updates, not just at equilibrium.
- Built DDE (delay differential equation) solvers with ring-buffer history for w(t−τ), using Brent's method for root-finding across parameter sweeps (capacity, router count, α/β fairness parameters).
- Diagnosed and resolved subtle model-correctness issues (sign errors in the characteristic equation, degenerate equilibria causing NaNs in bifurcation sweeps) that would have silently invalidated results.

## Results

- Mapped critical delay τ_c as a function of link capacity (C), number of routers (N_T), and fairness parameter (α) — giving a practical stability boundary network operators can check against.
- NS-3 simulations confirmed the theoretical bifurcation predictions on a realistic multi-router topology under both TCP variants.
- *[Add specific % improvement over baseline / conference name once finalized]*

## Skills Demonstrated

**Control theory:** Nyquist stability, Lyapunov analysis, Hopf bifurcation, linearization
**Programming:** Python (NumPy/SciPy, DDE solvers, numerical root-finding), NS-3 (C++)
**Networking:** SDN architecture, AQM, TCP congestion control (DCTCP, Compound TCP), multipath routing
**Other:** LaTeX/technical writing, IEEE-style research communication

---
*Full simulation code and paper draft available on request.*
