# Gaia–LAMOST Galactic Archaeology Project

**Machine Learning Assisted Chemo-Dynamical Analysis of Milky Way Stellar Populations Using Gaia DR3 and LAMOST**

This repository contains Project 1 of a broader Gaia–LAMOST Galactic Archaeology research portfolio. The goal of Project 1 is to build a reproducible proof-of-concept pipeline that combines Gaia DR3 astrometry and photometry with LAMOST spectroscopic stellar parameters, then uses chemo-kinematic features to explore Milky Way stellar populations.

## Project Overview

Galactic archaeology studies the formation history of the Milky Way by analyzing the spatial, kinematic, and chemical properties of stars. Gaia provides precise astrometry and photometry, while LAMOST provides large-scale spectroscopic stellar parameters such as radial velocity, effective temperature, surface gravity, and metallicity.

Project 1 builds a compact but complete workflow:

1. Query and validate a Gaia DR3 stellar sample.
2. Explore LAMOST DR9 low-resolution catalogues.
3. Cross-match Gaia and LAMOST sources.
4. Construct chemo-kinematic features.
5. Explore stellar population structure through clustering and candidate selection.
6. Validate candidate groups and write a scientific interpretation draft.
7. Package the project into a public-facing research showcase.

## Research Question

Can a lightweight Gaia–LAMOST pipeline recover interpretable chemo-kinematic structure in a local Milky Way stellar sample, and can it produce candidate groups suitable for future large-scale Galactic archaeology analysis?

## Data Sources

- **Gaia DR3**: astrometry, photometry, parallax, proper motion, and source-level stellar information.
- **LAMOST DR9 LRS**: low-resolution spectroscopic stellar parameters, including radial velocity, effective temperature, surface gravity, and metallicity.

## Project 1 Status

Project 1 has completed the main technical and interpretation milestones.

| Milestone | Focus | Status |
|---|---|---|
| M1 | Gaia DR3 query and validation | Completed |
| M2 | LAMOST catalogue exploration and Gaia–LAMOST cross-match | Completed |
| M3 | Chemo-kinematic feature construction | Completed |
| M4 | Initial clustering and stellar population exploration | Completed |
| M5 | Larger-sample candidate selection and visualization | Completed |
| M6 | Candidate validation and robustness checks | Completed |
| M7 | Scientific interpretation draft | Completed |
| Final Packaging | README showcase and final report draft | In progress |

## Repository Structure

data/
  raw/              # Raw or downloaded catalogue files
  processed/        # Cross-matched samples and derived feature tables
  external/         # External reference data, if used

docs/
  dev_log.md        # Development log and milestone notes

figures/
  *.png             # Scientific visualizations

notebooks/
  01_*.ipynb        # Gaia DR3 query and validation
  02_*.ipynb        # LAMOST exploration and cross-match
  ...               # Feature construction, clustering, validation

report/
  project1_milestone7_scientific_interpretation_draft.md
  project1_final_report_draft.md

src/
  *.py              # Reusable analysis utilities

## Main Outputs

Key generated outputs include:

- Gaia DR3 nearby stellar sample.
- Gaia–LAMOST cross-matched sample.
- Chemo-kinematic feature tables.
- Candidate stellar population selections.
- Diagnostic figures, including CMDs, metallicity distributions, velocity-space visualizations, and clustering summaries.
- Scientific interpretation draft.
- Project 1 final report draft.

## Methods

### 1. Gaia DR3 sample construction

A Gaia DR3 stellar sample was queried and validated using astrometric and photometric checks. Basic distributions such as sky position, parallax, distance, and color–magnitude structure were inspected.

### 2. LAMOST catalogue exploration

LAMOST DR9 low-resolution catalogues were explored to identify spectroscopic fields useful for Galactic archaeology, including radial velocity, effective temperature, surface gravity, and metallicity.

### 3. Gaia–LAMOST cross-match

The Gaia and LAMOST samples were cross-matched using source identifiers where possible and angular-neighbour matching as a fallback. Multiple angular thresholds were tested to evaluate match quality.

### 4. Chemo-kinematic feature construction

Astrometric, photometric, and spectroscopic fields were combined into derived features suitable for stellar population analysis. The feature set includes distance-related quantities, color–magnitude information, velocity-related quantities, and chemical indicators such as metallicity.

### 5. Candidate selection and interpretation

Exploratory clustering and physically motivated cuts were used to identify possible stellar population candidates. Candidate groups were assessed using color–magnitude structure, metallicity distribution, and velocity-related feature space.

## Scientific Interpretation

The current Project 1 result should be treated as a proof-of-concept pipeline rather than a final population census. The sample is intentionally compact and designed for methodological development. The main scientific value is that the workflow demonstrates how Gaia astrometry and LAMOST spectroscopy can be combined into an interpretable chemo-kinematic analysis pipeline.

The most important outcome is not a definitive discovery claim, but a reproducible framework that can be scaled to larger Gaia–LAMOST samples in Project 2 and extended with more rigorous population modelling in Project 3.

## Limitations

- The current sample size is limited.
- Selection effects from Gaia and LAMOST are not fully modelled.
- Distance estimates use simplified assumptions.
- Candidate groups require larger-sample validation.
- The current clustering results are exploratory and should not be interpreted as confirmed stellar streams or merger remnants.

## Next Steps

Future work will focus on:

1. Scaling the pipeline to a larger Gaia–LAMOST sample.
2. Improving selection-function awareness.
3. Adding more robust Galactic coordinate and velocity transformations.
4. Comparing candidates with known Milky Way components and merger debris.
5. Preparing a polished research-style report suitable for RA applications and academic outreach.

## Project Context

This repository is part of a larger three-project research portfolio:

- **Project 1**: Gaia–LAMOST pipeline construction and local chemo-kinematic exploration.
- **Project 2**: Larger-scale stellar population mapping and clustering.
- **Project 3**: Research-level interpretation, validation, and possible paper-style synthesis.

## Author

**Lior Linho**  
Independent astronomy and scientific computing project  
Focus: Astrophysics, Data Science, Scientific Computing
