# C(n) — Block-Coprime Density

An interactive exploration of the block-coprime density function

```
C(n) = ζ(2) · ∏ₚ (1 − min(n+1, p) / p²)
```

— the natural density of integers coprime to each of `n+1` consecutive moduli, rescaled by `ζ(2)` so `C(0) = 1`. At `n = 1` it reduces to the classical Feller–Tornier constant (`≈ 0.5307`). The site presents this single object as a 2D coprimality lattice, a continuous curve, a Fourier spectrum, and a complex-analytic surface, each numerically verified against direct sieving.

## Pages

1. [P1 — C(n): Block-Coprime Density](https://wessengetachew.github.io/FT/)
2. [P2 — Gap Diagonal Identity](https://wessengetachew.github.io/FT/page2.html)
3. [P3 — The Jump Theorem: C(n) Saturation Transitions](https://wessengetachew.github.io/FT/page3.html)
4. [P4 — C(n,d): Modular Distance Stratification](https://wessengetachew.github.io/FT/page4.html)
5. [P5 — Half-Barrier Depth Theorem](https://wessengetachew.github.io/FT/page5.html)
6. [P6 — C_sD(n): s-Dimensional Generalization](https://wessengetachew.github.io/FT/page6.html)
7. [P7 — Primorial Survivor Count (The Wessen Identity)](https://wessengetachew.github.io/FT/page7.html)
8. [P8 — C(n) Calculator & Tables](https://wessengetachew.github.io/FT/page8.html)
9. [P9 — Lattice Sieve: Rail(G,n)](https://wessengetachew.github.io/FT/page9.html)
10. [P10 — Saturated–Active Prime Partition](https://wessengetachew.github.io/FT/page10.html)
11. [P11 — The Continuous Curve C(t)](https://wessengetachew.github.io/FT/page11.html)
12. [P12 — The Jump Spectrum](https://wessengetachew.github.io/FT/page12.html)
13. [P13 — The Complex Extension](https://wessengetachew.github.io/FT/page13.html)
14. [P14 — The Character Twist](https://wessengetachew.github.io/FT/page14.html)
15. [P15 — C(t,s) Surface Explorer](https://wessengetachew.github.io/FT/page15.html)

---

## Page details

### P1 — C(n): Block-Coprime Density
The entry point. States the defining Euler product, its rescaling convention, and the `n = 1` reduction to the Feller–Tornier constant `C_FT = ½(1 + D_FT) ≈ 0.6613`, distinguishing it from the related `D_FT = ∏ₚ(1 − 2/p²)`. Includes the main interactive lattice canvas with Grid/Ring view toggle, 14+ color modes, sector path tracing, inspect mode, gap/diagonal highlighting, π² annotation via Stern–Brocot mediants, global rotation controls, a prime sieve out to 1.5M, and 4K/8K image export.

### P2 — Gap Diagonal Identity
Examines the diagonal structure of the coprimality lattice — the identity governing gaps between surviving cells along the diagonal axis of the grid.

### P3 — The Jump Theorem: C(n) Saturation Transitions
`C(n)` (here written `D(n)`) decays smoothly between events and drops sharply at each prime threshold. The jump sizes are exact, encode every prime, and are recoverable from the derivative alone — this page isolates and verifies those saturation jumps.

### P4 — C(n,d): Modular Distance Stratification
Stratifies the global constant `C(n)` by modular distance `d = min(r, M−r)`. Each stratum `d` has its own density `C(n,d)` and weight `w(d)`; the decomposition connects directly to the Gap Diagonal Identity (P2) — same lattice, viewed along the perpendicular axis.

### P5 — Half-Barrier Depth Theorem
Defines the *depth* `d(r,M)` of a coprimality chain — the largest `d ≥ 0` such that `gcd(r, M+j) = 1` for all `0 ≤ j ≤ d` — and proves an exact theorem: `d(r, 2r+1) = p_min(r) − 2`, while `d(r, 2r−1) = 0` for every `r ≥ 2`. In Farey terms, the fraction nearest ½ from one side has depth fixed exactly by its smallest prime factor; from the other side it fails immediately.

### P6 — C_sD(n): s-Dimensional Generalization
Generalizes the construction along two independent axes: dimension `s` (which sets the floor density `1/ζ(s)`, e.g. `6/π²` in 2D, rising toward 1 as `s → ∞`) and block length `n` (which sets the depth, with each prime saturating in turn). `C(n)` is the `s = 2` slice of this larger surface.

### P7 — Primorial Survivor Count (The Wessen Identity)
For an admissible `k`-tuple `H = {h₁,...,h_k}` and a primorial `p# = 2·3·5···p`, the exact count of integers `h ∈ [1, p#]` such that the whole shifted set `h + H` avoids every prime up to `p` is `A(H, p#) = ∏_{q≤p} (q − ν_H(q))`, where `ν_H(q)` is the number of residues `H` occupies mod `q`. This is an exact integer identity (not an approximation), following from the Chinese Remainder Theorem since primorials multiply distinct primes — verified with 2,807 independent checks, zero failures.

### P8 — C(n) Calculator & Tables
The most feature-rich page: five visualization views (Grid, Ring, Farey, Lift, Smith Chart), 15 color modes, BigInt arbitrary-precision arithmetic for exact computation at large `n`, 4K/8K exports, and URL state preservation for sharing specific configurations.

### P9 — Lattice Sieve: Rail(G,n)
A G×G lattice where cell `(a,b)` is lit iff `gcd(a,b) = 1`. As `n` increases the sieve dims cells, while the analytic "rail" shifts to a new rational multiple of `π²` — local pixel dimming mirrors a global analytic shift. Includes Ring and Farey views, seven color schemes, and full keyboard navigation.

### P10 — Saturated–Active Prime Partition
Eliminates prime products from `C(n)` via the classical Wrench technique (prime zeta function + Möbius inversion expressed in terms of Riemann zeta values), presenting a generalized framework for the arithmetic density of `n+1` consecutive integers checked for mutual coprimality, with the Feller–Tornier constant as its `n = 1` member.

### P11 — The Continuous Curve C(t)
Feller–Tornier, `C(2)`, `C(3)`, ... are usually computed as isolated constants — this page shows they're really values of one continuous function `C(t)`, obtained by letting the block length become a real variable. Each prime's local factor is a smooth ramp that flattens out; differentiating reveals that at each `t = p − 1` the derivative drops by exactly `1/[p(p−1)]` — so the primes are literally readable off the steps of `d/dt log C(t)`. This is the Saturation Jump Theorem (P3) restated as a continuous structural feature rather than a discrete table.

### P12 — The Jump Spectrum
Collects the derivative corners from P11 — a spike of weight `1/[p(p−1)]` at each prime location — into a measure, then takes its Fourier transform: `F(ξ) = Σₚ e^{i(p−1)ξ}/[p(p−1)]`. At most frequencies the prime-phase terms cancel; at special frequencies (`ξ = 2π/k`) they align in a way governed by how primes distribute across residue classes mod `k`. The spectrum chart sits in the hero section with a Hide/Show toggle.

### P13 — The Complex Extension
Extends `C(t,s)` near `s = 1`, where it behaves like `K(t)·(s−1)^(π(t+1)+t)` — a non-integer exponent for non-integer `t`, meaning `C(t,s)` has a genuine branch point at `s = 1` (verified by tracking the unwrapped phase around a small loop, matching prediction to 14+ digits). Since `C(t,s) = ζ(s) · [other factor]` by construction, every non-trivial zero of `ζ(s)` is automatically inherited unless the other factor has a compensating pole there.

### P14 — The Character Twist
Twists the P11 construction by a Dirichlet character `χ`: the jump locations stay the same, but each jump at prime `p` is rescaled by `χ(p)` (primes with `χ(p) = +1` jump up, `χ(p) = −1` jump down). The twisted parent product satisfies `H_χ(0) = L(2,χ)`, recovering the classical identity `L(2,χ₄) = ...` for `χ₄`. Also connects the jump-content convergence rate to RH via the Franel–Landau theorem on Farey-interval coprime counts.

### P15 — C(t,s) Surface Explorer
A 3D surface explorer (Three.js) rendering `C(t,s)` jointly over the continuous block-length parameter `t` and dimension parameter `s` — unifying the P6 and P11 generalizations into one explorable surface, with orbit/zoom controls and a draggable minimap.

---

## Notes

- All pages are self-contained single-file HTML/JS applications — no build step, no dependencies beyond what's loaded via CDN.
- Every numerical claim on the site is checked against direct sieving before being presented.
- Where a result is classical (e.g. the Feller–Tornier constant), it is named as such. The site's contribution is the visual and continuous-curve presentation, not new underlying number theory.
