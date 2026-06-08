# Gaia–LAMOST Galactic Archaeology Project

Research-oriented project exploring Milky Way stellar populations using **Gaia DR3** astrometry and **LAMOST** spectroscopy.

## Overview

This project combines astrometric, photometric, kinematic, and spectroscopic information from large-scale astronomical surveys to study the chemo-dynamical structure of Milky Way stellar populations.

The current goal is to build a clean Gaia–LAMOST cross-matched sample, construct physically meaningful features, and prepare the dataset for exploratory visualization and machine learning analysis.

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
