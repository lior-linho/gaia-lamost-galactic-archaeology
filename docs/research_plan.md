# Research Plan

## Umbrella Direction

This repository is an umbrella research-oriented project on **data-driven Galactic archaeology** using Gaia DR3 and LAMOST.

The project is not designed as a single isolated notebook. Instead, it is organized as a connected research line with three sub-projects, moving from data construction to exploratory discovery and then to interpretable candidate selection.

The current focus is to build a reproducible scientific workflow for combining large-scale astronomical survey data, constructing physically meaningful features, and exploring stellar population structures.

## Research Line

### Project I: Gaia–LAMOST Cross-matching and Chemo-kinematic Feature Construction

**Goal:**  
Build a clean Gaia–LAMOST cross-matched sample and construct physically meaningful features for later stellar population analysis.

**Main questions:**

- How can Gaia DR3 astrometry and LAMOST spectroscopy be combined into a clean analysis-ready sample?
- What quality checks are needed for cross-matched sources?
- Which astrometric, kinematic, chemical, and stellar-parameter features are useful for downstream analysis?

**Expected outputs:**

- Gaia DR3 sample validation
- LAMOST catalogue exploration
- Gaia–LAMOST cross-matched sample
- Chemo-kinematic feature table
- Basic validation figures

---

### Project II: Unsupervised Stellar Population Discovery

**Goal:**  
Use visualization, dimensionality reduction, and clustering methods to explore possible stellar population structures in the Gaia–LAMOST feature space.

**Main questions:**

- Can exploratory visualization reveal separations between different stellar populations?
- How do metallicity, motion, and stellar parameters relate to disk-like or halo-like populations?
- Can unsupervised learning methods reveal meaningful structures without predefined labels?

**Expected outputs:**

- Color-magnitude and chemo-kinematic visualizations
- Feature-space projections
- Clustering experiments
- Initial interpretation of possible stellar population groups

---

### Project III: Interpretable Machine Learning for Galactic Substructure Candidates

**Goal:**  
Develop interpretable machine learning workflows for identifying and analyzing candidate Galactic substructures.

**Main questions:**

- Can candidate stellar groups be selected using interpretable feature-based models?
- Which features contribute most strongly to possible population separation?
- How can machine learning outputs be connected back to astrophysical interpretation?

**Expected outputs:**

- Candidate selection workflow
- Interpretable model experiments
- Feature importance or explanation analysis
- Research-style discussion of limitations and future work

---

## Planned Milestones

### Milestone 1: Gaia DR3 Query and Validation

Query Gaia DR3 stellar samples and validate the basic astrometric and photometric fields.

### Milestone 2: LAMOST Catalogue Exploration and Cross-match

Explore LAMOST spectroscopic fields and cross-match LAMOST sources with Gaia DR3 sources.

### Milestone 3: Chemo-kinematic Feature Construction

Construct distance, velocity, metallicity, and stellar-parameter features for later analysis.

### Milestone 4: Exploratory Visualization

Visualize the sample using color-magnitude diagrams, distance distributions, velocity features, and metallicity trends.

### Milestone 5: Machine Learning Exploration

Apply exploratory methods such as dimensionality reduction and clustering to search for stellar population structures.

### Milestone 6: Research-style Report

Summarize the data, methods, figures, limitations, and possible interpretations in a research-style report.

## Expected Outcome

The expected outcome is a reproducible undergraduate-level research portfolio project with clean documentation, visual outputs, reusable code, and a written report.

The project is designed as a foundation for future research opportunities in physics, astronomy, scientific computing, or data-driven science.
