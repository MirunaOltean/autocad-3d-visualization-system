# Geometry Processing Algorithms

This document describes the core computational geometry algorithms used in the system to transform AutoCAD polyline data into structured representations for 2D and 3D visualization.

The system is designed as a multi-stage pipeline that separates geometry processing, mesh generation, and semantic visualization.

---

## 🔺 1. Polygon Triangulation (Ear Clipping)

### Overview

Ear Clipping is the primary algorithm used to decompose simple polygons into triangles for rendering and mesh generation.

It is a fundamental step in converting CAD polyline structures into renderable geometry.

---

### Algorithm principle

The algorithm works by iteratively removing "ears" from a polygon.

An "ear" is defined as a triangle formed by three consecutive vertices that satisfies:

- The triangle lies entirely inside the polygon
- No other polygon vertices are contained inside it
- The triangle does not intersect polygon edges

---

### Process

1. Identify a valid ear in the polygon
2. Remove the ear from the polygon
3. Store it as part of the triangulated mesh
4. Repeat until the polygon is fully decomposed

---

### Complexity

- Time complexity: **O(n²)**
- Suitable for architectural floorplans and moderate complexity shapes

---

### Usage in system

- Room decomposition
- Floorplan triangulation
- Mesh generation for Unity rendering

---

## 🔷 2. Delaunay Triangulation

### Overview

Delaunay triangulation is used in specific cases to improve mesh quality by maximizing minimum triangle angles.

This reduces skinny triangles and improves rendering stability.

---

### Properties

- Produces more uniform triangle distribution
- Improves visual quality of meshes
- Reduces geometric distortion during rendering

---

### Usage in system

- Mesh optimization stage
- Alternative triangulation method for specific datasets

---

## 📐 3. 2D → 3D Transformation

### Overview

This process converts 2D triangulated geometry into 3D structures by extruding or mapping coordinates into 3D space.

---

### Method

The transformation is based on:

- Maintaining vertex relationships from 2D polygons
- Mapping coordinates into 3D space
- Generating surfaces from triangulated data

---

### Output

- 3D wall surfaces
- Floor geometry
- Structural volumetric representation of CAD layouts

---

## 🏛️ 4. Architectural Semantic Layer (2D-Only Representation)

### Overview

A semantic architectural layer is applied on top of the reconstructed 2D geometry to identify structural elements such as:

- Walls
- Doors
- Windows
- Interior partitions
- Bathroom-related structures

---

### ⚠️ Important design constraint

This semantic layer is **only applied in the 2D visualization mode**.

It is explicitly NOT included in:

- 3D mesh generation
- Silhouette / projection views

---

### Reason for separation

This design choice ensures clear separation between:

- semantic interpretation (2D architectural understanding)
- geometric reconstruction (3D rendering)
- abstraction (silhouette views)

---

### Effect on system behavior

| View mode | Semantic layer | Geometry |
|-----------|---------------|----------|
| 2D View | Enabled | Present |
| 3D View | Disabled | Present |
| Silhouette View | Disabled | Simplified |

---

### Impact

This separation allows:

- clearer architectural interpretation in 2D
- optimized performance in 3D rendering
- simplified structural analysis in silhouette mode

---

## 🎯 Summary

The system combines:

- Computational geometry (triangulation algorithms)
- 3D reconstruction techniques
- Context-dependent semantic interpretation

This enables transformation of raw CAD data into multiple meaningful representations depending on visualization mode.
