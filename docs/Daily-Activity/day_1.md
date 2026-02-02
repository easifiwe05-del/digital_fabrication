# Activity of Day 1: Introduction to Modeling and Fabrication Design

## Summary

Day 1 introduces the foundational concepts bridging **design intent** and **physical reality**. We explore the design-to-fabrication continuum and contemporary digital fabrication paradigms that shape modern making practices.

## Learning Objectives

- Understand the relationship between digital modeling and physical fabrication
- Learn the design-to-fabrication continuum: Design → Model → Prototype → Fabricate → Evaluate
- Identify key digital fabrication paradigms and their applications
- Recognize how fabrication methods shape design decisions from conception

## 1. Introduction to Modeling and Fabrication

### Why Modeling & Fabrication Matter

Contemporary design practice has fundamentally shifted. Design today is **computational**, **material-driven**, and **production-aware**. Fabrication is no longer merely an end step—it actively shapes design decisions from the earliest conceptual stages.

**Key Applications:**
- **Architecture:** Parametric facades, robotically fabricated structures
- **Product Design:** Rapid prototyping, mass customization, user-centered iteration
- **Engineering:** Simulation-driven design, additive manufacturing
- **Research:** Physical computing, material experimentation, speculative design

### The Design-to-Fabrication Continuum

Design follows an **iterative cycle**, not a linear path:

```
Design → Model → Prototype → Fabricate → Evaluate → [Repeat]
```

!!! warning "Critical Insight"
    This process is **iterative, not linear**. Feedback occurs at every stage, and failure serves as a powerful learning tool. Each cycle refines understanding and improves outcomes.

**Key Phases:**

| Phase | Description |
|-------|-------------|
| **Design** | Conceptualize and define intent, goals, and constraints |
| **Model** | Create digital representations encoding design logic |
| **Prototype** | Build physical tests to validate assumptions |
| **Fabricate** | Produce final artifacts using appropriate methods |
| **Evaluate** | Assess outcomes and gather learnings for next cycle |

### Digital Fabrication Paradigms

Contemporary fabrication methods fall into four primary categories:

#### Subtractive Fabrication
**Process:** Removing material from solid stock through cutting, milling, or drilling

**Technologies:** CNC milling, laser cutting, waterjet cutting, lathe turning

**Advantages:**
- High precision and accuracy
- Excellent surface finish
- Wide material compatibility

**Constraints:**
- Material waste
- Limited to 2.5D without multi-axis machines
- Tool access limitations

**Materials:** Wood, metals, plastics, foam, composites

#### Additive Fabrication
**Process:** Building objects layer-by-layer through material deposition

**Technologies:** FDM/FFF, SLA/DLP, SLS, binder jetting, material jetting

**Advantages:**
- Complex geometries without additional cost
- Minimal material waste
- Design freedom and internal structures possible

**Constraints:**
- Visible layer lines
- Support structures required
- Material limitations
- Post-processing often needed

**Materials:** PLA, ABS, PETG, nylon, resins, metals (specialized), ceramics

#### Formative Fabrication
**Process:** Shaping material through force, heat, or pressure using molds

**Technologies:** Casting, vacuum forming, injection molding, bending, stamping, thermoforming

**Advantages:**
- Material efficiency
- High-volume production capability
- Organic, flowing forms

**Constraints:**
- Requires tooling/molds (upfront cost)
- Draft angles required
- Undercut limitations

**Materials:** Plastics, metals, concrete, composites, textiles, elastomers

#### Hybrid Fabrication
**Process:** Combining multiple fabrication paradigms sequentially or simultaneously

**Examples:**
- 3D printed molds for casting
- Additive + subtractive machining
- Laser-cut assembled components with 3D printed connectors

**Advantages:**
- Optimizes strengths of each method
- Increased geometric complexity
- Material diversity in single object

**Constraints:**
- Workflow complexity
- Multiple machines/skills required
- Alignment challenges

!!! info "Key Insight"
    **Fabrication method is a design choice, not an afterthought.** The selected paradigm influences geometry, materiality, cost, sustainability, and aesthetic expression. Expert designers think through fabrication from the earliest conceptual stages. 

## 2. Activity: Building Documentation Website with MkDocs

### Overview

We are building a documentation website using **MkDocs with Material theme** to record and showcase all course activities, design processes, and fabrication experiments. This documentation serves as both a **learning tool** and a **professional portfolio**.

!!! success "Documentation as Design Practice"
    **Documentation is not an afterthought—it is part of the design process itself.** Through documenting your work, you develop clarity of thought, communicate complex ideas, and contribute to the collective knowledge of the design community.

