# Backend Overview (ASP.NET Core MVC)

## Overview

The backend system is responsible for managing CAD-derived data, model metadata, and structural organization of architectural models.

It acts as the central coordination layer between data ingestion (AutoCAD), geometry processing, and visualization systems.

---

## 🏗️ Architecture

The backend is built using:

- ASP.NET Core MVC
- C#
- REST-like structured endpoints (conceptually)

It follows the Model-View-Controller (MVC) pattern to separate concerns between data, logic, and presentation.

---

## 📦 Core Responsibilities

### 1. Data Management

The backend handles:
- Import of CAD-derived polyline data
- Storage of model metadata
- Organization of architectural model structures

---

### 2. Model State Handling

Each model contains structured information such as:
- Visible and hidden elements
- Layer/floor information
- Object grouping (rooms, structural zones)
- Versioning and metadata tracking

---

### 3. Geometry Preparation

Before sending data to the rendering pipeline, the backend:
- Parses raw CAD input
- Structures geometric relationships
- Prepares data for triangulation and transformation

---

## 🔄 Communication Flow

Backend interacts with:

- Frontend (UI layer)
- Geometry processing pipeline
- Unity rendering system

Data is passed in a structured format that allows each subsystem to operate independently.

---

## 🧱 MVC Structure

### Model
Represents:
- CAD entities
- Metadata structures
- Model configuration data

### View
Not directly used for rendering geometry, but supports:
- Data presentation in web UI
- Model selection interface

### Controller
Handles:
- Requests from frontend
- Data preparation
- Coordination with processing and rendering layers

---

## ⚙️ Design Principles

The backend is designed with the following principles:

- Separation of concerns
- Stateless processing where possible
- Clear separation from rendering logic
- Data-centric architecture (no visualization responsibilities)

---

## 🎯 Role in System

The backend serves as the **central data orchestration layer**, ensuring that:

- CAD data is properly structured
- Geometry pipeline receives clean input
- Rendering systems receive optimized data
- UI can interact with model states consistently
