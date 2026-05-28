# Geometry Processing Pipeline (Backend)

## Overview

This document describes how raw input data (JSON-based architectural models derived from AutoCAD) is processed into structured geometric representations used by the system.

The pipeline is responsible for transforming hierarchical building data into polygonal structures suitable for triangulation and rendering.

---

## 📥 1. Input Data Structure

The system starts from a JSON file containing structured architectural information.

Each file typically includes:

- Building name
- List of floors
- Layers per floor
- Geometry definitions per layer

Each geometry entry contains:
- Vertex coordinates
- Room identifier
- Room type
- Surface information
- Metadata (e.g. name, ID)

This structure represents the full architectural model in a hierarchical format.

---

## 🔄 2. Deserialization Process

The JSON data is deserialized into strongly typed C# objects.

This step transforms raw input into structured in-memory representations such as:

- Building objects
- Floor objects
- Layer objects
- Geometry objects

### Purpose

- Enable type-safe processing
- Simplify traversal of architectural hierarchy
- Prepare data for geometry reconstruction

---

## 🧱 3. Geometry Reconstruction

After deserialization, the system reconstructs geometric structures from raw coordinate data.

This includes:

- Building polygonal representations from vertex lists
- Ensuring proper vertex ordering
- Preparing closed shapes for triangulation

Each room or structural element becomes a **simple polygon** representation.

---

## 🔺 4. Triangulation Stage

Once polygons are reconstructed, they are passed to the triangulation engine.

The system uses two main approaches:

### Ear Clipping Algorithm
- Used for simple polygons
- Produces O(n²) triangulation
- Suitable for standard architectural rooms

### Delaunay / eDelaunay Triangulation
- Used for complex geometries
- Handles constraints and edge cases
- Supports holes and irregular structures

---

## ⚠️ Handling Complex Polygons

The system distinguishes between:

### Simple polygons
- Directly processed using Ear Clipping
- No self-intersections
- Suitable for most architectural rooms

### Complex polygons
- May contain holes or irregular structures
- Require Delaunay-based triangulation
- Handled as constrained geometry problems

---

## 🧠 Design Decision

The system prioritizes:

- correctness over approximation
- robustness over simplicity
- support for real architectural data

In practice, this means fallback to Delaunay triangulation when Ear Clipping is insufficient.

---

## 🔄 Output of Pipeline

The final output of this pipeline is:

- A list of triangle indices
- Vertex buffer data
- Structured mesh representation

This data is then forwarded to:

- Unity rendering engine (3D visualization)
- Web frontend (2D representation)

---

## 🎯 Summary

The geometry pipeline acts as the core transformation layer of the system:

**JSON Data → Structured Objects → Polygons → Triangulation → Mesh Data**

It bridges the gap between architectural data and real-time visualization.
