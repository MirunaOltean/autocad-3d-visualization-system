# Unity Rendering Pipeline

## Overview

The UnityViewer module is responsible for transforming processed geometric data into real-time visualizations.

It acts as the final rendering layer of the system and supports multiple visualization modes including 2D projection, full 3D rendering, and simplified silhouette views.

The module is built using Unity Engine and exported as a WebGL application for browser-based interaction.

---

## 🎮 Rendering Architecture

The rendering system is structured as a pipeline that receives pre-processed mesh data and converts it into Unity-compatible objects.

### Input Data Types
- Triangulated 2D geometry
- Extruded 3D mesh structures
- Metadata describing model state

---

## 🔺 1. Mesh Construction

Incoming triangulated data is converted into Unity Mesh objects.

This process includes:
- Vertex buffer creation
- Triangle index mapping
- Normal generation
- Mesh optimization for rendering

The result is a GPU-ready mesh structure.

---

## 🏗️ 2. Scene Assembly

Once meshes are generated, they are assembled into a Unity scene.

This includes:
- Positioning objects in world space
- Grouping geometry into logical structures (rooms, floors)
- Applying transformations based on model hierarchy

---

## 🧭 3. Visualization Modes

The renderer supports three distinct modes:

---

### 🟦 2D Architectural View

- Displays semantic architectural overlays
- Includes:
  - walls
  - doors
  - windows
  - interior elements
- Provides annotated structural understanding

⚠️ This mode is the ONLY one where semantic elements are rendered.

---

### 🔺 3D View

- Displays pure triangulated geometry
- No semantic overlays are included
- Focuses on structural accuracy and spatial representation

---

### 👤 Silhouette View

- Simplified projection of the model
- Removes internal geometry and semantic details
- Shows only outer structural boundaries

---

## 🌐 4. WebGL Export

The Unity application is exported as a WebGL build to enable browser execution.

This allows:
- Cross-platform accessibility
- No installation requirement
- Direct integration with web frontend

---

## ⚙️ Performance Considerations

To ensure smooth rendering:

- Meshes are optimized before runtime
- Unnecessary geometry is removed in non-2D modes
- Scene objects are grouped for efficient draw calls
- Memory usage is controlled for large models

---

## 🔄 Rendering Flow Summary

Processed Data → Mesh Generation → Scene Construction → Visualization Mode Selection → Real-time Rendering (WebGL)

---

## 🎯 Key Design Principle

The UnityViewer is strictly a rendering engine.

It does NOT:
- process CAD data
- perform triangulation
- handle semantic classification

Its only responsibility is:

> efficient and accurate visualization of preprocessed geometry
