# Day 5 – Digital Fabrication I: CNC and Laser Cutting

## Introduction

Day 5 focused on two complementary subtractive fabrication technologies: **CNC machining** and **laser cutting**. Both processes translate digital design files into precisely fabricated physical parts, but they differ fundamentally in their cutting mechanism, material compatibility, and workflow requirements.

**CNC (Computer Numerical Control) machining** removes material mechanically using a rotating tool driven along computer-generated toolpaths. **Laser cutting** removes material thermally, using a focused beam of light to vaporise or melt through sheet material. Understanding both processes — their operating principles, constraints, file preparation requirements, and safety procedures — is essential for selecting the appropriate fabrication method for a given design brief.

---

## Learning Objectives

By the end of this session, students should be able to:

- Distinguish between CNC machining and laser cutting as subtractive fabrication processes.
- Identify the primary hardware components of a laser cutting system and describe their function.
- Define kerf, feeds, and speeds, and explain how each affects fabrication output quality.
- Differentiate between 2D and 2.5D fabrication strategies and identify when each applies.
- Prepare design files correctly for both CNC and laser cutting workflows.
- Apply established safety protocols when operating a laser cutter.
- Execute a layered engraving-and-cutting workflow and critically evaluate the result.

---

## CNC Machining Principles

**CNC machining** is a subtractive manufacturing process in which a rotating cutting tool removes material from a solid workpiece according to computer-generated instructions. The process is governed by a set of motion commands — collectively referred to as **G-code** — that specify tool position, speed, and depth at every point in the operation.

Key characteristics of CNC machining:

- **Axis control:** Standard CNC routers operate on three axes (X, Y, Z). Multi-axis machines add rotational axes (A, B) for complex geometries.
- **Tooling:** End mills, ball-nose bits, and V-bits are selected based on the required cut profile, material hardness, and finish quality.
- **Material removal strategy:** Operations are classified by cut type — profiling (outer contour), pocketing (hollow interior), drilling, and engraving. Each requires a distinct toolpath type in CAM software.
- **Workholding:** Material must be rigidly fixed to the spoilboard using clamps, vacuum fixtures, or double-sided tape to prevent movement during cutting.
- **Spoilboard:** A sacrificial substrate sits beneath the workpiece to protect the machine bed from through-cuts and to allow flush cutting of the full material thickness.

**CAM (Computer-Aided Manufacturing)** software — such as Fusion 360 CAM, VCarve, or FreeCAD Path — translates a 3D or 2D design file into G-code. The workflow moves from design (CAD) → toolpath generation (CAM) → machine execution (CNC controller).

---

## Laser Cutting: System Architecture

A laser cutter is an integrated electromechanical system composed of six interdependent subsystems. Understanding each component is necessary for diagnosing machine behaviour and optimising output quality.

### Laser Source

The laser source generates the coherent beam used for all cutting and engraving operations. The three types relevant to digital fabrication are:

| Laser Type | Wavelength     | Primary Application                          |
|------------|----------------|----------------------------------------------|
| CO₂        | 10,600 nm      | Non-metals: wood, acrylic, leather, cardboard |
| Fiber      | 1,060–1,080 nm | Metals and engineered plastics               |
| Nd:YAG     | 1,064 nm       | Precision metal marking and deep engraving   |

**CO₂ lasers** are standard in fabrication labs. They are gas lasers that produce their beam from a mixture of carbon dioxide, nitrogen, and helium. Their wavelength is efficiently absorbed by organic and polymer-based materials, producing clean cuts with minimal residue. Source parameters include:

- **Power (Watts)** — sets the maximum energy output; determines cutting depth capacity.
- **Mode** — continuous wave (CW) mode for cutting; pulsed mode for controlled engraving with reduced heat input.

### Beam Delivery System

The beam travels from the laser tube to the cutting head via a sequence of three precision-aligned mirrors and a focusing lens:

```
Laser Tube → Mirror 1 → Mirror 2 → Mirror 3 → Focusing Lens → Material Surface
```

- **Mirrors** redirect the beam along the machine's motion axes. Misalignment at any mirror diffuses the beam, lowers power density at the focal point, and can cause internal damage.
- **Focusing lens** converges the beam to a minimum spot diameter at the focal point. A smaller spot produces a finer kerf and higher energy density. The focal length must be matched to the material thickness.

