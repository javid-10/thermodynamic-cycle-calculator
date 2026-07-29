# Thermodynamic Cycle Calculator

An interactive, browser-based tool for building and analyzing thermodynamic cycles — Brayton, Rankine, Otto, Diesel, Stirling, or any custom mix of isentropic / isobaric / isochoric / isothermal / polytropic processes. Everything updates live: state points, T-s and P-v diagrams, net work, efficiency, heat in/out, back-work ratio.

Built by **Javid Bilalov** (*thermodynamics*) & **Mard Jafarzada** (*software*).

---

## Why We Built It

Most cycle calculators lock you into one preset cycle and hide the math. We wanted a tool that:
* Lets you build any cycle from the five classical process types.
* Shows its work — every number traces back to a specific equation.

---

## Quick Start

1. **Open `index.html`** — no install, works in any browser.
2. **Pick a preset**, or start from scratch and add state points.
3. **At each point**, set P or T (leave the other blank — the solver fills it in).
4. **Pick the process type** connecting each pair of points.
5. **Done!** Diagrams and results update as you go.

---

## The Five Processes at a Glance

| Process | Relation | Heat ($q$) | Entropy ($\Delta s$) |
| :--- | :--- | :--- | :--- |
| **Isentropic** | $P = \text{const}$ | $0$ | $0$ |
| **Isobaric** | $T_2 / T_1 = (P_2 / P_1)^{(\gamma - 1)/\gamma}$ | $c_p \cdot \Delta T$ | $c_p \cdot \ln(T_2 / T_1)$ |
| **Isochoric** | $P / T = \text{const}$ | $c_v \cdot \Delta T$ | $c_v \cdot \ln(T_2 / T_1)$ |
| **Isothermal** | $T = \text{const}$ | $-R \cdot T \cdot \ln(P_2 / P_1)$ | $-R \cdot \ln(P_2 / P_1)$ |
| **Polytropic** | $T_2 / T_1 = (P_2 / P_1)^{(n - 1)/n}$ | $c_p \cdot \frac{n - \gamma}{\gamma(n - 1)} \cdot \Delta T$ | $c_p \cdot \frac{n - \gamma}{\gamma(n - 1)} \cdot \ln(T_2 / T_1)$ |

> **Note:** $W_{net} = Q_{in} - Q_{out}$ (first law) — always exact, no matter how any single process's work is modeled.

---

## One Subtlety Worth Knowing

The polytropic formulas have $\gamma$ in the denominator — not a typo. We checked it two ways: algebraically, and by confirming the limits make sense ($n \to \gamma$ gives $0$, matching isentropic; $n \to 0$ or $\infty$ recovers isobaric/isochoric heat). 

Separately: isentropic work here assumes an **open, steady-flow system** (turbine/compressor) — correct for Brayton/Rankine. A closed piston-cylinder cycle (Otto/Diesel) would technically use $c_v$ instead of $c_p$ for that leg. This doesn't touch $W_{net}$ or efficiency (both depend only on heat, which is the same either way) — it only affects the Turbine/Compressor work split for piston-cycle presets. We left it as a flagged simplification rather than adding a hidden system-type switch.

---

## Known Limits

* No cap on number of state points.
* Won't warn you if you manually enter inconsistent P/T at both ends of an isobaric/isochoric leg — it'll compute something, just maybe not what the label says.
* Polytropic index near exactly $1$ is a genuine mathematical singularity (handled as isothermal); values very close to but not exactly $1$ can look numerically extreme.

---

## License

MIT License
