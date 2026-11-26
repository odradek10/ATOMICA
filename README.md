# ATOMICA — 3D Crystallography & Solid-State Structure Visualizer

**Live app:** https://odradek10.github.io/ATOMICA/

Atomica is an interactive, browser-based 3D visualizer for crystal structures. You can rotate and zoom structures, build supercells, draw Miller planes and directions, explore interstitial voids, see reciprocal space and powder XRD patterns, play with crystal defects, and work with stereographic projections and Wulff nets.

> **You need an internet connection to use Atomica.** The 3D engine (Three.js), styling (Tailwind CSS) and fonts are loaded from online CDNs. Without a connection the app will not load properly, even if you download the file and open it locally.

---

## Why I built this

I'm a Materials and Metallurgical Engineering student. This semester our curriculum included a crystallography course, and I found it very hard to *visualize* the structures from 2D textbook drawings: where the atoms sit, how planes cut through a cell, where the voids are, why some X-ray reflections disappear.

After I worked through the course and finally understood it, I decided to build the tool I wished I'd had, so that other students can see these ideas in 3D and explore them by themselves instead of struggling the way I did.

## About the scope: 15 structures, on purpose

Atomica contains **exactly 15 crystal structures**, because those are the structures covered in my course curriculum. I only know these well enough to check them, and I did not want to add structures I couldn't verify. So I deliberately added nothing beyond them.

If you spot anything that doesn't match your textbook, please tell me (see "Feedback" below). Note that some structures can be drawn in different but equivalent settings (for example, a different choice of origin), so a textbook figure may look shifted compared to the one here.

---

## Quick tour: what each tab is for

| Tab | Use it to understand... |
|---|---|
| **Crystals** | where atoms sit in the 15 structures, how they are coordinated, and what planes cut through them |
| **Miller Indices** | how (hkl) planes and [uvw] directions are drawn in a unit cell |
| **Voids** | why small atoms fit into some holes (octahedral, tetrahedral) of BCC and FCC but not others |
| **Reciprocal** | how real-space planes become reciprocal-lattice points, Bragg's law, and XRD peaks |
| **Defects** | how vacancies, interstitials, dopants and dislocations distort a lattice, and how temperature controls vacancy concentration |
| **Stereographic** | how 3D plane normals are flattened onto a 2D stereogram, and how to measure angles and zone axes |
| **My Crystal** | how "space lattice + basis = crystal structure" by building your own |

---

## Features and how to explore each section

### 1. Crystals

**What it has**

- **15 structures:** BCC (α-Fe), FCC (Cu), HCP (Mg), Rock Salt (NaCl), Cesium Chloride (CsCl), Diamond Cubic, Zinc Blende, Wurtzite, CuO (Tenorite), Cu₂O (Cuprite), Rutile (TiO₂), Fluorite (CaF₂), Antifluorite (Li₂O), Ideal Cubic Perovskite (SrTiO₃) and Spinel (MgAl₂O₄).
- **Supercell expansion:** view 1, 2, 4 or 8 unit cells.
- **Spinel octant decomposition:** because the spinel cell is large (56 atoms), you can view 1/8, 1/4, 1/2 or a full unit cell, split into **Type A** and **Type B** octants. Switch between two origin conventions (FCC-O²⁻ octants, or Origin Choice 1 with Al₄O₄ heterocubane clusters), and toggle the internal octant dividers and Type A / Type B labels.
- **Visualization modes:** Ball & Stick, Space-Filling, Polyhedral, and Polyhedra + Ball & Stick, with adjustable polyhedra opacity.
- **Coordination polyhedra:** octahedra, tetrahedra, cubes, cuboctahedra and square-planar units, drawn for each structure.
- **Material properties:** atomic packing factor (APF), coordination number, crystal system, space group and lattice parameters.
- **Species visibility:** show or hide each element.
- **Click to remove parts:** click any atom, bond or polyhedron to hide it, then restore parts one by one or all at once (with an optional "rejoin" animation).
- **Hover tooltips:** hover over an atom to see its element and fractional coordinates.
- **Neighbor Explorer:** pick an atom and see its 1st, 2nd and 3rd nearest-neighbor shells, with counts and distances in Å.
- **Sectioning tool:** cut the crystal with any (hkl) plane at an adjustable offset and see a 2D slice of the atoms lying on that plane.
- **Color convention for compounds:** light green for cations, deep blue for anions, light yellow for a second cation (ternary compounds such as perovskite). In spinel, Mg²⁺ is yellow and Al³⁺ is green.

