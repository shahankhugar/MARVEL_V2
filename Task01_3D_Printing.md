# Task 01 — Introduction to 3D Printing

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is 3D Printing?

3D printing is an additive manufacturing process where objects are built layer by layer from a digital model. The most common type used in labs and hobbyist setups is **FDM (Fused Deposition Modeling)** — where plastic filament is melted through a heated nozzle and deposited onto a build plate, one layer at a time, until the full object is formed.

---

## How It Works (FDM)

1. A 3D model is created or downloaded as an **STL file**
2. The STL is imported into a **slicer** (e.g. Ultimaker Cura, Bambu Studio, Creality Print)
3. The slicer slices the model into layers and generates **G-code** — a set of movement and extrusion instructions the printer follows
4. The printer heats the nozzle and bed to the required temperatures, then builds the object layer by layer
5. Once complete, the part is removed from the build plate

---

## STL Files

An STL (Standard Tessellation Language) file describes the surface of a 3D object as a mesh of triangles. It contains only geometry — no color, texture, or material information. STL files can be downloaded from sites like Thingiverse, Printables, or Makerworld, or exported from CAD software like Fusion 360.

---

## Key Printer Settings

| Setting | What it controls |
|---|---|
| **Nozzle temperature** | How hot the filament melts (~200°C for PLA) |
| **Bed temperature** | Adhesion of the first layer (~55°C for PLA) |
| **Layer height** | Print quality vs speed (0.2mm is standard) |
| **Infill density** | Internal fill % — affects strength and material use |
| **Print speed** | How fast the printhead moves |
| **Supports** | Structures to hold up overhanging geometry |

---

## Slicing Workflow

1. Open slicer (Ultimaker Cura / Creality Print)
2. Import STL file
3. Select printer profile and material (PLA)
4. Adjust settings (layer height, infill, supports)
5. Slice → preview layers → export G-code
6. Load G-code onto printer via SD card / USB and start print

---

## Print Done

- **Model:** Calibration Cube
- **Material:** PLA
- **Settings:** 200°C nozzle, 55°C bed, 0.2mm layers, 20% infill
- **Result:** Successful
- *(Printed under coordinator supervision)*

---

**Reference:** [Introduction to 3D Printing — Bambu Lab A1](https://youtu.be/f94CnlQ0eq4)
