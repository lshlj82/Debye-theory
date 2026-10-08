# Debye Theory of Solids, Interactively

An interactive, single-page web demo of the Debye theory of solids: why the Einstein model fails at low temperature, how sound waves in a crystal become phonons, Debye's eighth-sphere approximation, the T³ law, the heat capacity of metals, and magnons in a ferromagnet.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Chapter 7, Quantum Statistics; Section 7.5, Debye Theory of Solids, with Problem 7.64). It is a companion to the demos for Sections 7.1 to 7.4 (the grand canonical ensemble, bosons and fermions, degenerate Fermi gases, and blackbody radiation).

## What's inside

**Where the Einstein model fails.** Independent oscillators give C<sub>V</sub> → 3Nk<sub>B</sub> at high temperature but an exponential fall-off at low temperature, while experiments show C<sub>V</sub> ∝ T³.

**Sound waves in a crystal.** An animated row of 12 atoms with fixed ends vibrates in any of its standing-wave modes. Push the mode number past 12 and the demo shows why wavelengths shorter than twice the atomic spacing aren't possible: the atoms sampling a too-short wave move exactly as in a longer mode. The quanta of these modes are phonons, bosons with μ = 0 and three polarizations.

**Debye's spherical cow.** A rotatable 3D view of *n*-space shows the real cube of modes, [1, N<sup>1/3</sup>]³, together with Debye's eighth-sphere of equal volume, n<sub>max</sub> = (6N/π)<sup>1/3</sup>. Modes are colored by whether they lie in both regions, only in the cube, or only in the sphere, and faded when frozen out at the chosen T/T<sub>D</sub>. The panel compares the heat capacity of the cube and the sphere, treated as continua: they agree exactly at low T and nearly at high T, with the largest difference, about 3%, near T ≈ 0.25 T<sub>D</sub>.

**The Debye heat capacity.** The derivation of the Debye temperature T<sub>D</sub> = (hc<sub>s</sub>/2k<sub>B</sub>)(6N/πV)<sup>1/3</sup> and of

```
U   = 9 N k_B T⁴/T_D³ ∫₀^(T_D/T) x³/(eˣ − 1) dx
C_V = 9 N k_B (T/T_D)³ ∫₀^(T_D/T) x⁴ eˣ/(eˣ − 1)² dx
```

with the high-temperature limit (equipartition) and the low-temperature T³ law, C<sub>V</sub> ≈ (12π⁴/5)(T/T<sub>D</sub>)³ Nk<sub>B</sub>. A chart compares Debye, Einstein (with ε matched at high temperature, ε/k<sub>B</sub> = √(3/5) T<sub>D</sub>), and the T³ law, on linear or logarithmic axes. Material presets from lead (88 K) to diamond (1860 K) give the molar heat capacity at any temperature. C<sub>V</sub> reaches 95% of its maximum at T = T<sub>D</sub>.

**Metals: electrons plus phonons.** C = γT + βT³, so C/T plotted against T² is a straight line whose intercept is the electronic γ and whose slope gives T<sub>D</sub>. Lines for gold, silver, and copper reproduce the lecture's figure, and the panel compares the measured γ with the free-electron estimate and gives the temperature below which electrons dominate (about 3.8 K for copper).

**Magnons in a ferromagnet (Problem 7.64).** An animated spin wave of precessing dipoles, whose precession speeds up with the square of 1/λ. For iron (m* = 1.24 × 10<sup>−29</sup> kg), the demo computes T<sub>0</sub> ≈ 4200 K and T<sub>1</sub> ≈ 2700 K, the loss of magnetization (T/T<sub>0</sub>)<sup>3/2</sup>, and a log-log comparison of the magnon and phonon heat capacities (T<sub>D</sub> = 470 K), which cross near 2 K. A final chart shows why there is no spontaneous magnetization in this model in two dimensions: as the system grows, the 3D magnon integral settles at 2.31516 while the 2D one grows without bound.

## A note on Problem 7.64(c)

At 300 K the lecture compares (C<sub>V</sub>/Nk<sub>B</sub>)<sub>magnon</sub> = 1/27 with (C<sub>V</sub>/Nk<sub>B</sub>)<sub>phonon</sub> ≈ 61 from the low-temperature formula. Since 300 K is 0.64 T<sub>D</sub> for iron, that formula is outside its range; the full Debye formula gives about 2.7. The conclusion is unchanged (phonons dominate by a factor of about 70), and the demo shows both values.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The Debye integral is evaluated numerically with Simpson's rule. The "real cube" heat capacity uses a precomputed distribution of distances within the cube, so it represents a macroscopic crystal rather than a small lattice.
- The 3D *n*-space view is a lightweight hand-written projection rather than a 3D library.
- The chain, *n*-space, and spin-wave animations pause when scrolled off screen and start paused when the system asks for reduced motion.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode: it follows `prefers-color-scheme`, and a sun/moon button in the top-right corner switches by hand (the choice is remembered across pages); and is responsive down to phone widths.
- Constants used: h = 6.626 × 10<sup>−34</sup> J s, k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K, R = 8.314 J/(mol K).

## Caveats

- Debye temperatures for lead (88 K), iron (470 K), and diamond (1860 K) come from the lecture; the others, and the values of γ for gold, silver, and copper, are typical handbook values. Different sources differ by a few percent.
- The chain animation uses Debye's linear relation between frequency and mode number; a real atomic chain's frequencies level off near the shortest wavelengths.
- The magnon results are low-temperature approximations, as in the problem.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Section 7.5 and Problem 7.64).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
