# C(n) — Block-Coprime Density

An interactive exploration of the block-coprime density function

```
C(n) = ζ(2) · ∏ₚ (1 − min(n+1, p) / p²)
```

— the natural density of integers coprime to each of `n+1` consecutive moduli, rescaled by `ζ(2)` so `C(0) = 1`. At `n = 1` it reduces to the classical Feller–Tornier constant (`≈ 0.5307`). The site presents this single object as a 2D coprimality lattice, a continuous curve, a Fourier spectrum, and a complex-analytic surface, each numerically verified against direct sieving.

## Pages

1. [P1 — C(n): Block-Coprime Density](https://wessengetachew.github.io/index.html)
2. [P2 — Gap Diagonal Identity](https://wessengetachew.github.io/page2.html)
3. [P3 — Jump Theorem: Saturation Transitions](https://wessengetachew.github.io/page3.html)
4. [P4 — C(n,d): Modular Distance Stratification](https://wessengetachew.github.io/page4.html)
5. [P5 — Half-Barrier Depth Theorem](https://wessengetachew.github.io/page5.html)
6. [P6 — s-Dimensional C_sD(n)](https://wessengetachew.github.io/page6.html)
7. [P7 — Primorial Survivor Count (The Wessen Identity)](https://wessengetachew.github.io/page7.html)
8. [P8 — C(n) Calculator](https://wessengetachew.github.io/page8.html)
9. [P9 — Lattice Sieve: Rail(G,n)](https://wessengetachew.github.io/page9.html)
10. [P10 — Saturated–Active Partition](https://wessengetachew.github.io/page10.html)
11. [P11 — The Continuous Curve C(t)](https://wessengetachew.github.io/page11.html)
12. [P12 — The Jump Spectrum](https://wessengetachew.github.io/page12.html)
13. [P13 — The Complex Extension](https://wessengetachew.github.io/page13.html)
14. [P14 — The Character Twist](https://wessengetachew.github.io/page14.html)
15. [P15 — C(t,s) Surface Explorer](https://wessengetachew.github.io/page15.html)

---

## Page details

### P1 — C(n): Block-Coprime Density
The entry point. States the defining Euler product, its rescaling convention, and the `n = 1` reduction to the Feller–Tornier constant `C_FT = ½(1 + D_FT) ≈ 0.6613`, distinguishing it from the related `D_FT = ∏ₚ(1 − 2/p²)`. Includes the main interactive lattice canvas with Grid/Ring view toggle, 14+ color modes, sector path tracing, inspect mode, gap/diagonal highlighting, π² annotation via Stern–Brocot mediants, global rotation controls, a prime sieve out to 1.5M, and 4K/8K image export.

### P2 — Gap Diagonal Identity
Explores the identity governing gaps along the diagonal of the coprimality lattice, with 3D and Field tab visualizations of how gap structure evolves with `n`.

### P3 — Jump Theorem: Saturation Transitions
Characterizes the points at which `C(n)` "saturates" as `n` crosses each prime threshold, visualizing the discrete jump transitions in the underlying Euler product.

### P4 — C(n,d): Modular Distance Stratification
Decomposes `C(n) = Σ_d w(d) · C(n,d)` by modular distance `d`, stratifying the block-coprime density into components indexed by distance from the diagonal.

### P5 — Half-Barrier Depth Theorem
A Goldbach-flavored exploration of coprime structure, with arc diagrams comparing observed coprime/prime-pair behavior against Hardy–Littlewood predictions.

### P6 — s-Dimensional C_sD(n)
Generalizes the construction to an `s`-dimensional Euler product, `C_sD(n) = ζ(s) · ∏ₚ(1 − min(n+1,p)/p^s)`, extending the block-coprime density beyond the `s = 2` case.

### P7 — Primorial Survivor Count (The Wessen Identity)
Presents the Wessen Identity: for any admissible `k`-tuple `H` and primorial `p#`, the exact count of `h ∈ [1, p#]` coprime to `p#` equals `∏(q − ν_H(q))` over primes `q ≤ p`. Verified with 2,807 independent checks, zero failures — the most rigorously checked result on the site.

### P8 — C(n) Calculator
The most feature-rich page: five visualization views (Grid, Ring, Farey, Lift, Smith Chart), 15 color modes, BigInt arbitrary-precision arithmetic for exact computation at large `n`, 4K/8K exports, and URL state preservation for sharing specific configurations.

### P9 — Lattice Sieve: Rail(G,n)
Visualizes `Rail(G,n)` with Ring and Farey views, seven color schemes, and full keyboard navigation for exploring the rail structure interactively.

### P10 — Saturated–Active Partition
Partitions the lattice into "saturated" and "active" regions as `n` grows, visualizing where the block-coprime condition has stabilized versus where it is still changing.

### P11 — The Continuous Curve C(t)
Extends `C(n)` from integer `n` to a continuous real variable `t`, presenting `C(t)` as a single interpolated curve rather than a discrete sequence.

### P12 — The Jump Spectrum
Computes the Fourier transform of the jump structure of `C(t)`: `F(ξ) = Σₚ e^{i(p−1)ξ} / [p(p−1)]`, which encodes the distribution of primes across residue classes. The spectrum chart is featured prominently in the hero section with a Hide/Show toggle.

### P13 — The Complex Extension
Extends `C(n)` to a complex variable, with verified results on exponent laws, monodromy behavior, and previously unidentified zeros within the critical strip.

### P14 — The Character Twist
Introduces a Dirichlet-character twist on the base construction, examining how the block-coprime density behaves under character-weighted sieving.

### P15 — C(t,s) Surface Explorer
A 3D surface explorer (built with Three.js) rendering `C(t,s)` jointly over the continuous parameter `t` and the dimension parameter `s`, unifying the P6 and P11 generalizations into a single explorable surface.

---

## Notes

- All pages are self-contained single-file HTML/JS applications — no build step, no dependencies beyond what's loaded via CDN.
- Every numerical claim on the site is checked against direct sieving before being presented.
- Where a result is classical (e.g. the Feller–Tornier constant), it is named as such. The site's contribution is the visual and continuous-curve presentation, not new underlying number theory.
