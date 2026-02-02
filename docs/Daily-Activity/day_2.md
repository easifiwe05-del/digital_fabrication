# Activity of Day 2: Digital Modeling for Fabrication

## Summary

Day 2 focuses on **digital modeling for fabrication**—the process of creating precise, production-ready digital designs that translate directly into manufacturing instructions. We explore how parametric 3D modeling and 2D vector design enable accurate fabrication while preventing costly errors and material waste.

**Key Concepts:**
- Digital models as manufacturing instructions
- Precision through parametric constraints
- Design for Manufacturing (DFM) principles
- Dimensional accuracy and real-world scaling

## Learning Objectives

- Understand how digital models control fabrication accuracy
- Learn parametric constraint-based modeling using FreeCAD
- Apply 2D vector design principles for laser cutting using Inkscape
- Recognize the relationship between digital geometry and physical fabrication
- Identify and troubleshoot common modeling errors

## 1. Introduction: Digital Modeling for Fabrication

### What is Digital Modeling for Fabrication?

A digital model is a **visual representation and instruction set** for manufacturing machines. Unlike artistic 3D models, fabrication models prioritize:

- **Accuracy:** Exact dimensions that machines can execute
- **Manufacturability:** Geometry that production equipment can handle
- **Material Awareness:** Designs that account for material properties and constraints
- **File Readiness:** Proper formats (STL, G-code, SVG, DXF) for specific machines

!!! warning "Critical Distinction"
    A visually correct model may still be fabrication-incorrect. Focus on **structural integrity** and **machine readability**, not just aesthetic appeal. This ensures successful physical output.

### Why Modeling for Fabrication Matters

Proper digital modeling:
- Reduces fabrication failures and cost overruns
- Minimizes material waste through optimized designs
- Enables fast iteration and design modifications
- Prevents machine errors and tool breakage
- Creates reusable, parametric design systems

### Precision Modeling and Scale Control

**Key Principles:**

| Principle | Description | Impact |
|-----------|-------------|--------|
| **Accurate Dimensions** | All measurements defined to appropriate precision (±0.1mm to ±1mm depending on process) | Ensures parts fit and function correctly |
| **Parametric Constraints** | Geometric relationships that control dimensions and proportions | Allows rapid design modification |
| **Real-World Scale** | Models created at 1:1 scale matching fabrication dimensions | Prevents fabrication errors due to scaling mistakes |
| **Fully Constrained Sketches** | Zero degrees of freedom prevents unintended changes | Ensures design stability and reproducibility |

Tools like **FreeCAD** empower designers with exact measurements, constraint-based sketches, and editable parameters, translating conceptual designs into tangible realities with precision.

### 3D Modeling for Fabrication: Key Practices

**Essential Techniques:**

1. **Fully Constrained Sketches** - Prevent unintended changes through geometric and dimensional constraints
2. **Parametric Dimensions** - Allow for easy design modifications without rebuilding
3. **Solid Modeling** - Ensure physical integrity and accurate volume calculations
4. **Feature-Based Workflow** - Use operations (Pad, Pocket, Fillet) that machines can execute

---

## Activity 1: L-Shaped Mounting Bracket (3D Modeling in FreeCAD)

### Design Overview

!!! info "Design Goal"
    Create a functional **L-shaped mounting bracket** demonstrating fundamental 3D modeling operations used in fabrication-ready designs.

**Design Characteristics:**
- Two flat faces at 90° angle
- Two circular holes for fasteners (screws or bolts)
- Simple, manufacturable geometry with no complex curves
- One filleted corner for safety and manufacturability
- Solid structure suitable for CNC milling or 3D printing

### Modeling Workflow

#### Step 1: Base Sketch (2D Profile)

- Create a new sketch on a reference plane
- Draw the **L-shaped 2D profile** using line tools
- Define the overall dimensions and proportions
- Create a closed, valid sketch profile

**Key Considerations:**
- Sketch lines must form a closed loop
- Use construction lines for reference geometry
- Keep geometry simple and manufacturable

![FreeCAD L-Shaped 2D Sketch Profile](./images/day_2/freecad_step1_sketch.jpg){ width=500 align=center }

