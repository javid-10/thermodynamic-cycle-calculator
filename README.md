# Thermodynamic Cycle Calculator

> **An interactive, browser-based simulator for constructing, visualizing, and analyzing thermodynamic cycles in real time.**

[![Live Demo](https://img.shields.io/badge/Demo-Live%20App-brightgreen?style=for-the-badge)](https://javid-10.github.io/thermodynamic-cycle-calculator/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

---

## Overview

Most online cycle calculators lock users into rigid presets and obscure the underlying thermodynamic relations. We built this tool to give physics and chemistry students, Olympiad competitors, and educators full freedom to model both classical and custom cycles with complete mathematical transparency.

* **Flexible Cycle Construction:** Build cycles from any combination of five fundamental process types (isentropic, isobaric, isochoric, isothermal, and polytropic).
* **Live Dynamic Visualization:** Real-time generation and updates of $T\text{-}s$ (Temperature–Entropy) and $P\text{-}v$ (Pressure–Specific Volume) diagrams.
* **Instant State & Metric Solvers:** Solves unknown state variables ($P, T, v$), net work ($W_{\text{net}}$), thermal efficiency ($\eta$), heat transfers ($Q_{\text{in}}, Q_{\text{out}}$), and back-work ratio.

---

## Preview

![Thermodynamic Cycle Calculator Dashboard](YOUR_IMAGE_OR_GIF_URL_HERE.png)
*Figure 1: Real-time analysis of an ideal Otto Cycle with dynamic T-s and P-v plotting.*

---

## Authors & Collaboration

* **Javid Bilalov** — *Thermodynamics Modeling, Theoretical Physics & Solvers*
* **Mard Jafarzada** — *Software Architecture, Web UI & Graphical Engine*

---

## Quick Start

1. **Launch:** Open `index.html` in any web browser—no installation, build tools, or dependencies required.
2. **Select or Build:** Choose a pre-configured cycle (Brayton, Rankine, Otto, Diesel, Stirling) or create a custom cycle from scratch by adding state points.
3. **Define State Variables:** Input known parameters ($P$ or $T$) at state points—the built-in solver automatically computes missing state variables.
4. **Specify Processes:** Assign process types connecting adjacent state points.
5. **Analyze:** Watch diagrams, work values, and efficiency update instantaneously as parameters change.

---

## Governing Thermodynamic Relations

Every value calculated in the tool traces back directly to foundational thermodynamic relations.

| Process | Relation | Heat ($q$) | Entropy Change ($\Delta s$) |
| :--- | :--- | :--- | :--- |
| **Isentropic** | $P = \text{const}$ | $0$ | $0$ |
| **Isobaric** | $\frac{T_2}{T_1} = \left(\frac{P_2}{P_1}\right)^{\frac{\gamma - 1}{\gamma}}$ | $c_p \cdot \Delta T$ | $c_p \cdot \ln\left(\frac{T_2}{T_1}\right)$ |
| **Isochoric** | $\frac{P}{T} = \text{const}$ | $c_v \cdot \Delta T$ | $c_v \cdot \ln\left(\frac{T_2}{T_1}\right)$ |
| **Isothermal** | $T = \text{const}$ | $-R \cdot T \cdot \ln\left(\frac{P_2}{P_1}\right)$ | $-R \cdot \ln\left(\frac{P_2}{P_1}\right)$ |
| **Polytropic** | $\frac{T_2}{T_1} = \left(\frac{P_2}{P_1}\right)^{\frac{n - 1}{n}}$ | $c_p \cdot \frac{n - \gamma}{\gamma(n - 1)} \cdot \Delta T$ | $c_p \cdot \frac{n - \gamma}{\gamma(n - 1)} \cdot \ln\left(\frac{T_2}{T_1}\right)$ |

> **Note on First Law Conservation:**  
> Net work is calculated via $W_{\text{net}} = Q_{\text{in}} - Q_{\text{out}}$. This application of the First Law of Thermodynamics guarantees exact work output regardless of how individual process work terms are formulated.

---

## Key Theoretical Considerations

### Polytropic Formulation
The denominator in the polytropic heat equation contains $\gamma$ by design:
$$q = c_p \cdot \frac{n - \gamma}{\gamma(n - 1)} \cdot \Delta T$$
This has been verified both algebraically and via limiting analysis:
* As $n \to \gamma$, heat transfer $q \to 0$, recovering the **isentropic** process.
* As $n \to 0$ or $n \to \infty$, the formulation properly reduces to **isobaric** and **isochoric** heat transfer models.

### Open vs. Closed System Assumption
Isentropic work within the simulator models an **open, steady-flow system** (e.g., turbines and compressors), which aligns with Brayton and Rankine cycles. For closed piston-cylinder systems (e.g., Otto or Diesel cycles), theoretical process work utilizes $c_v$ rather than $c_p$. 

Because overall cycle efficiency ($\eta$) and net work ($W_{\text{net}}$) depend exclusively on boundary heat flows ($Q_{\text{in}}$ and $Q_{\text{out}}$), this assumption **does not impact overall cycle metrics**, though it is noted for precise turbine/compressor work split interpretations.

---

## Current Scope & Edge Cases

* **State Points:** Supports arbitrary system sizes with no hard ceiling on state point additions.
* **Input Validation:** User-entered inconsistent $P/T$ values across isobaric or isochoric boundaries will be calculated numerically without explicit failure warnings.
* **Polytropic Singularities:** Near $n = 1$ (isothermal limit), calculations evaluate as true isothermal processes; values extremely close to $n = 1$ may exhibit numerical sensitivity.

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
