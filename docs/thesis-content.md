# Thesis Context & System Evolution

## Overview

This document describes the original scope of the bachelor thesis project and the subsequent extensions made after its official completion.

It explains key design decisions, limitations encountered during implementation, and improvements introduced later in the development process.

---

## 🎓 Original Thesis Scope

The initial system focused on:

- Processing AutoCAD polyline data
- Reconstructing architectural floorplans
- Applying triangulation algorithms (Ear Clipping / Delaunay)
- Rendering 2D and 3D visualizations
- Implementing a Unity-based visualization pipeline

The goal was to transform raw CAD data into structured geometric representations suitable for visualization.

---

## 🧱 Core System Limitation (Thesis Phase)

During the thesis implementation, the system primarily focused on:

- Geometric correctness
- Mesh generation
- Basic visualization workflows

At this stage:

- Architectural elements were derived only implicitly
- Semantic interpretation was limited or partially integrated
- Visualization layers were tightly coupled to data format constraints

---

## 🏛️ Post-Thesis Extension: Semantic Architectural Layer

After the official thesis presentation, the system was further extended with a semantic architectural layer.

### Key enhancement:

The system was improved to detect and represent architectural components such as:

- Walls
- Doors
- Windows
- Bathroom structures
- Interior partitions

---

### ⚠️ Important design constraint

This semantic layer is applied **only in the 2D visualization mode**.

It is explicitly excluded from:
- 3D mesh rendering
- silhouette / projection views

This decision ensures a strict separation between:
- semantic interpretation (2D)
- geometric reconstruction (3D)
- abstraction (silhouette)

---

## 🔄 Why this extension matters

This post-thesis improvement introduces:

- A higher level of architectural understanding
- A clearer separation of visualization responsibilities
- A more realistic representation of CAD-derived models in 2D

It effectively transitions the system from a purely geometric tool into a **semi-semantic architectural visualization system**.

---

## ⚙️ Design Evolution Summary

| Phase | Focus | Output |
|------|------|--------|
| Thesis | Geometry + triangulation | 2D/3D mesh rendering |
| Post-thesis | Semantic enrichment | Architectural 2D overlay system |

---

## 🎯 Final System View

The system now operates across three conceptual layers:

1. **Geometry Layer**
   - triangulation
   - mesh generation

2. **Semantic Layer (2D only)**
   - architectural element detection

3. **Visualization Layer**
   - 2D (semantic + geometry)
   - 3D (geometry only)
   - silhouette (abstracted geometry)

---

## 🧠 Key Insight

The evolution of the system reflects a shift from:

> computational geometry pipeline

to

> multi-layer architectural visualization system with semantic interpretation
