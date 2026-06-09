# Gaia–LAMOST Galactic Archaeology Project

**Machine Learning Assisted Chemo-Dynamical Analysis of Milky Way Stellar Populations Using Gaia DR3 and LAMOST**

This repository contains Project 1 of a broader Gaia–LAMOST Galactic Archaeology research portfolio. The goal of Project 1 is to build a reproducible proof-of-concept pipeline that combines Gaia DR3 astrometry and photometry with LAMOST spectroscopic stellar parameters, then uses chemo-kinematic features to explore Milky Way stellar populations.

This project is intended as a research portfolio project for computational astrophysics, data-driven astronomy, and scientific computing.

## Project Overview

Galactic archaeology studies the formation history of the Milky Way by analyzing the spatial, kinematic, and chemical properties of stars. Gaia provides precise astrometry and photometry, while LAMOST provides large-scale spectroscopic stellar parameters such as radial velocity, effective temperature, surface gravity, and metallicity.

Project 1 builds a compact but complete workflow:

1. Query and validate a Gaia DR3 stellar sample.
2. Explore LAMOST DR9 low-resolution catalogues.
3. Cross-match Gaia and LAMOST sources.
4. Construct chemo-kinematic features.
5. Prepare a larger Gaia–LAMOST sample for candidate exploration.
6. Validate candidate stars using velocity, metallicity, and CMD diagnostics.
7. Write a scientific interpretation draft and final report.
8. Polish the repository into a public-facing research showcase.

## Research Question

Can a lightweight Gaia–LAMOST pipeline recover interpretable chemo-kinematic structure in a local Milky Way stellar sample, and can it produce candidate stars or candidate groups suitable for future large-scale Galactic archaeology analysis?

## Data Sources

- **Gaia DR3**: astrometry, photometry, parallax, proper motion, and source-level stellar information.
- **LAMOST DR9 LRS**: low-resolution spectroscopic stellar parameters, including radial velocity, effective temperature, surface gravity, and metallicity.

## Scientific Motivation

The Milky Way contains multiple stellar populations that preserve information about its formation history. Stars from the Galactic disk, halo, and possible accreted components can differ in their spatial distribution, kinematics, and chemical properties.

By combining Gaia DR3 astrometry and photometry with LAMOST DR9 spectroscopy, this project explores how chemo-dynamical features can be used to identify candidate stellar populations and possible halo-like or dynamically distinct stars.

## Project 1 Status

Project 1 is complete and polished for presentation.

| Milestone | Focus | Status |
|---|---|---|
| M1 | Gaia DR3 query and validation | Completed |
| M2 | LAMOST catalogue exploration and Gaia–LAMOST cross-match | Completed |
| M3 | Chemo-kinematic feature construction | Completed |
| M4 | Larger Gaia–LAMOST sample preparation | Completed |
| M5 | Velocity and candidate diagnostics | Completed |
| M6 | Candidate-level validation | Completed |
| M7 | Scientific interpretation draft | Completed |
| Final Packaging | Repository-level organization and final report draft | Completed |
| Final Polish | README, documentation, and presentation refinement | Completed |

This repository is currently kept in a flat project structure. Directory restructuring into separate `project1/`, `project2/`, and `project3/` folders is intentionally postponed until the later multi-project stage.

## Repository Structure

    data/
      raw/              Raw or downloaded catalogue files
      processed/        Processed Gaia–LAMOST samples and derived feature tables
      external/         External reference files, if needed

    docs/
      dev_log.md        Development log and milestone notes
      milestones.md     Milestone tracking
      research_plan.md  Research planning notes

    figures/
      *.png             Scientific visualizations and diagnostic plots

    notebooks/
      01_gaia_dr3_query.ipynb
      02_lamost_catalogue_exploration.ipynb
      03_chemo_kinematic_features.ipynb
      04_larger_sample_kinematic_preparation.ipynb
      05_galactic_velocity_candidate_validation.ipynb
      06_candidate_level_diagnostics.ipynb

    report/
      project1_milestone7_scientific_interpretation_draft.md
      project1_final_report_draft.md

    src/
      Reserved for reusable source code modules in later stages

## Main Outputs

Key generated outputs include:

- Gaia DR3 nearby stellar sample.
- Gaia–LAMOST cross-matched sample.
- Chemo-kinematic feature tables.
- Larger Gaia–LAMOST candidate sample.
- Diagnostic figures, including CMDs, metallicity distributions, reduced proper motion diagrams, tangential velocity plots, radial velocity diagnostics, and Galactocentric velocity visualizations.
- Candidate-level diagnostic visualizations.
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

Exploratory clustering, physically motivated thresholds, and diagnostic visualizations were used to identify possible chemo-kinematic outliers. Candidate stars were assessed using color–magnitude structure, metallicity distribution, tangential velocity, radial velocity, and Galactocentric velocity diagnostics.

## Scientific Interpretation

Project 1 does not claim a definitive discovery of new stellar substructure. Instead, it demonstrates a reproducible analysis pipeline for selecting and interpreting candidate stars with unusual chemo-kinematic properties.

The current candidate selection should be interpreted as exploratory. The results are useful for identifying objects and regions of parameter space that may deserve deeper analysis in later projects.

The most important outcome is not a discovery claim, but a reproducible framework that can be scaled to larger Gaia–LAMOST samples in Project 2 and extended with more rigorous population modelling in Project 3.

## Limitations

Current limitations include:

- limited sample size after Gaia–LAMOST matching
- simplified candidate selection thresholds
- exploratory rather than fully statistical population classification
- selection effects from Gaia and LAMOST are not fully modelled
- no full orbital integration yet
- no robust comparison against known merger debris catalogues yet

These limitations motivate the next stages of the larger Gaia–LAMOST Galactic Archaeology project.

## Planned Next Stages

Future work will extend this repository into a broader multi-project research sequence:

- **Project 2**: Machine-learning assisted stellar population clustering.
- **Project 3**: Orbital characterization and literature-level comparison with known Galactic substructures.

The eventual goal is to build a stronger research portfolio project that connects astronomical catalogue analysis, machine learning, and Galactic archaeology.

## Tools and Libraries

Core Python tools used in this project include:

- `astroquery`
- `astropy`
- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`

See `requirements.txt` for the current environment specification.

## Author

**Lior Linho**

Independent astronomy and scientific computing project

Focus: Astrophysics, Data Science, Scientific Computing
