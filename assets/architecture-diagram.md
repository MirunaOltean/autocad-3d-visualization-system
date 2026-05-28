# System Architecture Diagram

## Overview

This document describes the high-level architecture of the AutoCAD 2D/3D visualization system.

It provides a visual and conceptual breakdown of how data flows through the system from input to final rendering.

---

## 🧭 System Architecture (Conceptual)

The system is composed of multiple independent layers:

- Data ingestion layer (AutoCAD input)
- Backend processing layer (ASP.NET Core MVC)
- Geometry processing layer (triangulation & reconstruction)
- Rendering layer (Unity Viewer)
- Presentation layer (Web Frontend)

Each layer is responsible for a single transformation step in the pipeline.

---

## 🔄 End-to-End Flow

AutoCAD Data  
→ Backend (Parsing & Metadata)  
→ Geometry Processing (Polygon reconstruction)  
→ Triangulation Engine (Ear Clipping / Delaunay)  
→ Unity Rendering Pipeline (Mesh generation)  
→ Visualization Modes (2D / 3D / Silhouette)  
→ Web Frontend UI

---

## 🏗️ Visualization Modes

The system supports three distinct outputs:

### 🟦 2D Architectural View
- Includes semantic overlays (walls, doors, windows)
- Used for architectural interpretation

### 🔺 3D View
- Pure triangulated geometry
- No semantic overlays
- Focus on spatial reconstruction

### 👤 Silhouette View
- Simplified structural outline
- Removes internal and semantic details

---

## 🧠 Key Design Idea

A major design principle of the system is **layer separation**:

- Geometry is independent from rendering
- Semantic interpretation exists only in 2D
- 3D rendering remains clean and optimized

---

## 📌 Diagram 

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/d0806105-3dc0-42e7-9f2e-d4f70576ff3a" />

---

## 🎯 Role in System

This architecture ensures:

- scalability of the pipeline
- clear separation of concerns
- flexible rendering modes
- maintainable system design