**How to explore it**

1. Pick a structure from the dropdown and drag to rotate. Use the camera buttons ([100], [110], [111], Isometric) to look along important directions.
2. Switch the visualization mode to *Polyhedral* to see how the structure is built from coordination polyhedra (for example, corner-sharing TiO₆ octahedra in perovskite).
3. Increase the supercell to see the repeating pattern, then hide atoms to look inside.
4. Turn on **Neighbor Explorer** and click different atoms to compare 1NN, 2NN and 3NN shells.
5. Turn on the **Sectioning Tool**, try (111) in FCC, and slide the offset to see stacking layers.
6. For spinel, start with 1/8 cell (Type A), then step up to 1/4, 1/2 and the full cell to see how Type A and Type B octants combine.

### 2. Miller Indices

**What it has**

- A clean reference unit cell with the origin and X, Y, Z axes.
- **Direction vectors [uvw]** and **lattice planes (hkl)**, including negative indices (the origin shifts automatically so the plane or vector stays inside the cell).
- Axial intercepts shown for each plane, plus one-click presets for common planes and directions.

**How to explore it**

1. Start with (100), (110) and (111) and watch the intercepts change.
2. Type a plane like (2 1 0) and check the intercepts against what you calculate by hand (take reciprocals, clear fractions).
3. Try negative indices such as (-1 1 1) to see how the origin shifts.
4. Compare a plane and a direction with the same indices, for example (111) and [111]. In cubic crystals, the direction is perpendicular to the plane.

### 3. Voids

**What it has**

- **BCC and FCC host lattices** with octahedral and tetrahedral interstitial voids.
- Filters for edge-centered, face-centered and interior voids.
- **Guest atom radius (r/R)** slider with an "auto-fit to critical ratio" mode, and badges telling you whether a guest fits ideally, rattles loose, or distorts the lattice.
- Shows the difference between FCC (regular voids) and BCC (distorted voids), and the effective number of voids per unit cell.
- **2D coordinates panel:** project the void positions onto XY, XZ or YZ planes at different slices, with coordinate labels. Hover a dot to highlight the void in 3D.
- Click voids in 3D to hide them or inspect them.

**How to explore it**

1. Start with FCC and "Auto-Fit". Every void is a perfect fit at its critical ratio (0.414 octahedral, 0.225 tetrahedral).
2. Switch to BCC and notice that the voids are *distorted* and the critical ratios are much smaller (0.155 and 0.291).
3. Turn off auto-fit and drag the guest radius slider to see when a guest atom rattles, fits or pushes the lattice apart.
4. Open the **2D Grid**, choose a plane and slice, and match the dot positions to the 3D void positions.
5. Check the "Effective / Cell" counter against the known numbers (FCC: 4 octahedral and 8 tetrahedral voids per cell).

### 4. Reciprocal Space, Bragg's Law & XRD

**What it has**

- **3D reciprocal lattice** with the reciprocal basis vectors (a*, b*, c*), allowed and forbidden reflections, and a selectable (hkl) node.
- **Live readout:** d-spacing, |g| = 1/d, |G| = 2π/d, 2θ and the structure factor for the selected reflection.
- **Bragg's Law simulator:** an animated 2D diagram of nλ = 2d·sinθ with adjustable wavelength (Cu, Mo and Co Kα₁ presets), d-spacing and diffraction order, and a warning when diffraction is impossible.
- **Theoretical powder XRD pattern:** calculated from the structure factor, multiplicity and Lorentz-polarization factor, with adjustable peak width, forbidden reflections marked, a peak table, and click-a-peak to sync (hkl).

**How to explore it**

1. In **3D Lattice**, pick FCC and look at which nodes are allowed. Only all-odd or all-even (hkl) survive.
2. Click a node, then switch to **Bragg's Law**. The d-spacing carries over automatically. Change λ or n and watch the angle change.
3. Push λ up or d down until the red "No diffraction possible" warning appears. This shows why nλ ≤ 2d.
4. Open **XRD Pattern**, choose a structure, and click peaks to see which (hkl) they belong to.
5. Compare the XRD patterns of BCC, FCC and a simple cubic structure and note which peaks are missing (forbidden ticks in red).

