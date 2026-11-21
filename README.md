# Atomica — 3D Crystallography & Solid-State Structure Visualizer

**Live app:** https://odradek10.github.io/ATOMICA/

Atomica is an interactive, browser-based 3D visualizer for crystal structures. You can rotate and zoom structures, build supercells, draw Miller planes and directions, explore interstitial voids, see reciprocal space and powder XRD patterns, and play with crystal defects.

> **You need an internet connection to use Atomica.** The 3D engine (Three.js), styling (Tailwind CSS) and fonts are loaded from online CDNs. Without a connection the app will not load properly, even if you download the file and open it locally.

---

## Why I built this

I'm a Materials and Metallurgical Engineering student. This semester our curriculum included a crystallography course, and I found it very hard to *visualize* the structures from 2D textbook drawings: where the atoms sit, how planes cut through a cell, where the voids are, why some X-ray reflections disappear.

After I worked through the course and finally understood it, I decided to build the tool I wished I'd had, so that other students can see these ideas in 3D and explore them by themselves instead of struggling the way I did.

## About the scope: 15 structures, on purpose

Atomica contains **exactly 15 crystal structures**, because those are the structures covered in my course curriculum. I only know these well enough to check them, and I did not want to add structures I couldn't verify. So I deliberately added nothing beyond them.

If you spot anything that doesn't match your textbook, please tell me (see "Feedback" below). Note that some structures can be drawn in different but equivalent settings (for example, a different choice of origin), so a textbook figure may look shifted compared to the one here.
---

## Features

### 1. Crystals

- **15 structures:** BCC (α-Fe), FCC (Cu), HCP (Mg), Rock Salt (NaCl), Cesium Chloride (CsCl), Diamond Cubic, Zinc Blende, Wurtzite, CuO (Tenorite), Cu₂O (Cuprite), Rutile (TiO₂), Fluorite (CaF₂), Antifluorite (Li₂O), Ideal Cubic Perovskite (SrTiO₃) and Spinel (MgAl₂O₄).
- **Supercell expansion:** view 1, 2, 4 or 8 unit cells. For spinel (a large cell), view 1/8, 1/4, 1/2 or a full unit cell so you can inspect the details.
- **Visualization modes:** Ball & Stick, Space-Filling, Polyhedral, and Polyhedra + Ball & Stick, with adjustable polyhedra opacity.
- **Coordination polyhedra:** octahedra, tetrahedra, cubes, cuboctahedra and square-planar units, drawn for each structure.
- **Material properties:** atomic packing factor (APF), coordination number, crystal system, space group and lattice parameters.
- **Species visibility:** show or hide each element.
- **Click to remove parts:** click any atom, bond or polyhedron to hide it, then restore parts one by one or all at once (with an optional "rejoin" animation).
- **Hover tooltips:** hover over an atom to see its element and fractional coordinates.
- **Neighbor Explorer:** pick an atom and see its 1st, 2nd and 3rd nearest-neighbor shells, with counts and distances in Å.
- **Sectioning tool:** cut the crystal with any (hkl) plane at an adjustable offset and see a 2D slice of the atoms lying on that plane.
- **Color convention for compounds:** light green for cations, deep blue for anions, light yellow for a second cation (ternary compounds such as perovskite and spinel).

### 2. Miller Indices

- A clean reference unit cell with the origin and X, Y, Z axes.
- **Direction vectors [uvw]** and **lattice planes (hkl)**, including negative indices (the origin shifts automatically so the plane or vector stays inside the cell).
- Axial intercepts shown for each plane, plus one-click presets for common planes and directions.

### 3. Voids

- **BCC and FCC host lattices** with octahedral and tetrahedral interstitial voids.
- Filters for edge-centered, face-centered and interior voids.
- **Guest atom radius (r/R)** slider with an "auto-fit to critical ratio" mode, and badges telling you whether a guest fits ideally, rattles loose, or distorts the lattice.
- Shows the difference between FCC (regular voids) and BCC (distorted voids), and the effective number of voids per unit cell.
- **2D coordinates panel:** project the void positions onto XY, XZ or YZ planes at different slices, with coordinate labels. Hover a dot to highlight the void in 3D.
- Click voids in 3D to hide them or inspect them.

### 4. Reciprocal Space, Bragg's Law & XRD

- **3D reciprocal lattice** with the reciprocal basis vectors (a*, b*, c*), allowed and forbidden reflections, and a selectable (hkl) node.
- **Live readout:** d-spacing, |g| = 1/d, |G| = 2π/d, 2θ and the structure factor for the selected reflection.
- **Bragg's Law simulator:** an animated 2D diagram of nλ = 2d·sinθ with adjustable wavelength (Cu, Mo and Co Kα₁ presets), d-spacing and diffraction order, and a warning when diffraction is impossible.
- **Theoretical powder XRD pattern:** calculated from the structure factor, multiplicity and Lorentz-polarization factor, with adjustable peak width, forbidden reflections marked, a peak table, and click-a-peak to sync (hkl).

### 5. Defects

- **Point defects (0D)** in FCC, BCC, simple cubic and ionic NaCl lattices: vacancy, self-interstitial, substitutional (larger or smaller dopant), Frenkel pair and Schottky pair.
- **Strain visualization:** neighboring atoms shift and highlight around each defect.
- **Vacancy diffusion:** an animated atom hop with an activation-energy (Eₐ) diagram.
- **Dislocations (1D):** edge and screw dislocations with the dislocation line, Burgers vector, Burgers circuit, slip plane and compressive/tensile strain coloring. (These are schematic illustrations for building intuition.)

### 6. My Crystal (build your own)

- Design a crystal as **space lattice + basis**: choose one of the 7 crystal systems and a valid Bravais centering (P, I, F or C), and set the cell lengths and angles (constrained to what the chosen system allows).
- Add basis atoms from a periodic-table element list, with fractional coordinates (decimals or fractions like 1/2).
- Toggle between lattice points only and the full crystal, choose a supercell, and auto-generate bonds.
- Presets: CsCl, NaCl, diamond Si and BaTiO₃.
- Save structures in your browser, and export or import them as JSON files.

### Everywhere

- Camera presets along [100], [110], [111] and an isometric view.
- Mouse controls: drag to orbit, Shift or right-drag to pan, scroll to zoom (pinch on touch screens).
- **Export PNG** with a transparent or white background (2D plots export as-is).
- Collapsible controls sidebar.

---

## Built with

- [Three.js](https://threejs.org/) (r128) for 3D rendering
- [Tailwind CSS](https://tailwindcss.com/) (CDN) for styling
- Plain HTML, CSS and JavaScript in a single file, with no build step

## Run it locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Stay connected to the internet (the libraries load from CDNs).

## Feedback

Found a bug, or something that doesn't match your textbook? Please [open an issue](https://github.com/odradek10/ATOMICA/issues) on this repository, or use the **Report Bugs or Suggestions** button inside the app. Suggestions are very welcome.

## Limitations

- Only the 15 structures from my course curriculum are included.
- Values such as APF and structure positions are for learning and visualization. Please check them against your textbook for exams or research.
- XRD patterns are theoretical powder patterns (no temperature or instrument effects).
- Needs an internet connection (see above).