**Figure:** Initial 2D L-shaped profile created in FreeCAD Sketcher workbench

#### Step 2: Apply Geometric Constraints

Constrain the sketch to ensure design intent:

- **Horizontal/Vertical Constraints:** Ensure edges align to axes
- **Parallel/Perpendicular Constraints:** Control angular relationships
- **Equal Constraints:** Make dimensions consistent
- **Coincident Constraints:** Align endpoints and intersections

**Result:** A fully constrained sketch (degrees of freedom = 0)

![Fully Constrained Sketch with Dimensions](./images/day_2/freecad_step2_constrained.jpg){ width=500 align=center }

**Figure:** Sketch with all geometric and dimensional constraints applied, showing dimensional values (red) and constraint indicators

#### Step 3: Apply Dimensional Constraints

Define exact measurements:

- Overall length, width, and height of bracket arms
- Thickness of material
- Distance between holes
- Corner radius for fillet area

**Key Point:** Every dimension drives design intent. Parametric values allow rapid iteration.

#### Step 4: Pad (Extrude to 3D)

- Select the fully constrained 2D sketch
- Apply the **Pad tool** to extrude perpendicular to sketch plane
- Set extrusion distance (usually material thickness)
- Result: Solid 3D bracket base

![3D Padded Bracket Base](./images/day_2/freecad_step4_pad.jpg){ width=500 align=center }

**Figure:** L-shaped profile extruded into 3D solid form using Pad operation

#### Step 5: Create Mounting Holes

- Select appropriate face for hole placement
- Create new sketch on that face
- Draw **two circles** using circle tool
- Apply **Equal constraint** to ensure identical diameters
- Apply **geometric constraints** to position holes symmetrically

- Use **Pocket tool** with settings:
  - Type: Through All (creates holes through entire bracket)
  - Profile: Circle sketches

- Apply **Chamfer** to circular edges:
  - Removes sharp edges around holes
  - Creates slight bevels for fastener alignment
  - Typical chamfer: 0.5mm - 1mm

![Bracket with Holes and Chamfered Edges](./images/day_2/freecad_step5_holes_chamfer.jpg){ width=500 align=center }

**Figure:** 3D model showing two circular mounting holes with chamfered edges for fastener alignment

#### Step 6: Apply Fillet to Edges

- Identify sharp external edges (particularly the L-corner)
- Select **Fillet tool**
- Apply fillet radius (typically 1-2mm for small parts)

**Benefits:**
- Removes sharp edges for safety
- Improves manufacturability
- Reduces stress concentrations
- Enhances aesthetic quality

### Final Result

The completed L-shaped mounting bracket includes:
- Solid 3D geometry ready for fabrication
- Two through-holes for fasteners
- Chamfered hole edges for assembly
- Rounded corner fillet
- Full dimensional definition and parametric control

![Final L-Shaped Mounting Bracket](./images/day_2/freecad_final_bracket.jpg){ width=500 align=center }

**Figure:** Finished L-shaped mounting bracket with all features: two mounting holes, chamfered edges, and filleted corner for manufacturability

### Common Challenges and Solutions

| Challenge | Cause | Solution |
|-----------|-------|----------|
| **Sketch won't constrain** | Under-constrained with missing dimensions or relationships | Add missing geometric/dimensional constraints; verify all degrees of freedom are removed |
| **Pad fails to execute** | Sketch not fully closed or contains errors | Check sketch for gaps, overlapping lines, or invalid geometry; fix and retry |
| **Hole placement inaccurate** | Sketch on wrong face or constraints misaligned | Verify sketch plane; re-sketch holes with precise coordinate constraints |
| **Fillet fails on sharp corner** | Radius too large for feature size; conflicting geometry | Reduce fillet radius; ensure edges are distinct and not shared with other features |
| **Model dimensions unexpected** | Unit mismatch or constraint values unclear | Verify document units; check all dimensional constraints; adjust as needed |
| **File too large/slow** | Too many features or high polygon resolution | Simplify geometry; delete construction sketches; reduce feature complexity |

---

## Activity 2: Press-Fit Box Panel (2D Vector Design in Inkscape)

### Design Overview