### 5. Defects

**What it has**

- **Point defects (0D)** in FCC, BCC, simple cubic and ionic NaCl lattices: vacancy, self-interstitial, substitutional (larger or smaller dopant), Frenkel pair and Schottky pair.
- **Unit cell size:** work in 1, 2 (2×1×1) or 4 (2×2×1) cells.
- **Defect concentration:** temperature (300–2500 K) and activation energy Q (0.10–1.80 eV) sliders that compute the equilibrium fraction n/N = e<sup>−Q/kT</sup>, with presets (Demo, Al, Cu). With "Auto-Sync" on, the 3D cell shows that many vacancies.
- **Strain visualization:** neighboring atoms shift and highlight around each defect.
- **Vacancy diffusion:** an animated atom hop with a live activation-energy diagram (the barrier height follows Q, and a kT line shows thermal energy) and jump frequency Γ = ν₀e<sup>−Q/kT</sup>. Use **Simulate Diffusion Hop** for one jump or **Auto-Hop** for continuous hopping at a rate tied to T and Q.
- **Dislocations (1D):** edge and screw dislocations with the dislocation line, Burgers vector, Burgers circuit, slip plane and compressive/tensile strain coloring. (These are schematic illustrations for building intuition.)

**How to explore it**

1. Click an atom with the **Vacancy** tool, then click the red wireframe again to heal it. Notice the neighbors shifting toward the hole.
2. Try each tool in turn: self-interstitial (click an octahedral or tetrahedral marker), substitutional (larger vs smaller dopant), Frenkel (vacancy + interstitial pair) and Schottky (switches to NaCl automatically).
3. Move the **Temperature** slider up with the Cu preset and watch n/N grow exponentially. Then raise Q and see the concentration collapse.
4. Add a vacancy, press **Simulate Diffusion Hop**, and watch the dot ride over the barrier in the Eₐ diagram. Then turn on **Auto-Hop** and compare fast (high T, low Q) vs slow (low T, high Q) hopping.
5. Switch to **Dislocations (1D)** and compare edge (b ⊥ t) with screw (b ∥ t). Toggle the Burgers circuit and strain coloring.

### 6. Stereographic Projection

**What it has**

- **Three viewing modes:** a 3D reference sphere, a 2D stereogram with Wulff net, or both side by side (Dual View).
- **3D reference sphere:** shows the equatorial plane, N/S poles, a unit cube with its crystal axes, the plane through the sphere centre and its great circle, the normal ray to the pole P, and the projection line from P to the opposite pole that pierces the equator at P′.
- **Projection center presets:** [001], [110] and [111].
- **Pole input:** add a plane (hkl) with its great-circle trace, add a direction [uvw], or plot all symmetry equivalents ({hkl} or ⟨uvw⟩). A standard {100} + {110} + {111} preset loads in one click.
- **Upper and lower hemisphere:** upper poles are drawn as filled dots (●), lower poles as open circles (○).
- **Angle & Zone Axis tool:** click any two poles (or type P₁ and P₂) to get the interplanar angle θ, the zone axis [UVW] from P₁ × P₂, and the zone circle.
- **Wulff net overlay:** 10° or 15° grid, adjustable rotation φ, and an "Align to P₁–P₂" button that rotates the net so the two poles lie on the same great circle.
- Plotted-poles list where you can focus a pole (draws its 3D ray), toggle its great-circle trace, or delete it.

**How to explore it**

1. Open **Dual View**, load the standard preset, and compare the 3D sphere with the flat 2D stereogram. The 3D projection line shows how each point is projected.
2. Click two poles, for example (111) and (101). Read θ and the zone axis, and check them by hand with the dot product and cross product.
3. Turn on the zone circle and see that both poles lie on it.
4. Click **Align Wulff Net to P₁–P₂** to rotate the net and measure the angle along the net's graduated great circle.
5. Change the projection center from [001] to [110] or [111] and see how the whole pattern rotates (the familiar [111] three-fold symmetry appears).

