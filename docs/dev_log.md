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


## Milestone 2: LAMOST catalogue exploration and Gaia–LAMOST cross-match

Started the LAMOST data integration stage of the Gaia–LAMOST Galactic Archaeology Project.

### LAMOST sample

Used the LAMOST DR9 v2.0 low-resolution AFGKM stellar parameter catalogue.

A small test sample was downloaded from the LAMOST Low Resolution Search interface with the following approximate constraints:

- RA: 120–122 deg
- DEC: 0–2 deg
- Teff: 4500–6500 K
- logg: 3.5–5.0
- [Fe/H]&#58; -1.0 to 0.5
- snrg: > 50

The exported LAMOST CSV file was found to be pipe-separated rather than comma-separated, so it was read using:

```python
pd.read_csv(path, sep="|")
```

The cleaned LAMOST sample contains 187 rows and 27 columns.

### Gaia regional query

A Gaia DR3 regional sample was queried around the LAMOST test field and saved to:

```text
data/raw/gaia_dr3_lamost_region_sample.csv
```

Distance and absolute G magnitude were computed and saved to:

```text
data/processed/gaia_dr3_lamost_region_with_features.csv
```

### Gaia–LAMOST cross-match

The primary cross-match method used Gaia source IDs:

```text
Gaia source_id = LAMOST gaia_source_id
```

This produced a first Gaia–LAMOST cross-matched sample with:

```text
138 stars × 29 columns
```

The final sample was saved to:

```text
data/processed/gaia_lamost_crossmatched_sample.csv
```

The sample includes Gaia astrometry and photometry together with LAMOST spectroscopic parameters:

- parallax
- proper motion
- G magnitude
- BP-RP color
- distance
- absolute G magnitude
- Teff
- logg
- [Fe/H]
- radial velocity
- S/N
- Gaia–LAMOST coordinate separation

### Cross-match validation

A coordinate-separation check was performed for the source-ID matched sample.

Summary of Gaia–LAMOST coordinate separation:

```text
count: 138
mean: 0.155 arcsec
median: 0.126 arcsec
max: 0.832 arcsec
```

All source-ID matched objects have Gaia–LAMOST coordinate separations below 1 arcsec.

A coordinate-based SkyCoord nearest-neighbour match was also tested:

```text
0.5 arcsec: 120 matches
1.0 arcsec: 123 matches
2.0 arcsec: 123 matches
3.0 arcsec: 124 matches
```

This confirms that the source-ID cross-match is reliable, while coordinate matching is stable at the 1–2 arcsec level.

### Figures generated

Two Gaia–LAMOST validation figures were generated:

```text
figures/gaia_lamost_cmd_colored_by_feh.png
figures/gaia_lamost_rv_vs_feh.png
```

### Current status

Milestone 2 core workflow is now working on a small LAMOST test sample.

Next steps:

- scale the workflow to a larger LAMOST field
- improve duplicate-handling for repeated LAMOST observations
- compute tangential velocity from Gaia proper motion and distance
- combine radial velocity and tangential information for kinematic analysis
- prepare for Milestone 3: chemo-kinematic feature construction