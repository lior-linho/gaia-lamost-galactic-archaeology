# Development Log

## 2026-06-05

### Project Initialization

Initialized the Gaia–LAMOST Galactic Archaeology Project repository.

Created the initial project structure:

- data/
- notebooks/
- src/
- figures/
- report/
- docs/

Configured the Python virtual environment and installed the core scientific computing dependencies, including:

- pandas
- numpy
- matplotlib
- astropy
- astroquery
- scikit-learn
- umap-learn
- hdbscan
- jupyter

### Gaia DR3 Query Pipeline

Created the first notebook:

notebooks/01_gaia_dr3_query.ipynb

The notebook queries Gaia DR3 for a small nearby stellar sample using the following quality criteria:

- parallax > 1 mas
- parallax_over_error > 10
- valid proper motions
- valid Gaia G magnitude
- valid BP-RP color
- RUWE < 1.4

The query successfully returned 5,000 nearby stars.

### Feature Construction

Computed two basic derived features:

- distance_pc
- absolute_g_mag

The derived dataset was saved locally as:

data/processed/gaia_dr3_nearby_5000_with_features.csv

### Initial Validation Plots

Generated three validation figures:

- figures/gaia_dr3_nearby_5000_cmd.png
- figures/gaia_dr3_nearby_5000_distance_distribution.png
- figures/gaia_dr3_nearby_5000_proper_motion_space.png

The CMD shows a clear stellar main sequence, confirming that the Gaia query, distance calculation, and absolute magnitude calculation are working correctly.

The distance distribution confirms that the development sample covers the nearby 0–1000 pc range.

The proper motion diagram shows the kinematic spread of the nearby stellar sample and provides an initial basis for later high proper motion and high velocity candidate selection.

### Notes

This first 5,000-star sample is a development sample, not the final science sample.

It is used to validate the data access, feature construction, and visualization pipeline before scaling up and performing Gaia–LAMOST cross-matching.

### Git Commits

Initial project setup:

Initialize Gaia-LAMOST galactic archaeology project

Gaia query and validation notebook:

Add Gaia DR3 query and initial validation plots

### Next Steps

- Expand the Gaia sample size.
- Prepare a LAMOST catalogue download/loading notebook.
- Investigate Gaia–LAMOST cross-matching strategies.
- Build the first combined chemo-dynamical feature table.