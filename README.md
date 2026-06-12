# C(n) — Block-Coprime Density

**Analytic Number Theory · Wessen Getachew**
[wessengetachew.github.io/FT](https://wessengetachew.github.io/FT)

---

## Series

| Page | Topic |
|------|-------|
| **[Index — C(n)](index.html)** ← you are here | Block-Coprime Density explorer |
| [P2 — Gap Diagonal](page2.html) | Gap Diagonal Identity |
| [P3 — Saturation](page3.html) | Saturation Transitions |
| [P4 — C(n,d) Stratification](page4.html) | Modular Distance Stratification |
| [P5 — Goldbach Structure](page5.html) | Goldbach Coprime Structure |
| [P6 — C_sD(n) Lattice](page6.html) | s-Dimensional Generalisation |
| [P7 — Wessen Identity](page7.html) | Wessen Identity |

---

## What This Page Is

This is the main explorer for **C(n)** — the block-coprime density constant. C(n) measures the natural density of integer pairs (r, M) for which gcd(r, M+j) = 1 for every j = 0, 1, …, n, rescaled by ζ(2) so that C(0) = 1.

At n = 1 it recovers C(1) = ζ(2)·D_FT ≈ 0.5307, where D_FT = ∏_p(1 − 2/p²) is the Feller–Tornier Euler product. The classical Feller–Tornier constant C_FT = ½(1 + D_FT) ≈ 0.6613 is a distinct object.

### Formula

```
C(n) = ζ(2) · ∏_p ( 1 − min(n+1, p) / p² )
```

An exact closed form over all primes p, converging absolutely for every finite n. Computed using all primes up to 1,500,000 (114,155 primes) with an analytic tail correction for p > 1,500,000, giving full double-precision accuracy.

---

## The Block-Coprime Lattice

The hero canvas plots all pairs (r, M) with 1 ≤ r, M ≤ G:

- **Gold** — block-coprime at depth n: gcd(r, M+j) = 1 for all j = 0, …, n
- **Teal** — coprime at j = 0 only (depth < n)
- **Invisible** — not coprime to M

Four views are available:

| View | Description |
|------|-------------|
| **Grid** | Square lattice (r, M) |
| **Ring** | Concentric residue rings; dot r at angle 2πr/M |
| **Farey** | Hyperbolic strip x = r/M, y = log(2/M) |
| **Lift** | Survival dynamics of the block-coprime condition |

### Color Modes (18 total)

Farey angle (2πr/M rainbow), Farey proximity (1/p), lift angle, 3-state (gold/teal/dark), survival depth, block window j-index, saturation profile, fail-prime spectrum, GCD(r,M) spectrum, φ(M)/M density, Möbius μ(M), quadratic residues, r primality, mod class (r mod M / M), rainbow (r/M hue), divisibility count, zero divisors, idempotents, modular distance.

---

## Controls

| Control | Description |
|---------|-------------|
| **N slider** | Depth n — sets the block-coprime threshold. Animate with ▶ Play. |
| **G slider** | Grid size — number of (r, M) rows and columns rendered, up to 5000. |
| **⊞ Finite** | Switch to finite-prime approximation mode. Slider selects how many primes to include: 0 gives ζ(2) (empty product baseline), up to all 114,155 primes ≤ 1,500,000. Colour tracks the convergence gap to the asymptotic value (gold < 0.001%, teal < 0.1%, lime < 1%, coral = far). |
| **p± / p²±** | Step n to the next or previous prime or prime-square saturation point. |
| **Color** | 18 color modes for the hero lattice. Hero-local setting, independent of the global mode. |
| **Label** | Overlay per-cell labels: r/M ratio, depth, GCD, or none. |
| **Gap g** | Highlight only pairs with gap \|M − r\| = g. Off = show all. |
| **Goldbach** | Overlay prime-pair sums for a chosen even N. Pairs mode shows (p₁, p₂) with p₁ + p₂ = N. |
| **Row shift** | Shift columns by a fixed offset for helical/diagonal pattern exploration. |
| **Inspect (⊕)** | Click mode: pin points and read full details (r, M, depth, GCD, gap, angle). |
| **Zoom / Pan** | Scroll to zoom, drag to pan in Ring and Farey views. |
| **Rotation** | Rotate the grid or ring view in steps of 90° or by continuous angle. |

---

## Exports

| Export | Output |
|--------|--------|
| **↓ 4K Export** | 3840 × 5400 poster — title, formula, hero canvas, data footer. Respects current color mode. Includes π² annotation where applicable. |
| **Grid + Ring 8K** | 7680 × 4320 side-by-side with title header and stat footer. |
| **Grid + Farey 8K** | 7680 × 4320 side-by-side with Farey strip as right panel. |
| **Grid PNG** | Hero grid canvas only with stat boxes. |
| **Ring PNG** | Ring view with stat boxes. |
| **Cube 4K** | 3D cube projection export. |
| **Chart PNG / CSV** | Euler product convergence chart or data table. |
| **Data Table CSV** | C(n), D(n), saturation flags, prime indicators for n = 0…N_max. |
| **DOM Page** | Full page snapshot as self-contained HTML. |

---

## π² Annotation

When the displayed C(n) value is a rational multiple of π² — as occurs in finite-prime mode, where the partial product equals ζ(2) · (rational) = (π²/6) · (rational) — the exact closed form is shown in violet beside the decimal.

Examples with finite-prime mode active:

| Primes included | Value | Exact form |
|-----------------|-------|------------|
| 1 (p = 2) | 1.233700… | = π²/8 |
| 2 (p ≤ 3) | 1.096622… | = π²/9 |
| 3 (p ≤ 5) | 1.052757… | = 8π²/75 |
| ∞ (asymptotic) | C(0) = 1 | — |

Detection uses a Stern–Brocot mediants search on val/π² up to denominator 480 with tolerance 2×10⁻⁹. The annotation appears in all canvas exports.

---

## Mathematical Background

C(n) is the exact Euler-product expression for block-coprime density in the modular arithmetic lattice. Key values:

- **C(0) = 1** — all coprime pairs (r, M) with gcd(r, M) = 1; density = 6/π²; rescaling makes this 1
- **C(1) ≈ 0.530712** — the Feller–Tornier lift survival constant; C(1) = ζ(2) · D_FT
- **C(n) → 0** as n → ∞ — the block-coprime condition becomes increasingly restrictive
- **Saturation jumps** occur at prime values of n+1 (where the factor for p = n+1 switches from (1 − (n+1)/p²) = 0 to 1) and at prime-square values

The product telescopes exactly: for n ≥ p − 1, the factor for prime p contributes 1 − 1 = 0 unless n+1 > p, at which point min(n+1, p) = p and the factor is (1 − 1/p) = (p−1)/p. This transition structure is the subject of P3 (Saturation) and P4 (C(n,d) Stratification).

The relationship C(n) = ζ(2) · ∏_{p ≤ n+1} ((p−1)/p) · ∏_{p > n+1} (1 − (n+1)/p²) makes explicit the connection to primorial products and the Wessen Identity on P7.

---

## Computation Notes

- Sieve of Eratosthenes to 1,500,000 — 114,155 primes
- Smallest prime factor (SPF) table to 1,500,000 for factorisation
- Analytic tail correction: log ∏_{p > 1.5M}(1 − (n+1)/p²) ≈ −(n+1) · Σ_{p > 1.5M} p⁻² using the prime zeta function P(2) = Σ_p p⁻² ≈ 0.452247
- C(n) cache for n = 0 … 600 computed at startup
- Block-coprime depth array uses true unbounded depths (Int16Array, per-cell upper bound = r), not capped at any fixed MAX_N — so the grid canvas responds correctly at all values of n

---

*wessengetachew.github.io/FT · June 2026*