### Step 1: Install Prerequisites

```bash
# Install Python 3.8 or later
# Download from https://www.python.org/

# Install MkDocs and Material theme
pip install mkdocs-material
```

**Requirements:**
- Python version 3.8 or later
- pip (Python package manager)

### Step 2: Create a New MkDocs Project

```bash
# Create new documentation project
mkdocs new fabrication-docs

# Move into project directory
cd fabrication-docs
```

This creates the following structure:
```
fabrication-docs/
├── mkdocs.yml
├── docs/
│   └── index.md
└── README.md
```

### Step 3: Enable the Material Theme

Edit `mkdocs.yml` to enable Material theme and configure basic settings:

```yaml
site_name: Fabrication Documentation
site_description: Foundations of Modeling & Fabrication
site_author: Your Name

theme:
  name: material
  palette:
    primary: blue
    accent: orange
```

### Step 4: Write Documentation Content

All documentation pages are written in **Markdown** format. Place files in the `docs/` directory:

```
docs/
├── index.md                 # Home page
├── daily-activity/
│   ├── day_1.md
│   ├── day_2.md
│   └── ...
├── images/
│   └── ...
└── stylesheets/
    └── extra.css
```

### Step 5: Configure Navigation

Define site navigation in `mkdocs.yml` to organize pages hierarchically:

```yaml
nav:
  - Home: index.md
  - Daily Activities:
    - Day 1: daily-activity/day_1.md
    - Day 2: daily-activity/day_2.md
    - Day 3: daily-activity/day_3.md
```

### Step 6: Preview the Website Locally

Run the development server to preview changes in real time:

```bash
mkdocs serve
```

Open your browser to `http://127.0.0.1:8000` to view your site. Changes auto-reload as you edit files.

### Step 7: Enable Material Features (Optional)

Add advanced Material theme features to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.tabs
    - navigation.sections
    - toc.integrate
    - search.suggest
    - content.code.copy
```

### Step 8: Add Recommended Markdown Extensions

Enable markdown extensions for richer documentation:

```yaml
markdown_extensions:
  - admonition          # Create notes, warnings, etc.
  - tables              # Support for markdown tables
  - attr_list          # Element attributes
  - md_in_html         # Markdown inside HTML blocks
  - pymdownx.details    # Collapsible sections
  - pymdownx.superfences  # Code fence enhancements
  - pymdownx.highlight  # Syntax highlighting
  - toc:
      permalink: true   # Permanent links to headings
```

### Step 9: Build the Static Website

Generate static HTML files for deployment:

```bash
mkdocs build
```

This creates a `site/` directory containing all HTML, CSS, and JavaScript files ready for hosting.

### Step 10: Deploy to GitHub Pages

Deploy your documentation website to GitHub Pages:

```bash
mkdocs gh-deploy
```

!!! note "Prerequisites for Deployment"
    - Project must be in a Git repository
    - Must have GitHub account and repository
    - Requires write access to repository settings

**Alternative Deployment Options:**
- Netlify
- Vercel
- Local server
- Traditional web hosting




## Key Takeaways

### Conceptual Understanding

**Design and making are inseparable.** Fabrication methods shape design from conception.  
**Fabrication method is a design choice.** Each paradigm influences form, material, cost, and aesthetics.  
**Iteration drives learning.** The design-to-fabrication cycle repeats to refine outcomes.  
**Documentation is design practice.** Recording work develops clarity and builds professional portfolios.

### Practical Skills

By completing this activity, you have:

1. **Set up a local development environment** for documentation
2. **Created a MkDocs project** with Material theme
3. **Configured navigation and site structure**
4. **Previewed website changes** in real-time
5. **Built and deployed** documentation online

### TakeHome Assignment

**Objective:** Create a professional documentation website via GitHub Pages that documents every activity, experiment, and fabrication project completed during this course.

**Requirements:**

- [ ] Project repository created on GitHub
- [ ] MkDocs site deployed to GitHub Pages
- [ ] Navigation structure established for all course activities
- [ ] At least 3 pages completed with content and images
- [ ] Custom Material theme styling applied
- [ ] Site is publicly accessible and documented

**Deliverable:** Submit the GitHub Pages URL to document your Fabrication course journey.

### Resources

**Documentation Tools:**
- [MkDocs Official Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)

**Git & GitHub:**
- [GitHub Pages Documentation](https://pages.github.com/)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

**Version Control Best Practices:**
- Create meaningful commit messages
- Document all design iterations
- Back up frequently
- Share progress with team members




