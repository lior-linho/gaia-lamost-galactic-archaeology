# Data-driven Galactic Archaeology with Gaia DR3 and LAMOST

This repository is an umbrella research-oriented project exploring Milky Way stellar populations using **Gaia DR3** astrometry and **LAMOST** spectroscopy.

The project is organized into three connected sub-projects:

1. **Gaia–LAMOST Cross-matching and Chemo-kinematic Feature Construction**  
   Building a clean Gaia–LAMOST cross-matched sample and constructing physically meaningful astrometric, kinematic, chemical, and stellar-parameter features.

2. **Unsupervised Stellar Population Discovery**  
   Applying exploratory visualization, dimensionality reduction, and clustering methods to search for possible stellar population structures.

3. **Interpretable Machine Learning for Galactic Substructure Candidates**  
   Developing interpretable models and selection workflows for identifying and analyzing candidate Galactic substructures.

## Overview

This project combines astrometric, photometric, kinematic, and spectroscopic information from large-scale astronomical surveys to study the chemo-dynamical structure of Milky Way stellar populations.

The current stage focuses on **Project I**, including Gaia DR3 sample validation, LAMOST catalogue exploration, cross-matching, and chemo-kinematic feature construction.

## Data

- **Gaia DR3**: positions, parallaxes, proper motions, photometry
- **LAMOST DR9**: stellar parameters, radial velocities, metallicity estimates
- **Cross-matched sample**: Gaia sources matched with LAMOST spectroscopic entries

## Current Progress

- [x] Gaia DR3 sample query and validation
- [x] LAMOST catalogue exploration
- [x] Gaia–LAMOST cross-match
- [ ] Chemo-kinematic feature construction
- [ ] Exploratory visualization
- [ ] Clustering and stellar population analysis
- [ ] Research-style project report

## Methodology

1. Query and validate Gaia DR3 stellar samples
2. Explore LAMOST spectroscopic catalogue fields
3. Cross-match Gaia and LAMOST sources
4. Construct distance, velocity, metallicity, and stellar-parameter features
5. Visualize stellar populations in physical and feature spaces
6. Apply exploratory machine learning methods
7. Interpret possible population structures

## Repository Structure

    data/        Raw and processed datasets
    docs/        Development logs and milestone notes
    figures/     Generated plots and visual outputs
    notebooks/   Jupyter notebooks for exploration and analysis
    src/         Reusable Python modules
    report/      Research-style writeups

## Technical Stack

Python · NumPy · Pandas · Matplotlib · Astropy · Scikit-learn · Jupyter · ADQL · Git

## Status

This is an independent research-oriented undergraduate portfolio project. The project is under active development.

## Acknowledgements

This project uses publicly available data from the Gaia mission and LAMOST survey.
