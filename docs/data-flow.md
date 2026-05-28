# Data Flow Pipeline

This document describes the end-to-end data flow of the system, from raw AutoCAD input to final visualization outputs across different rendering modes.

The system is designed as a multi-stage processing pipeline where each stage transforms or enriches the data.

---

## 🧭 1. Input Stage (AutoCAD Data)

The process begins with CAD-generated polyline data representing architectural floorplans.

This includes:
- Lines
- Polylines
- Closed polygonal structures
- Room boundaries

These elements serve as the base geometric input for the system.

---

## ⚙️ 2. Backend Processing (ASP.NET Core MVC)

The backend is responsible for:

- Parsing CAD-derived data
- Organizing model metadata
- Preparing structured geometry for processing
- Managing model state and versioning

At this stage, the system still works with abstract geometric representations.

---

## 🔺 3. Geometry Processing Layer

This stage transforms raw polylines into structured mesh data.

Operations include:

- Polygon reconstruction
- Triangulation (Ear Clipping / Delaunay)
- Cleaning and validation of geometry
- Preparation for 3D transformation

Output: triangulated 2D mesh structures

---

## 🏗️ 4. 3D Reconstruction (Unity Pipeline)

The triangulated data is then transformed into 3D structures.

This includes:

- Vertex extrusion and mapping into 3D space
- Mesh generation
- Scene construction in Unity
- Preparation for WebGL export

Output: fully rendered 3D model

---

## 🏛️ 5. Semantic Architectural Layer (2D Only)

A semantic interpretation layer is applied **only in the 2D visualization mode**.

It identifies architectural components such as:
- Walls
- Doors
- Windows
- Interior partitions
- Bathroom elements

⚠️ Important:
This layer is NOT included in:
- 3D rendering
- silhouette views

It exists exclusively for enhanced 2D architectural understanding.

---

## 👤 6. Silhouette / Projection Mode

In this mode, the system generates a simplified structural representation.

Characteristics:
- Removes semantic elements
- Removes interior details
- Preserves only outer structural boundaries

This is used for abstraction and high-level shape analysis.

---

## 🖥️ 7. Presentation Layer (Frontend)

The final stage exposes the processed data to the user.

Features include:
- Model selection interface
- Visualization mode switching (2D / 3D / silhouette)
- Interaction controls
- Metadata display

Technologies:
- HTML
- CSS
- JavaScript

---

## 🔄 Complete Flow Summary

AutoCAD Input  
→ Backend Processing  
→ Geometry Reconstruction  
→ Triangulation Engine  
→ 3D Unity Rendering  
→ Optional Semantic Layer (2D only)  
→ Final Visualization Output

---

## 🎯 Key Design Principle

Each stage in the pipeline is independent and responsible for a single transformation:

- Geometry is separated from rendering
- Semantic interpretation is isolated to 2D
- 3D rendering remains clean and performance-focused
