# C(n) — The Generalized Feller–Tornier Constant Explorer

**Live demo → [wessengetachew.github.io/FT](https://wessengetachew.github.io/FT/)**

An interactive research tool for studying the one-parameter family of arithmetic constants

$$C(n) = \zeta(2)\cdot\prod_{p\;\text{prime}}\!\left(1 - \frac{\min(n+1,\,p)}{p^2}\right)$$

which measures the natural density of integer pairs $(r, M)$ satisfying the **block-coprimality condition** $\gcd(r, M+j) = 1$ for every $j = 0, 1, \ldots, n$.

---

## What This Is

A single-file, zero-dependency interactive mathematics tool built in HTML/CSS/JavaScript. It combines rigorous analytic number theory with high-quality WebGL2 and Canvas2D visualizations, step-by-step proof derivations, and a full export system — all in one self-contained page.

The central object is a generalization of the classical **Feller–Tornier constant** $C(1) \approx 0.5307$, extended to a family indexed by block length $n+1$.

---

## Mathematical Background

### The Block-Coprimality Condition

For a non-negative integer $n$, a pair $(r, M)$ is **block-coprime** if $r$ is coprime to every integer in the block $\{M, M+1, \ldots, M+n\}$:

$$\gcd(r,\, M+j) = 1 \quad \text{for all } j = 0, 1, \ldots, n$$

### Main Theorem

The natural density of block-coprime pairs exists and equals

$$D(n) = \prod_{p\;\text{prime}} \left(1 - \frac{\min(n+1,\,p)}{p^2}\right)$$

Formally:

$$D(n) = \lim_{N\to\infty}\frac{\#\{(r,M)\in[1,N]^2 : \gcd(r,M+j)=1 \;\forall\, j\leq n\}}{N^2}$$

The normalized constant $C(n) = \zeta(2) \cdot D(n)$ satisfies $C(0) = 1$ exactly.

### Saturation Transitions

Each prime $p$ undergoes a **saturation transition** at $n = p - 1$. When the block length $n+1$ reaches $p$, the local factor changes from the active form $1-(n+1)/p^2$ to the saturated sieve form $1 - 1/p^2$. This creates prime-triggered step changes visible as slope breaks in the $C(n)$ curve — a static Euler product turned into a dynamical object indexed by $n$.

### Asymptotics

By Mertens' theorem, as $n \to \infty$:

$$D(n) \;\sim\; \frac{e^{-\gamma}}{\log(n+1)}$$

where $\gamma \approx 0.5772$ is the Euler–Mascheroni constant.

### Special Values

| $n$ | $C(n)$ | Note |
|-----|--------|------|
| 0 | 1.000000 | Trivial — recovers $6/\pi^2 \cdot \zeta(2) = 1$ |
| 1 | 0.530718 | Classical Feller–Tornier constant |
| 2 | 0.422013 | Saturation at $p=2$ |
| 3 | 0.354366 | |
| $\to\infty$ | $\to 0$ | Rate: $e^{-\gamma}/\log n$ |

---

## Features

### Sticky Navigation Bar
Global $n$ control (slider, step buttons, direct input), live readout of $C(n)$, $D(n)$, saturated prime count, and empirical density. Play button animates all views from $n=0$ upward. Export dropdown with five export options.

### 1 · Calculator
$C(n)$ and $D(n)$ to 8 decimal places, saturation pill strip for the first 30 primes, next saturation threshold, asymptotic decay info.

### 2 · Prime Factor Table
First 60 primes with local factor, log factor, and running partial products $D$ and $C(n)$ converging from below. **Click any row** → Prime Detail Modal with full derivation, forbidden residue set, jump theorem, and prime flags (twin, Sophie Germain, safe).

### 3 · C(n) Chart
Canvas2D plot from $n=0$ to x-max with toggleable overlays: $D(n)$ line, asymptotic curve, log Y axis, saturation jump brackets, current-$n$ marker. Hover anywhere to inspect values.

### 4 · Data Table
Every value $n = 0 \to N$ with $C(n)$, $D(n)$, step ratio, saturated prime count, and event labels. **Click any row** → Data Row Detail Modal with 7-step derivation and partial product convergence visualization.

### 5 · Block-Coprimality Canvas

**Grid View — WebGL2**
A 2D grid where each pixel is a $(r, M)$ pair, colored by coprimality status. The $n+1$-offset GCD check runs per-pixel in a GLSL ES 3.00 fragment shader — interactive at grid sizes up to $G = 2000 \times 2000$. Falls back to Canvas2D automatically.

**Ring View — Canvas2D**
Concentric rings where ring $M$ places dot $r$ at angle $2\pi r/M$. Block-coprime dots are colored by the active mode; the angular placement makes CRT independence visually interpretable. Results cached per $(n, M_{\max})$ so pan and zoom are instant after the first render.

**Six color modes** shared across both views: Sector (r/M hue), 3-state, Survival count gradient, First-failure prime, Gold/dark binary, Density heatmap.

Independent $n$ sliders for grid and ring (lockable to global $n$). Animation strip for canvas-only animation.

### 6 · Step-by-Step Derivation
Eight collapsible MathJax-rendered proof steps covering: formal problem definition with limiting density, CRT reduction, forbidden residue counting, local factor derivation, the Global Density Theorem, verification at $n = 0$ and $n = 1$, the $C(n)$ normalization, and saturation with Mertens asymptotics.

### Export System

| | Format | Description |
|--|--------|-------------|
|  | **Comprehensive PNG** | Multi-panel image (Grid, Ring, Chart) at up to 4K. Custom layout (6 options), title/subtitle/author overlay, legend, formula. Live preview before download. |
|  | **Chart PNG** | $C(n)$ vs $n$ chart at 1920×800 with branded header. Preview before download. |
|  | **Chart CSV** | $n$, $C(n)$, $D(n)$, ratio, saturation count, asymptotic — 0 to x-max |
|  | **Prime Table CSV** | First 60 primes with all local factor columns at 12 decimal places |
|  | **HTML Report** | Self-contained standalone page with embedded chart, prime table, data table |

---

## Technical Notes

### Architecture
- **Single HTML file** — no build step, no npm, no framework, no server required
- **WebGL2 (GLSL ES 3.00)** — grid coprimality loop uses `j ≤ min(u_n, 600)` as loop bound (uniform-controlled, valid in ES 3.00), correct for all $n \leq 600$
- **Canvas2D** — ring, chart, all exports, and WebGL2 fallback
- **MathJax 3** — CDN-loaded for LaTeX in proof steps
- **ResizeObserver** — redraws on container resize, rate-limited via `requestAnimationFrame`

### Computation
- Smallest prime factor sieve to 200,000 — enables O(log n) factorization in tooltips
- $C(n)$ memoized; first 600 values pre-warmed at startup
- Ring results cached per $(n, M_{\max})$ — pan/zoom reuse cache with no recomputation
- Global animation uses a lightweight update path, skipping expensive table rebuilds per frame

### Complexity
| Component | First render | Subsequent pan/zoom |
|-----------|-------------|---------------------|
| WebGL grid | GPU-parallel | GPU-parallel |
| Canvas2D grid fallback | O(G² · n) | O(G² · n) |
| Ring view | O(M² · n) | O(M²) — cached |

---

## Getting Started

The entire application is `index.html`. Open it directly in any modern browser:

```bash
git clone https://github.com/wessengetachew/FT.git
cd FT
open index.html      # macOS
xdg-open index.html  # Linux
# or just drag index.html into your browser
```

Or visit the live page: **[wessengetachew.github.io/FT](https://wessengetachew.github.io/FT/)**

**Browser requirements:** WebGL2 (with Canvas2D fallback), ES2017+, modern CSS (custom properties, grid, flexbox). Tested in Chrome, Firefox, Safari, Edge.

**Quick start:**
1. Drag the **$n$ slider** in the top bar — all six sections update simultaneously
2. Hover over the **ring or grid canvas** to inspect individual $(r, M)$ pairs
3. Click any row in the **Data Table** for a full step-by-step derivation
4. Click **▶ Play** to animate $n$ from 0 upward and watch saturation events propagate
5. Use **↓ Export ▾** to save PNG images or CSV data

---

## Repository Structure

```
FT/
├── index.html    ← entire application (single self-contained file)
└── README.md
```

---

## References

- Hardy, G. H. & Wright, E. M. — *An Introduction to the Theory of Numbers*
- Mertens, F. — $\prod_{p \leq x}(1 - 1/p) \sim e^{-\gamma}/\log x$
- Euler, L. — $\zeta(2) = \pi^2/6$ and Euler product representations
- Fröberg, C. E. — numerical coprimality density computations
- Feller–Tornier theorem on squarefree integer pair density