!!! info "Design Goal"
    Create a **2D press-fit box panel** using vector geometry for laser cutting. Design enables flat-pack assembly without fasteners—panels slide and lock together through precisely sized slots.

**Design Characteristics:**
- Flat rectangular panel
- Rectangular slots cut along edges
- Slot widths precisely matched to material thickness
- Designed for interlocking assembly
- Entirely 2D vector-based geometry
- 1:1 scale for accurate fabrication

### Design Principles for Press-Fit Assembly

**Key Considerations:**

1. **Material Thickness Accuracy** - Slots must match cutting sheet thickness exactly (±0.1mm)
2. **Slot Length** - Must accommodate interlocking with adjacent panels
3. **Kerf Compensation** - Account for laser kerf (material removed by laser)
4. **Stress Points** - Design tabs and slots to distribute stress evenly
5. **Flat-Pack Efficiency** - Nest parts to minimize material waste

### Modeling Workflow in Inkscape

#### Step 1: Set Up Document

- Create new document at actual project scale (1:1)
- Set document dimensions to cutting area size
- Enable grid for precise alignment
- Configure rulers in appropriate units (mm)

#### Step 2: Create Base Rectangle

- Draw main panel rectangle using rectangle tool
- Set dimensions matching box panel requirements
- Lock rectangle to prevent accidental movement

#### Step 3: Create Tabs and Slots

**Tabs (outward projections):**
- Draw rectangles extending from panel edges
- Dimension to material thickness + small clearance
- Position symmetrically on edges where assembly occurs

**Slots (inward cuts):**
- Draw rectangular profiles representing slot openings
- Width = material thickness (typically 3mm for acrylic/plywood)
- Length = depth needed for interlocking
- Position to align with adjacent panel tabs

![Initial Press-Fit Box Geometry](./images/day_2/inkscape_step3_tabs_slots.jpg){ width=500 align=center }

**Figure:** Initial press-fit box panel geometry showing rectangular tabs and slot placements for interlocking assembly

#### Step 4: Create Circular Edge Details

- Draw circles for rounded corners or design elements
- Apply **Union** tool to merge circles with base geometry
- Creates smooth, continuous outlines

#### Step 5: Apply Path Operations

**Union Operation:**
- Select multiple elements to merge
- Apply Union (Path menu) to combine into single shape
- Result: Single unified outline

**Difference Operation:**
- Select outer boundary and inner elements
- Apply Difference to subtract inner geometry from outer
- Creates holes and slots as negative space

**Process Example:**
1. Draw complete panel outline (rectangle + tabs + circles)
2. Draw all slot rectangles as separate elements
3. Select panel outline + slot rectangles
4. Apply Difference → slots become cut-outs
5. Result: Single panel with integrated slots ready for laser cutting

#### Step 6: Verify Geometry

- Check all paths are closed and valid
- Verify no overlapping or self-intersecting geometry
- Convert all text to paths (if text is used)
- Ensure strokes are converted to fills for cutting

### Final Design

The completed press-fit box panel includes:
- Main rectangular outline
- Precisely dimensioned slots for interlocking
- Clean vector paths ready for laser cutting
- 1:1 scale matching actual material thickness
- Optimized nesting for material efficiency

![Complete Press-Fit Box Assembly](./images/day_2/inkscape_final_pressfitbox.jpg){ width=500 align=center }

**Figure:** Finished press-fit box panel design showing all interlocking panels with precisely sized rectangular slots for flat-pack assembly

### Common Challenges and Solutions

| Challenge | Cause | Solution |
|-----------|-------|----------|
| **Slots too tight for assembly** | Dimensions don't match material thickness; kerf not accounted for | Measure actual material thickness; add 0.1-0.2mm clearance; account for laser kerf (typically 0.1-0.3mm) |
| **Panels won't interlock** | Slot depth insufficient or geometry misaligned | Verify slot length matches adjacent tab size; check alignment of slot pairs |
| **Paths have gaps or overlaps** | Geometry created with line tools rather than proper shapes | Use rectangle/circle tools; apply Union/Difference for clean operations; delete overlapping segments |
| **Design won't export to DXF/SVG** | Path not properly closed or contains unmerged elements | Select all; apply Union to ensure single path; convert text to paths; check for stray lines |
| **Laser cuts too deep/shallow** | File format issue or machine power miscalibration | Verify stroke weight is consistent; use proper file format for laser software; test on scrap material |
| **Parts don't nest efficiently** | Layout wastes material; parts placed randomly | Organize parts in rows/columns; minimize gaps between parts; rotate parts for optimal fit |
| **Kerf compensation forgotten** | Geometry dimension doesn't account for material removal | Add 0.1-0.2mm to all internal dimensions and subtract from external dimensions; test on sample material |

