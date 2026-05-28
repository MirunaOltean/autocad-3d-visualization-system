# Frontend Overview (Web UI Layer)

## Overview

The frontend layer provides the user interface for interacting with the system, enabling users to load, visualize, and switch between different representations of architectural models.

It serves as the bridge between user actions and the backend + rendering systems.

---

## 🧱 Technologies Used

- HTML5
- CSS3
- JavaScript (Vanilla)

The frontend is intentionally lightweight and focused on functionality rather than framework-heavy design.

---

## 🎯 Core Responsibilities

### 1. Model Selection

The UI allows users to:
- Browse available CAD-based models
- Load selected architectural datasets
- Trigger visualization pipeline execution

---

### 2. Visualization Control

Users can switch between different rendering modes:

- 🟦 2D Architectural View (with semantic overlays)
- 🔺 3D View (pure geometry)
- 👤 Silhouette View (simplified structure)

Each mode triggers a different rendering configuration in the backend/Unity pipeline.

---

### 3. Interaction Handling

The frontend manages:
- User input events (clicks, selections)
- UI state updates
- Communication with backend services
- Triggering model reload or transformation actions

---

## 🔄 Communication Flow

Frontend interacts with:

- ASP.NET Core backend (data requests)
- UnityViewer (rendering output)
- Model metadata services

Data is exchanged in a structured way to ensure consistency across all visualization layers.

---

## 🖥️ UI Structure

The interface is organized into:

- Model selection panel
- Visualization canvas/container
- Control panel (view switching, toggles)
- Metadata display section

---

## ⚙️ Design Approach

The frontend was designed with the following principles:

- Minimal and functional UI
- Separation from geometry logic
- Clear interaction with backend services
- Compatibility with Unity WebGL embedding

---

## 🎯 Role in System

The frontend acts as the **user control layer**, responsible for:

- Initiating data loading
- Switching visualization modes
- Displaying model state information
- Embedding Unity-rendered content into the web interface
