# constraint-demos

**Browser-based constraint theory visualizations and interactive demos.**

Shows constraint snapping, drift curves, hex lattice geometry, and the conservation law in action. Educational/demonstration repo for constraint-theory-core.

## Demos

| File | What It Shows |
|------|---------------|
| `constraint-funnel.html` | Constraint funneling — how problems narrow to exact solutions |
| `drift-race.html` | Drift comparison — shows zero-drift property of Eisenstein integers |
| `hex-snap-playground.html` | Hex lattice snapping — interactive hex grid with constraint snap |

## Quick Start

Open any `.html` file directly in a browser — no server needed. All demos are self-contained single HTML files.

```bash
# Open in browser
open constraint-funnel.html
# or
xdg-open constraint-funnel.html
```

## What These Demos Show

**Constraint funneling:** Real problems have many near-solutions that collapse to one exact solution under constraint theory. The funnel visualizes this collapse.

**Drift race:** Shows that floating-point accumulation drifts over time while Eisenstein integer arithmetic stays exact. Real-world implications for long-running simulations.

**Hex snap:** Interactive hex grid where you can place points and watch them snap to exact Eisenstein coordinates. Demonstrates the zero-drift property visually.

## Related

- [constraint-theory-core](https://github.com/SuperInstance/constraint-theory-core) — Rust library with the actual constraint engine
- [eisenstein-tools](https://github.com/SuperInstance/eisenstein-tools) — CLI benchmarks for the same math
- [flux-isa](https://github.com/SuperInstance/flux-isa) — FLUX bytecode with constraint opcodes

---

*Part of the Cocapn fleet. These demos explain the math behind the FLUX VM.*