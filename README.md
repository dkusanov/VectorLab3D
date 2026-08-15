# VectorLab 3D

**VectorLab 3D** is an interactive, browser-based **3D vector algebra laboratory** built with HTML, CSS, vanilla JavaScript, and [Three.js](https://threejs.org/) (with `OrbitControls`). It lets you place points, draw free or bound vectors, and perform vector operations — addition, subtraction, cross product, normalization, magnitude, direction cosines — while watching the geometry update live in an orbitable 3D scene that uses a true **Z-up** (mathematics/engineering) coordinate convention. No server, install, or build step required.

Created by **Danilo S. Kusanovic**, Assistant Professor of Teaching, Civil and Environmental Engineering, University of California, Davis.

![VectorLab 3D demo](assets/vector-visualizer-demo.gif)

## Features

- Place **points** anywhere in 3D space, on a configurable construction plane (XY, XZ, or YZ, with an adjustable offset).
- Draw **vectors** — either *bound* (tail/head anchored to existing points) or *free* (defined by explicit tail/head coordinates).
- Perform vector **operations** on selected vectors: Normalize (v̂), Add (+v), Subtract (−v), Cross product (×), Direction Cosines (cos·), and Magnitude (‖v‖) — each creates a labeled result you can inspect or use as input to further operations.
- Live **Working Tree** of every point, vector, and operation, and a **Properties** panel for numeric editing.
- Orbit, pan, and zoom the 3D view (via `OrbitControls`); camera presets for Isometric, XY, XZ, and YZ views.
- Toggle grid, axes, labels, and auxiliary construction geometry independently.
- Dark and light themes; adjustable decimal precision.
- Save/Open models as JSON files; export the current view as a PNG image.

## Getting Started

VectorLab 3D is a single self-contained HTML file. It loads Font Awesome, Three.js, and the Three.js `OrbitControls` example script from public CDNs, so you need an internet connection the first time you open it (browsers will typically cache them afterward).

1. Download or clone this repository.
2. Open [`UCD_Vector_Visualizer-UI.html`](UCD_Vector_Visualizer-UI.html) directly in a modern desktop browser (Chrome, Edge, or Firefox recommended) — just double-click the file, or use **File → Open** in your browser.
3. No build tools, package managers, or servers are required.

> Tip: some browsers restrict certain features (like file downloads) for pages opened via `file://`. If you run into issues, you can instead serve the folder locally, e.g. `python3 -m http.server` from this directory and open `http://localhost:8000/UCD_Vector_Visualizer-UI.html`.

## Interface Overview

| Area | Description |
|---|---|
| **Menu bar** (top) | `File` (New/Open/Save/Export PNG), `Edit` (Select/Add Point/Draw Vector/Delete/Clear All), `View` (settings, grid/labels/axes/auxiliary-geometry toggles, zoom to fit, camera presets, theme). |
| **Toolbar** (below menu bar) | Quick-access icons for file operations, the Select/Point/Vector tools, the six vector-operation buttons (v̂, +v, −v, ×, cos·, ‖v‖), and zoom controls. |
| **Working Tree** (left panel) | A live list of every point, vector, and operation in the model, grouped by type. Click an entry to select it. |
| **3D Canvas** (center) | The orbitable 3D scene. Drag to orbit, scroll to zoom, right-drag (or two-finger drag) to pan. Shows the current construction plane at the bottom. |
| **Properties** (right panel) | Shows editable coordinates/components and computed results (magnitude, direction cosines/angles, etc.) for whatever is currently selected. |
| **Status bar** (bottom) | Live cursor coordinates and running counts of points/vectors/operations. |

## Quick Tutorial: Add Two Vectors and Inspect the Result

This is the workflow shown in the GIF above:

1. **Add points.** Click the **Point tool**, then click in the 3D view to place two or three points off the origin (the origin `O` always exists by default).
2. **Draw vectors.** Switch to the **Vector tool**, then click a start point and an end point to draw a *bound* vector from one to the other. Repeat to create a second vector (for example, both starting from the origin).
3. **Select both vectors.** Switch to the **Select tool** and select the two vectors you just created (in the Working Tree or by clicking them in the scene).
4. **Add them.** Click the **+v (Add)** operation button. A new result vector appears, equal to the vector sum, along with its construction (auxiliary) geometry.
5. **Inspect the result.** Select the result vector and read its components, magnitude, and direction cosines/angles in the Properties panel.
6. **Try another operation.** Select a single vector and click **v̂ (Normalize)**, **‖v‖ (Magnitude)**, or **cos(·) (Direction Cosines)** to see the corresponding textbook computation performed live; select two vectors and click **× (Cross)** to see the right-hand-rule perpendicular vector.
7. **Orbit the scene** to view the vectors from different angles, or use **View → Camera: Isometric/XY/XZ/YZ** for standard viewpoints.

## Coordinate Convention

VectorLab 3D uses a **Z-up** convention (x, y, z with z vertical), matching how vectors are typically taught in engineering and physics courses — this differs from the Y-up convention that Three.js and most game engines use by default. The source code comments explain how the app remaps axes internally so that what you see on screen matches the math you're doing on paper.

## Saving & Loading

- **Save** / **Save As...** downloads the current model (points, vectors, and operations) as a `.json` file.
- **Open...** lets you pick a previously saved `.json` file to restore a session.
- **Export View as PNG** downloads a snapshot of the current 3D view.

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Esc` | Return to the Select tool / close any open dialog |
| `Delete` / `Backspace` | Delete the currently selected point, vector, or operation (when not typing in a field) |

## For Students: How the Math Works

The commented source (`UCD_Vector_Visualizer-UI.html`) starts with a small, self-contained `VectorMath` module implementing the standard vector-algebra formulas — dot and cross products, magnitude, normalization, direction cosines/angles, and the angle between two vectors — completely independent of the 3D graphics. Reading that section first, before the Three.js scene-setup code, is a good way to connect the formulas from a linear-algebra or statics textbook to a working implementation, and to see exactly how each toolbar operation maps to a line of vector math.

## License / Attribution

This tool is provided for educational use by the UC Davis Civil and Environmental Engineering department. Third-party libraries used via CDN: [Font Awesome](https://fontawesome.com/), [Three.js](https://threejs.org/).
