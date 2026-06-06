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

### Milestone summary

LAMOST DR9 stellar parameters were integrated with Gaia DR3 astrometry and photometry through Gaia source IDs. A validated Gaia–LAMOST cross-matched sample was produced, and first chemo-photometric validation figures were generated.

### Current status

Milestone 2 core workflow is now working on a small LAMOST test sample.

Next steps:

- scale the workflow to a larger LAMOST field
- improve duplicate-handling for repeated LAMOST observations
- compute tangential velocity from Gaia proper motion and distance
- combine radial velocity and tangential information for kinematic analysis
- prepare for Milestone 3: chemo-kinematic feature construction

## Milestone 3: Chemo-kinematic Feature Construction

Completed the first chemo-kinematic feature construction workflow using the Gaia–LAMOST crossmatched pilot sample.

This milestone transforms the Gaia–LAMOST merged catalogue from a crossmatched data table into a first chemo-kinematic feature table that can be used for later Galactic archaeology workflow validation.

The current result should be interpreted as:

```text
workflow validation
pilot sample analysis
small-field demonstration
```

It should not be interpreted as a final Galactic archaeology result.

### Input data

Input file:

```text
data/processed/gaia_lamost_crossmatched_sample.csv
```

Input sample size:

```text
138 stars × 29 columns
```

The input table contains Gaia astrometry and photometry together with LAMOST stellar parameters and radial velocities.

Important input columns include:

```text
source_id
ra_gaia
dec_gaia
parallax
parallax_over_error
pmra
pmdec
phot_g_mean_mag
bp_rp
ruwe
distance_pc
absolute_g_mag
teff
logg
feh
rv
snrg
id_match_sep_arcsec
```

### Output data

Output feature table:

```text
data/processed/gaia_lamost_chemo_kinematic_features.csv
```

Output sample size:

```text
138 stars × 36 columns
```

The output table preserves the original Gaia–LAMOST crossmatched fields and adds newly constructed chemo-kinematic features.

### Constructed kinematic features

New kinematic features:

```text
pm_total
tangential_velocity_kms
reduced_pm_g
```

Definitions:

```text
pm_total = sqrt(pmra^2 + pmdec^2)
```

where `pmra` and `pmdec` are in mas/yr.

```text
tangential_velocity_kms = 4.74047 * pm_total / parallax
```

where:

```text
pm_total: mas/yr
parallax: mas
tangential_velocity_kms: km/s
```

Reduced proper motion in Gaia G band:

```text
H_G = G + 5 * log10(pm_total_arcsec_per_year) + 5
```

where:

```text
pm_total_arcsec_per_year = pm_total / 1000
```

The reduced proper motion is used here as a kinematic proxy for workflow validation.

### Kinematic feature statistics

Basic summary of constructed kinematic features:

```text
pm_total:
mean ≈ 13.84 mas/yr
max  ≈ 53.62 mas/yr

tangential_velocity_kms:
mean ≈ 35.37 km/s
max  ≈ 131.66 km/s

reduced_pm_g:
mean ≈ 8.13
max  ≈ 11.37
```

No missing values were found in the required kinematic feature columns.

### Constructed chemical grouping

A simple metallicity grouping was constructed from LAMOST `[Fe/H]`.

Metallicity group definition:

```text
metal_poor:   [Fe/H] < -0.5
solar_like:  -0.5 <= [Fe/H] <= 0.2
metal_rich:   [Fe/H] > 0.2
```

New chemical grouping column:

```text
metallicity_group
```

Metallicity group counts:

```text
solar_like    114
metal_rich     21
metal_poor      3
```

These groups are used only for pilot-sample workflow validation.

### Candidate selection flags

Constructed candidate flag columns:

```text
high_vtan_candidate
metal_poor_candidate
chemo_kinematic_candidate
```

Definitions:

```text
high_vtan_candidate:
tangential_velocity_kms > 100

metal_poor_candidate:
feh < -0.5

chemo_kinematic_candidate:
tangential_velocity_kms > 100 and feh < -0.5
```

Candidate flag counts:

```text
high_vtan_candidate           1
metal_poor_candidate          3
chemo_kinematic_candidate     0
```

These flags are not final population classifications. They are simple candidate-selection indicators used to validate the chemo-kinematic workflow.

### Validation plots

Generated Milestone 3 validation plots:

```text
figures/gaia_lamost_vtan_distribution.png
figures/gaia_lamost_vtan_vs_feh.png
figures/gaia_lamost_cmd_colored_by_vtan.png
figures/gaia_lamost_reduced_pm_diagram.png
```

Plot purposes:

```text
gaia_lamost_vtan_distribution.png
```

Checks the tangential velocity distribution and identifies whether any high-velocity outliers are present.

```text
gaia_lamost_vtan_vs_feh.png
```

Provides a first comparison between tangential velocity and metallicity.

```text
gaia_lamost_cmd_colored_by_vtan.png
```

Shows where stars with different tangential velocities are located on the Gaia color-magnitude diagram.

```text
gaia_lamost_reduced_pm_diagram.png
```

Uses reduced proper motion as a kinematic proxy and visualizes the sample by metallicity group.

### Notebook

Created notebook:

```text
notebooks/03_chemo_kinematic_features.ipynb
```

The notebook performs the following workflow:

```text
1. Load Gaia–LAMOST crossmatched sample
2. Verify required columns
3. Construct pm_total
4. Construct tangential_velocity_kms
5. Construct reduced_pm_g
6. Construct metallicity_group
7. Construct candidate selection flags
8. Generate validation plots
9. Save chemo-kinematic feature table
```

### Interpretation

The current sample contains only:

```text
138 stars
```

Therefore, Milestone 3 should be interpreted as a small pilot-sample demonstration.

The main achievement is not a scientific discovery, but a validated workflow showing that:

```text
Gaia astrometry + Gaia photometry + LAMOST spectroscopy
```

can be merged and transformed into:

```text
a chemo-kinematic feature table
```

This prepares the project for later expansion to a larger Gaia–LAMOST sample and for future population-separation methods such as clustering or dimensionality reduction.

### Next milestone direction

The next stage can expand this workflow toward:

```text
larger Gaia–LAMOST samples
more complete kinematic features
UVW velocity construction
Galactocentric coordinate transformation
UMAP / HDBSCAN clustering
thin disk / thick disk / halo candidate exploration
```