### 7. My Crystal (build your own)

**What it has**

- Design a crystal as **space lattice + basis**: choose one of the 7 crystal systems and a valid Bravais centering (P, I, F or C), and set the cell lengths and angles (constrained to what the chosen system allows).
- Add basis atoms from a periodic-table element list, with fractional coordinates (decimals or fractions like 1/2).
- Toggle between lattice points only and the full crystal, choose a supercell, and auto-generate bonds.
- Presets: CsCl, NaCl, diamond Si and BaTiO₃.
- Save structures in your browser, and export or import them as JSON files.

**How to explore it**

1. Load the **CsCl** preset and switch between *Lattice Points Only* and *Full Crystal* to see the idea of lattice + basis.
2. Load **NaCl** (F-centering + 2-atom basis) and compare it with the built-in NaCl on the Crystals tab.
3. Change the crystal system and watch which cell parameters lock automatically (for example, all lengths equal in cubic).
4. Add or move basis atoms and watch how bonds and the crystal change. Invalid fractions turn red.
5. Save your structure, or export it as JSON to share with a friend.

### Everywhere

- Camera presets along [100], [110], [111] and an isometric view.
- Mouse controls: drag to orbit, Shift or right-drag to pan, scroll to zoom (pinch on touch screens).
- **Export PNG** with a transparent or white background (2D plots export as-is, and Stereographic Dual View exports both panels side by side).
- Collapsible controls sidebar.
- A built-in **Report Bugs or Suggestions** button.

---

## How the code is organized

Atomica is a single `index.html` file with no build step. Inside the script, the code is organized in clear layers:

1. **Crystallographic database:** the 15 structures are plain data objects (cell parameters, atomic basis in fractional coordinates, bond rules and coordination-polyhedra rules). Adding or checking a structure means editing data, not logic.
2. **Geometry engine:** converts lattice parameters (a, b, c, α, β, γ) into lattice vectors, expands the basis into supercells, finds bonds by distance rules, and finds coordination polyhedra by collecting ligands around each cation. Special-case builders handle the hexagonal prism (HCP, wurtzite) and the spinel octants.
3. **Math modules:** Miller plane and direction geometry, reciprocal-lattice vectors, structure factors (Cromer-Mann atomic form factors), powder XRD with multiplicity and Lorentz-polarization, stereographic projection and great-circle math, and the defect thermodynamics (Boltzmann factors).
4. **Application state:** one central `state` object holds every setting for all seven tabs.
5. **Scene builders:** a separate function per tab builds the Three.js scene (`rebuild3DScene`), and 2D canvases draw the Bragg diagram, XRD plot and Wulff net.
6. **UI renderers:** each tab has a sidebar renderer that rebuilds the controls from the current state and wires up the events. `updateAll()` refreshes everything after any change.
7. **Interaction layer:** a custom orbit controller (drag, pan, pinch, zoom, camera snap), raycasting for hover tooltips and clicks, and PNG export.

This layout makes the code easy to read tab by tab: find the tab's state, then its scene builder, then its sidebar.

---

## Built with

- [Three.js](https://threejs.org/) (r128) for 3D rendering
- [Tailwind CSS](https://tailwindcss.com/) (CDN) for styling
- Plain HTML, CSS, JavaScript and the Canvas 2D API in a single file, with no build step

## Run it locally

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Stay connected to the internet (the libraries load from CDNs).

## Feedback

Found a bug, or something that doesn't match your textbook? Please [open an issue](https://github.com/odradek10/ATOMICA/issues) on this repository, or use the **Report Bugs or Suggestions** button inside the app. Suggestions are very welcome.

## Limitations

- Only the 15 structures from my course curriculum are included.
- Values such as APF and structure positions are for learning and visualization. Please check them against your textbook for exams or research.
- XRD patterns are theoretical powder patterns (no temperature or instrument effects), and they use neutral-atom form factors even for ionic compounds.
- The Defects tab is a teaching model. The vacancy concentration and the jump frequency both use a single activation energy Q, whereas real materials have separate formation and migration energies. The dislocation views are schematic.
- The stereographic tools (symmetry-equivalent poles and the angle formula) assume **cubic** crystal geometry.
- Needs an internet connection (see above).
