# Galactic Archaeology with Gaia DR3 & LAMOST DR9

## A Personal Independent Research Program in Galactic Dynamics and Stellar Populations

This repository hosts a personal independent research program in Galactic archaeology, using Gaia DR3 and LAMOST DR9 to identify dynamically and chemically distinct stellar populations in the Milky Way through reproducible computational methods.

The project is designed as an open, reproducible research program rather than a one-time coursework-style analysis. It connects data foundation, Galactic dynamics, stellar-population analysis, chemical evolution, computational discovery, and scientific validation.

For the full research-program structure, see:

- `docs/research_program_charter.md`

---

## Research Goal

Use Gaia DR3 and LAMOST DR9 to identify dynamically and chemically distinct stellar populations in the Milky Way through reproducible computational methods.

---

## Research Program Structure

The full program is organized into six independent but connected research projects:

1. **Project I — Data Foundation**  
   Build the Gaia-LAMOST data foundation through data acquisition, cross-match, quality control, feature engineering, and candidate discovery.

2. **Project II — Orbital Dynamics**  
   Extend the candidate catalogue with orbit integration, angular momentum, orbital energy, action-space analysis, and orbit-family interpretation.

3. **Project III — Stellar Population Analysis**  
   Classify candidate stars into Galactic populations and compare them with disk, halo, and merger-related structures.

4. **Project IV — Chemical Evolution**  
   Use LAMOST chemical information to study metallicity, abundance patterns, and chemical tagging.

5. **Project V — Computational Discovery**  
   Apply dimensionality reduction, clustering, consensus analysis, and anomaly detection to identify robust structures in the data.

6. **Project VI — Scientific Validation**  
   Validate the results through uncertainty propagation, literature comparison, and scientific interpretation.

---

## Current Status

The repository is currently transitioning from milestone-based development into a six-part research-program structure.

Existing work maps onto the new structure as follows:

| Existing Work | New Research-Program Mapping | Status |
|---|---|---|
| Project 1: Gaia-LAMOST cross-match, quality control, feature engineering, and candidate discovery | Project I — Data Foundation | Completed initial version |
| Project 2: PCA, UMAP, DBSCAN, robustness testing, and cross-method candidate summary | Project V — Computational Discovery | Completed initial version |
| Project 3: Orbit input preparation, distance recovery, and angular-momentum diagnostics | Project II — Orbital Dynamics | In progress |

During this transition, the repository keeps its current flat structure. Large directory restructuring is intentionally postponed until the research outputs are stable.

---

## Immediate Next Step

The current focus is:

**Project II — Orbital Dynamics: Orbital-Family Interpretation**

This step uses the angular-momentum candidate table to interpret possible orbital families based on angular momentum, velocity diagnostics, metallicity, and distance provenance.

---

## Repository Structure

The repository currently keeps a flat, development-friendly structure:

    gaia-lamost-galactic-archaeology/
    ├── data/
    ├── docs/
    ├── figures/
    ├── notebooks/
    ├── report/
    ├── src/
    └── README.md

A larger research-program directory structure may be introduced later after the main scientific outputs are stable.

---

## Main Outputs So Far

### Project I — Data Foundation

Initial Gaia-LAMOST data foundation completed, including:

- Gaia DR3 sample preparation
- LAMOST DR9 cross-match
- Match-quality assessment
- Quality-control filtering
- Feature engineering
- Candidate discovery
- Candidate Catalog v1

### Project V — Computational Discovery

Initial computational-discovery layer completed, including:

- PCA feature-space analysis
- UMAP embedding analysis
- DBSCAN baseline clustering
- Small parameter-sweep robustness analysis
- Cross-method candidate evidence summary

### Project II — Orbital Dynamics

Current orbital-dynamics work includes:

- Orbit-input preparation
- Distance-recovery preparation
- Velocity-space orbital diagnostics
- Angular-momentum diagnostics
- Candidate-level orbital interpretation in progress

---

## Long-Term Deliverables

The final research program aims to produce:

- Candidate Catalog
- Orbit Catalog
- Population Catalog
- Chemical Catalog
- Computational Discovery Catalog
- Publication-quality figures
- Research-paper-style tables
- Methodology and reproducibility documentation
- A reproducible computational workflow
- A LaTeX manuscript in A&A-style or MNRAS-style format

The manuscript does not need to be submitted immediately, but the long-term goal is to reach a standard close to submission readiness.

---

## Research Standard

Each research project follows the same scientific structure:

1. Scientific Question
2. Background and Motivation
3. Data and Methods
4. Results
5. Validation and Uncertainty
6. Discussion
7. Deliverables

This shared structure ensures that the repository develops as a coherent scientific program rather than a collection of disconnected notebooks.

---

## License and Reproducibility

This repository is developed as an open personal research portfolio. Data-processing steps, notebooks, figures, and reports are documented to support reproducibility and later scientific review.
