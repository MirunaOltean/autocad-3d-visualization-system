# System Architecture

## Overview

The system is composed of multiple interconnected modules responsible for processing, transforming, and visualizing AutoCAD-based geometric data.

The architecture follows a layered design that separates:

- Data ingestion
- Geometry processing
- Rendering
- User interaction

---

## Main Components

### 1. Data Processing Layer (Backend - ASP.NET Core MVC)

Responsible for:
- Loading CAD-derived data
- Managing model metadata
- Handling structure and state of architectural models

Technologies:
- C#
- ASP.NET Core MVC

---

### 2. Geometry Processing Layer

Responsible for transforming raw polyline data into usable mesh structures.

Key operations:
- Polygon reconstruction
- Triangulation (Ear Clipping / Delaunay)
- 2D → 3D transformation

---

### 3. Rendering Layer (Unity Viewer)

Responsible for:
- Real-time visualization of 2D/3D geometry
- Mesh rendering
- Scene management
- WebGL export for browser usage

---

### 4. Presentation Layer (Frontend)

Responsible for:
- User interaction
- Model selection
- UI controls for visibility and layers
- Communication with backend services

Technologies:
- HTML
- CSS
- JavaScript

---

## Architecture Flow

AutoCAD Data  
→ Backend Processing (ASP.NET Core)  
→ Geometry Reconstruction  
→ Triangulation Engine  
→ Unity Rendering Pipeline  
→ Web UI Interaction  

---

## Key Design Principle

The system is designed with separation of concerns:
- Geometry logic is independent from rendering
- Backend manages structure, not visualization
- Unity handles rendering only
