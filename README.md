# AutoCAD 2D/3D Visualization System

A full-stack software system that transforms AutoCAD polyline data into interactive 2D and 3D visualizations using geometry processing, triangulation algorithms, and real-time rendering with Unity and a web-based viewer.

---

## 📌 Overview

This project was developed as part of a bachelor’s thesis and focuses on bridging the gap between raw AutoCAD geometric data and interactive visualization systems.

The system enables:
- Extraction and processing of polyline data from CAD models
- Conversion of 2D geometric structures into triangulated meshes
- Generation of 3D representations from 2D architectural data
- Interactive visualization in both web and Unity environments

The goal is to support use cases in architecture, engineering, and spatial analysis by providing a modern visualization pipeline.

---

## 🧠 Key Features

- Import and processing of AutoCAD polyline-based data
- Polygon triangulation using computational geometry algorithms
- 2D to 3D transformation pipeline for spatial reconstruction
- Real-time rendering of models in Unity (WebGL)
- Web-based interface for model interaction and metadata handling
- Layer/floor switching and model state management
- Semantic architectural reconstruction (walls, doors, windows, interior elements)
- Optimized memory handling for large-scale models

---

## 🏗️ System Architecture

The system is composed of two main components:

### 🔹 1. 3DViewer (Web Application)
Backend + frontend system responsible for data handling and user interaction.

**Backend:**
- ASP.NET Core MVC
- C#
- Handles model metadata, structure, and state management

**Frontend:**
- HTML
- CSS
- JavaScript
- Provides interactive UI for model browsing and control

---

### 🔹 2. UnityViewer (Rendering Engine)
A Unity-based rendering module responsible for visualizing processed geometry.

- Built using Unity Engine
- Written in C#
- Exported as WebGL module
- Handles real-time rendering of 2D/3D geometry
- Responsible for mesh visualization and scene management

---

## 📐 Core Algorithms

### 🔸 Polygon Triangulation (Ear Clipping)
The system uses the Ear Clipping algorithm to decompose complex polygons into triangles.

- Time complexity: **O(n²)**
- Used for:
  - Polygon decomposition
  - Mesh generation
  - 3D surface construction

---

### 🔸 Delaunay Triangulation
Used for improving mesh quality and stability in certain reconstruction scenarios.

- Produces more uniform triangles
- Improves rendering stability

---

### 🔸 2D → 3D Transformation
Transforms flat CAD geometry into 3D structures by:

- Mapping planar coordinates into 3D space
- Generating surfaces from triangulated meshes
- Preserving spatial relationships from original CAD data

---

### 🔸 Silhouette Extraction
Converts 3D models back into 2D projections for visualization and analysis purposes.

---

## 🏛️ Architectural Semantic Layer (Post-Thesis Extension)

After the completion and official defense of the bachelor thesis, the project was further extended with an additional semantic reconstruction layer on top of the existing geometric pipeline.

While the original system focused on converting AutoCAD polyline data into triangulated 2D and 3D representations, the extended version introduces a higher-level interpretation of architectural elements.

### 🔹 What was added

A semantic architectural mapping layer that identifies and overlays building components such as:

- Walls
- Doors
- Windows
- Bathroom fixtures (e.g., stalls, partitions)
- Structural boundaries and interior separations

These elements are constructed on top of the previously generated room and polyline-based geometry.

---

### 🔹 How it works conceptually

Instead of treating the CAD input purely as geometric data, the system now interprets structural relationships between elements and assigns semantic meaning based on spatial configuration and layout rules.

This allows the visualization system to move from:

> raw geometric representation

to:

> semantically enriched architectural model

---

### 🔹 Resulting improvement

This extension significantly improves the realism and usability of the visualization by enabling:

- Clear identification of functional spaces (rooms vs structural elements)
- More accurate architectural representation of CAD drawings
- Enhanced interpretability for architectural and engineering use cases
- A foundation for future BIM-like extensions (Building Information Modeling concepts)

---

### 🔹 Impact on the system

This addition transforms the project from a purely geometric visualization tool into a semi-structured architectural reconstruction system capable of representing both:

- geometric correctness (triangulated meshes)
- semantic meaning (building components)

---

## 🧩 Data Flow

1. AutoCAD polyline input
2. Parsing and preprocessing
3. Polygon reconstruction
4. Triangulation (mesh generation)
5. 2D rendering + semantic architectural overlay
6. 3D rendering (Unity viewer)
7. User interaction (layer switching, visibility control)

---

## 🛠️ Tech Stack

### Backend
- C#
- ASP.NET Core MVC
- .NET Framework

### Frontend
- HTML5
- CSS3
- JavaScript

### Rendering
- Unity Engine
- WebGL

### Geometry Processing
- Custom triangulation algorithms
- Computational geometry methods

---

## 📷 Screenshots

- AutoCAD input model
  
  <img width="416" height="635" alt="image" src="https://github.com/user-attachments/assets/7c111138-b31e-466f-a14c-4b9c135c37b3" />

- 2D web visualization

  <img width="599" height="401" alt="image" src="https://github.com/user-attachments/assets/2a5b821e-b85b-4e38-81af-eb9ebb4b556e" />

- 3D Unity rendering

  <img width="788" height="481" alt="image" src="https://github.com/user-attachments/assets/068de093-5b87-4585-b57f-85b74428b895" />
  
- Silhouette Extraction

  <img width="827" height="522" alt="image" src="https://github.com/user-attachments/assets/c1d4513d-f6ed-4997-b595-a88f4d81638e" />

- Architectural semantic visualization

  <img width="601" height="386" alt="Screenshot 2026-05-28 141947" src="https://github.com/user-attachments/assets/310235d3-2b77-40a6-9bee-4b6621f9e3e0" />

---

## 📚 Use Cases

- Architectural visualization
- Urban planning analysis
- Engineering design review
- CAD data interpretation systems
- Educational geometry visualization

---

## 🎓 Project Context

This project was developed as a bachelor’s thesis in Applied Computer Science and was carried out in collaboration with an industry environment.

It combines:
- theoretical computational geometry
- practical software engineering
- real-world CAD data processing

---

## 🚀 Future Improvements

- Support for additional CAD formats (e.g., Revit, IFC)
- Improved triangulation performance
- GPU-accelerated mesh generation
- Enhanced real-time collaboration features
- Cloud-based model storage and streaming

---

## 👩‍💻 Author

**Miruna Oltean**  
Bachelor’s Thesis – Applied Computer Science  
Brașov, Romania

---

## 📄 License

This project is part of an academic thesis and is shared for portfolio purposes.