---

## Comparison: FreeCAD vs. Inkscape

| Aspect | FreeCAD (3D) | Inkscape (2D) |
|--------|-------------|--------------|
| **Purpose** | 3D solid modeling for CNC, 3D printing | 2D vector design for laser cutting, vinyl cutting |
| **Output Format** | STL, STEP, IGES, G-code | SVG, DXF, PDF |
| **Primary Constraint Method** | Sketch constraints + feature operations | Path operations (Union, Difference) |
| **Manufacturability Focus** | Structural integrity, material thickness | Sheet layout, cut accuracy, nesting efficiency |
| **Learning Curve** | Moderate to steep | Gentle to moderate |
| **Best For** | Mechanical parts, functional geometry | Flat patterns, graphic designs, sheet material layouts |

---

## Key Takeaways

### Conceptual Understanding

**Digital modeling is not just visualization—it is manufacturing instruction.** Every dimension, constraint, and feature in your model directly affects fabrication outcome.

**The Design-to-Fabrication Translation:**
- Sketch → Define 2D profile or geometry
- Constrain → Apply relationships ensuring design intent
- Dimension → Assign exact measurements
- Feature → Build 3D geometry (Pad, Pocket, etc.) or path operations
- Export → Generate machine-ready files (G-code, DXF, STL)

### Practical Skills Developed

By completing these activities, you have:

1. Created a **fully parametric 3D model** with geometric constraints
2. Applied **feature-based modeling** operations (Pad, Pocket, Fillet, Chamfer)
3. Designed **2D vector geometry** for precision cutting
4. Used **path operations** to create complex shapes from simple elements
5. Considered **manufacturability** at every design decision
6. Exported models in **appropriate formats** for different fabrication methods

### Design for Fabrication (DFM) Principles Applied

- Constraints prevent design drift and enable iteration
- Parametric dimensions connect design logic to specific values
- Feature-based approach mirrors machine capabilities
- 1:1 scale ensures dimensional accuracy
- Simplicity and cleanness prevent fabrication errors

---

## Download References

[ L-Shaped Mounting Bracket (FreeCAD)](../downloads/Day2_Activity1_LShaped_Bracket.FCStd){: .md-button .md-button--primary }

[ Press-Fit Box Panel (Inkscape)](../downloads/Day2_Activity2_PressFitBox.svg){: .md-button .md-button--primary }

---

## Resources

**FreeCAD Learning:**
- [FreeCAD Official Documentation](https://wiki.freecadweb.org/)
- [Parametric Constraints Guide](https://wiki.freecadweb.org/Sketcher_tutorial)
- [Pad, Pocket, Fillet Operations](https://wiki.freecadweb.org/PartDesign_Workbench)

**Inkscape Learning:**
- [Inkscape Official Tutorials](https://inkscape.org/learn/)
- [Path Operations Reference](https://inkscape.org/en/learn/tutorials/)
- [Vector Design Best Practices](https://inkscape.org/en/learn/)

**Digital Fabrication:**
- [Design for Laser Cutting Guide](https://www.epiloglaser.com/resources/how-to/design-for-laser-cutting)
- [Design for 3D Printing Best Practices](https://ultimaker.com/en/resources/52692-design-guidelines-for-3d-printing)

---

## Reflection Questions

- How did constraints in FreeCAD help prevent design errors?
- What was the relationship between slot dimensions and material thickness in Inkscape?
- How would you modify these designs for a different material or fabrication method?
- What manufacturing limitations did you discover during modeling?
- How does modeling at 1:1 scale change your design process?