### Motion System

The cutting head is driven in two dimensions by a gantry-based motion system:

- **X-axis:** The cutting head moves laterally across the gantry beam.
- **Y-axis:** The gantry beam moves along the machine frame from front to back.
- **Drive mechanism:** Belt-and-pulley systems for speed-optimised machines; lead screw drives for precision-critical applications.
- **Motor type:** Stepper motors in entry-level and mid-range machines; servo motors in industrial systems where higher positioning accuracy and speed are required.

### Workbed

The workbed supports the material and allows combustion gases and debris to be extracted downward during cutting.

| Workbed Type | Description                                      | Recommended Use                    |
|--------------|--------------------------------------------------|------------------------------------|
| Honeycomb    | Aluminium grid; minimises surface contact area   | General cutting and engraving      |
| Slat         | Steel slat strips; supports heavy sheet stock    | Thick or heavy materials           |
| Vacuum       | Suction fixture holds flexible material flat     | Thin film, paper, and fabric       |

The **honeycomb bed** is standard in fabrication labs. Minimal contact between the bed surface and the underside of the material reduces back-reflection and prevents heat accumulation at contact points, which would otherwise cause scorching.

### Exhaust and Cooling Systems

**Exhaust:** Vaporised material generates a laser plume containing combustion gases, fine particulates, and — depending on the material — potentially toxic compounds. An inline exhaust fan draws this plume downward through the honeycomb bed and vents it outside the workspace. Active exhaust is mandatory during all cutting and engraving operations to protect the operator, preserve optical cleanliness, and prevent beam scatter on smoke.

**Water cooling:** CO₂ laser tubes require a closed-loop water chiller to regulate tube temperature during operation. Insufficient cooling causes output power degradation and permanently shortens tube service life.

**Electronic cooling:** The power supply unit, controller board, and motor drivers generate heat continuously during operation. Dedicated fans integrated into the machine cabinet dissipate this heat, preventing thermal overload that would otherwise cause operational errors or permanent damage to the control electronics.

### Control System and Software

An on-board controller — commonly the **Ruida** controller for CO₂ systems — receives motion and power commands from the connected workstation and drives all machine axes and the laser source in synchrony.

Common laser control software:

| Software    | Platform               | Key Capability                                          |
|-------------|------------------------|---------------------------------------------------------|
| LightBurn   | Windows, macOS, Linux  | Full layer control, parameter preview, kerf compensation |
| RDWorks     | Windows only           | Native Ruida controller interface                       |
| LaserWeb    | Browser-based          | Open-source; compatible with Grbl-based controllers     |

**Accepted design file formats:** SVG and DXF for vector operations; PNG and BMP for raster engraving. All vector geometry must consist of closed paths with no duplicate lines or open contours.

**Operational parameters configured per layer:**

- **Power (%)** — fraction of maximum output. Higher power removes more material per pass.
- **Speed (mm/s)** — head travel velocity. Lower speed increases energy dwell time per unit length, producing deeper cuts.
- **Frequency (Hz)** — pulse rate (pulsed mode). Affects edge smoothness and heat input per pulse.
- **Passes** — number of repeated traversals of the same path. Used to cut materials exceeding single-pass depth capacity.

---

## Toolpaths, Kerf, Feeds, and Speeds

### Kerf

**Kerf** is the width of material removed by the laser beam along a cut path. Because the focused beam has a finite spot diameter, every cut removes a measurable strip of material from both sides of the design line.

- Typical kerf range: **0.1 mm – 0.5 mm**, depending on material type, thickness, laser power, and focus distance.
- For dimensionally critical designs — particularly interlocking assemblies using press-fit joints, slots, or tabs — the design file must be offset to compensate for kerf. Standard practice is to offset each cut path by half the measured kerf value in the appropriate direction (inward for internal features, outward for external profiles).
- Kerf compensation that is not applied or is incorrectly calculated results in joints that are either too loose to hold or too tight to assemble without damage.

### Feeds and Speeds

In the context of laser cutting, **feeds** refers to the travel speed of the cutting head (mm/s), and **speeds** refers to the laser power setting (%). These two parameters are inversely coupled: for a given material and thickness, reducing travel speed while increasing power achieves greater cut depth, while increasing speed with lower power produces lighter surface engraving.

The correct feed-and-speed combination is determined by:

1. **Material type** — different materials absorb laser energy at different efficiencies.
2. **Material thickness** — thicker material requires more energy per unit length.
3. **Required finish** — cut edges, engraved surfaces, and scored fold lines each require different parameter sets.
4. **Number of passes** — multiple lower-power passes can produce cleaner edges on sensitive materials than a single high-power pass.

---

## 2D and 2.5D Fabrication Strategies

**2D fabrication** refers to operations that produce flat parts by cutting through the full thickness of a sheet material along a 2D contour path. Laser cutting is inherently a 2D fabrication process — every cut operation produces a flat profile determined by the design geometry.

**2.5D fabrication** extends the 2D paradigm by introducing controlled variation in cut depth without producing fully three-dimensional geometry. In laser cutting, 2.5D operations include:

- **Surface engraving** — the beam removes only the top surface layer, producing a visible mark without penetrating the full material thickness.
- **Score lines** — partial-depth cuts that create deliberate weakening lines for folding or controlled fracture.
- **Multi-pass stepped pocketing** — repeated passes at incremental Z-offsets remove material progressively to create recessed areas.

In CNC machining, 2.5D strategies include pocketing, slotting, and contouring at variable depths, all generated from 2D profiles extruded or offset in the Z-axis within CAM software.

---

## File Preparation for CNC and Laser Machines

Correct file preparation is the primary determinant of output quality in both CNC and laser cutting workflows. Errors in the design file — open paths, duplicate geometry, incorrect units, or missing layer separation — propagate directly into the fabricated part and cannot be corrected at the machine level.

### Laser Cutting File Requirements

- **Format:** SVG or DXF for vector operations. Geometry must be in vector form; raster images cannot be used for precision cutting paths.
- **Path integrity:** All cut paths must be fully closed. Open paths produce incomplete cuts. Overlapping geometry causes the beam to traverse the same path twice, increasing heat input and potentially burning the material.
- **Layer separation:** Engraving operations and cutting operations must be assigned to separate layers, each with its own power and speed parameters. Mixing operations on a single layer prevents independent parameter control.
- **Colour coding:** Most laser software assigns parameters by colour. Engraving paths and cut paths must be different colours to allow the controller to apply distinct settings to each.
- **Design scaling:** Confirm the document units and scale before export. A design created at 1:1 in millimetres must be exported and imported at the same scale.

### CNC File Requirements

- **Format:** G-code (`.nc`, `.gcode`, `.tap`), generated by CAM software from a CAD model (STL, STEP, or DXF source).
- **Toolpath type selection:** Profile, pocket, drill, and engrave operations are each generated as separate toolpaths with dedicated tool, feed, speed, and depth parameters.
- **Tabs:** Thin material bridges (tabs) are added to hold parts to the sheet during cutting and prevent them from shifting when the final contour cut is made. Tabs are manually removed after machining.
- **Safe Z height:** A retract height above all clamps and fixtures must be set to prevent the tool from colliding with workholding during rapid moves.

---

## Assembly Methods for Flat-Fabricated Parts

Parts produced by laser cutting and CNC routing are typically flat profiles. Structural three-dimensional assemblies are achieved through one of the following joinery methods:

- **Press-fit joints** — slots and tabs dimensioned to the material thickness minus kerf compensation, designed to assemble with friction alone. No fasteners or adhesive required. Tolerances must be validated with a test cut before committing to full production.
- **Slots and tabs** — interlocking geometry that provides mechanical indexing and alignment during assembly. Common in flat-pack structural components.
- **Mechanical fasteners** — bolts, screws, and rivets provide strong, reversible connections. Require drilled or cut clearance holes in the design file.
- **Adhesives** — epoxy, wood glue, or cyanoacrylate applied after assembly. Used where press-fit alone is insufficient and where disassembly is not required.

Joint type selection depends on the required structural performance, assembly reversibility, and the tolerance achievable by the fabrication machine being used.

---

## Safety Protocols

Laser cutters present hazards from optical radiation, toxic fumes, fire, and electrical systems. The following rules are mandatory and non-negotiable:

1. **Assess material compatibility before loading.** Only use materials confirmed as safe for laser cutting. PVC and unknown plastics are strictly prohibited — they release chlorine gas and hydrochloric acid fumes when cut, which are toxic and corrosive to both the operator and the machine optics.
2. **Log all machine use and obtain authorisation.** All jobs must be registered before the machine is operated.
3. **Wear appropriate laser safety eyewear.** Goggles must be rated for the machine's specific wavelength. Standard tinted safety glasses do not provide adequate protection against a CO₂ or fiber laser beam.
4. **Never look into the beam or beam path.** The lid must remain closed during operation. Even a reflected or diffuse beam can cause irreversible retinal damage.
5. **Never leave the machine unattended.** Materials can ignite during cutting. The operator must remain present and attentive for the full duration of the job.
6. **Keep the laser beam below eye level.** Never position yourself in the beam axis or bend over the machine during operation. Direct or reflected exposure at eye height poses an immediate risk of irreversible retinal injury.
7. **Never wear watches or reflective jewellery during alignment or operation.** Reflective surfaces on the wrist or hands can redirect the beam in unpredictable directions, creating secondary hazards outside the cutting area.

---

## Machine Maintenance

Consistent maintenance is essential for sustaining output quality, extending component service life, and ensuring safe operation. The PDF guidance identifies three mandatory maintenance categories:

- **Optical cleaning:** The focusing lens and all beam-path mirrors must be cleaned regularly using appropriate optical-grade solvents and lint-free swabs. Residue from laser plume accumulates on optical surfaces during cutting, reducing beam transmission, increasing focal scatter, and causing localised heating that can crack or permanently fog the optics.
- **Calibration checks:** Mirror alignment and focal length must be verified periodically, particularly after the machine has been moved or subjected to vibration. A misaligned beam produces inconsistent cut quality and incorrect kerf positioning even when software parameters are set correctly.
- **Mechanical lubrication:** The linear rails, lead screws, and belt-drive components require periodic lubrication to maintain smooth, low-friction motion. Inadequate lubrication increases motor load, causes positioning errors at high speeds, and accelerates wear of rails and bearings.

---

## Results and Observations

The practical component of this session involved preparing a two-layer design file (an engraving layer and a cutting layer), loading it onto a CO₂ laser cutter via a network connection, and producing a star-shaped piece from plywood with names engraved on its surface and the outer profile laser-cut to shape. The engraving operation was executed first at low power and high speed, followed by the cutting operation at high power and low speed. The output demonstrated the following:

- **Engraving quality:** The engraved text and surface detail were legible and consistent in depth, with no burn-through, indicating appropriate power calibration for the surface operation.
- **Cut edge quality:** The cut edges were clean and required no secondary finishing. Minimal charring at the edges confirmed that the speed parameter was set high enough to prevent excessive heat accumulation along the cut path.
- **Dimensional accuracy:** The finished piece dimensions matched the design intent, consistent with correct kerf compensation on the outer cut contour.
- **Workflow sequencing:** Executing the engraving layer before the cutting layer is operationally mandatory. Completing the cut first separates the piece from the sheet, making accurate re-registration for a subsequent engraving pass impossible.

---

## Reflection

This session demonstrated that laser cutting is not a single-step process but a coordinated system requiring correct setup, file preparation, parameter selection, and sequencing at every stage. The most significant conceptual insight is that **the digital file and the physical machine must be understood as a coupled system**: errors in the design file — open paths, missing layer separation, absent kerf compensation — manifest directly and irreversibly in the fabricated part. These errors cannot be corrected at the machine level; they must be resolved before the job is sent to the controller.

A secondary observation concerns machine integration and lab management. Modern laser cutters support network-based access via IP address, allowing job files to be sent and machine status to be monitored from a connected workstation. In shared fabrication environments, this reduces congestion around the equipment and enables orderly job queuing — reinforcing that digital fabrication competency extends beyond design and operation to include an understanding of how machines are administered within a working lab infrastructure.

---

## References

- *Day 5 – Digital Fabrication I: CNC & Laser Cutting*, ACEIoT Digital Fabrication Module available at [https://fablabrwanda.github.io/UR-ACEIoT/day5.html](https://fablabrwanda.github.io/UR-ACEIoT/day5.html)
- LightBurn Software Documentation. Available at: [https://lightburnsoftware.com/pages/lightburn-documentation](https://lightburnsoftware.com/pages/lightburn-documentation)
- Fab Academy. *Computer-Controlled Cutting*. Available at: [https://academy.cba.mit.edu](https://academy.cba.mit.edu)
