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

## Milestone 4 Checkpoint: Gaia Larger Sample Preparation

Milestone 4 has started with a larger Gaia-side sample preparation workflow.

Completed in this checkpoint:

- Created `notebooks/04_larger_sample_kinematic_preparation.ipynb`
- Defined a larger Milestone 4 sky region:
  - RA: 120–130 deg
  - DEC: -5 to 5 deg
- Prepared reusable LAMOST column-standardization and reading functions
- Confirmed that `data/raw/lamost_dr9_larger_sample.csv` is not yet available locally
- Queried Gaia DR3 for the larger sky region
- Saved Gaia larger raw sample locally:
  - `data/raw/gaia_dr3_larger_lamost_region_sample.csv`
  - Shape: 50000 stars × 10 columns
- Constructed basic Gaia features:
  - `distance_pc`
  - `absolute_g_mag`
- Saved Gaia larger processed feature table locally:
  - `data/processed/gaia_dr3_larger_lamost_region_with_features.csv`
  - Shape: 50000 stars × 12 columns
- Generated Gaia larger validation figures:
  - `figures/gaia_lamost_larger_sky_distribution.png`
  - `figures/gaia_lamost_larger_cmd.png`
  - `figures/gaia_lamost_larger_distance_distribution.png`
  - `figures/gaia_lamost_larger_proper_motion_space.png`

Notes:

- The Gaia query used `SELECT TOP 50000`, and the result reached this limit.
- Therefore, the current Gaia larger sample should be interpreted as a truncated larger-region workflow sample rather than a complete spatially uniform Gaia DR3 sample.
- The larger LAMOST sample still needs to be obtained before Gaia–LAMOST source_id cross-match can be performed.

Next steps:

- Obtain or import `data/raw/lamost_dr9_larger_sample.csv`
- Standardize the larger LAMOST sample
- Perform Gaia–LAMOST source_id cross-match
- Validate coordinate separation
- Construct larger-sample chemo-kinematic features
- Prepare Galactic coordinates and UVW input fields

## Milestone 4 Completed: Larger Gaia-LAMOST Feature Preparation

Milestone 4 has been completed.

This milestone expanded the project from the Milestone 3 pilot Gaia–LAMOST sample to a larger matched stellar sample suitable for later chemo-kinematic analysis.

Completed work:

- Created and completed `notebooks/04_larger_sample_kinematic_preparation.ipynb`
- Downloaded and imported a larger LAMOST DR9 AFGK sample
- Queried Gaia DR3 for the corresponding LAMOST sky region
- Performed coordinate-based Gaia–LAMOST cross-match
- Adopted a conservative `1.0 arcsec` matching radius
- Built an observation-level matched table
- Detected and handled duplicate Gaia `source_id` entries
- Created a deduplicated star-level larger feature table
- Constructed larger-sample chemo-kinematic features
- Added Galactic coordinates:
  - `gal_l`
  - `gal_b`
- Checked UVW input-field completeness
- Generated final validation figures

Input samples:

```text
LAMOST larger sample:
2979 rows × 16 columns

Gaia LAMOST-region sample:
36531 stars × 12 columns
```

Cross-match result:

```text
Observation-level matched sample:
2487 rows × 29 columns

Deduplicated star-level sample:
1838 unique Gaia sources
```

Final feature table:

```text
data/processed/gaia_lamost_larger_chemo_kinematic_features.csv
Shape: 1838 stars × 38 columns
```

Constructed features:

```text
pm_total
tangential_velocity_kms
reduced_pm_g
metallicity_group
high_vtan_candidate
metal_poor_candidate
chemo_kinematic_candidate
gal_l
gal_b
```

Final candidate counts:

```text
high_vtan_candidate:          38
metal_poor_candidate:        148
chemo_kinematic_candidate:    27
```

Final validation figures:

```text
figures/gaia_lamost_larger_vtan_distribution.png
figures/gaia_lamost_larger_vtan_vs_feh.png
figures/gaia_lamost_larger_cmd_colored_by_vtan.png
figures/gaia_lamost_larger_reduced_pm_diagram.png
figures/gaia_lamost_larger_galactic_lb_distribution.png
```

Key result:

```text
The larger Gaia–LAMOST workflow successfully identified a non-empty set of metal-poor high-tangential-velocity candidates.
```

This demonstrates that the pilot chemo-kinematic workflow can scale to a larger matched stellar sample.

Next milestone direction:

- Validate candidate properties in more detail
- Add formal Galactic velocity calculations
- Explore UMAP / HDBSCAN clustering
- Compare candidates with known Milky Way stellar populations
- Prepare report-ready figures and write-up

## Milestone 5: Formal Galactic Velocity Construction and Candidate Validation

Completed Milestone 5 by extending the larger Gaia–LAMOST chemo-kinematic feature table with formal Galactocentric velocity diagnostics.

Main work completed:

- Created `notebooks/05_galactic_velocity_candidate_validation.ipynb`
- Loaded the Milestone 4 larger feature table with 1838 stars and 38 columns
- Validated required astrometric and radial-velocity input fields
- Constructed 6D `SkyCoord` objects using Gaia astrometry and LAMOST radial velocities
- Recomputed Galactic coordinates with `astropy` and confirmed consistency with Milestone 4 `gal_l` and `gal_b`
- Recorded the default `astropy` Galactocentric frame assumptions
- Transformed the sample into the Galactocentric frame
- Extracted Galactocentric Cartesian position and velocity components
- Computed `galcen_vtot_kms`
- Saved the velocity-enhanced feature table
- Extracted and saved the chemo-kinematic candidate table
- Generated Milestone 5 validation figures

Data products:

- `data/processed/gaia_lamost_larger_velocity_features.csv`
  - 1838 stars × 47 columns
- `data/processed/gaia_lamost_larger_chemo_kinematic_candidates.csv`
  - 27 candidates × 31 columns

Validation figures:

- `figures/gaia_lamost_larger_galcen_velocity_distribution.png`
- `figures/gaia_lamost_larger_galcen_vx_vy.png`
- `figures/gaia_lamost_larger_galcen_vtot_vs_feh.png`
- `figures/gaia_lamost_larger_candidates_vtan_vs_feh.png`
- `figures/gaia_lamost_larger_candidates_cmd.png`
- `figures/gaia_lamost_larger_candidates_sky_galactic.png`
- `figures/gaia_lamost_larger_candidates_rv_distribution.png`

Interpretation:

The Milestone 4 chemo-kinematic candidate sample contains 27 metal-poor high-tangential-velocity candidates. Milestone 5 confirms that these candidates occupy useful diagnostic regions in velocity-metallicity and color-magnitude spaces.

These candidates should be interpreted as possible halo-like chemo-kinematic candidates for further validation, not as confirmed halo stars, confirmed merger debris, or confirmed Galactic substructure members.

Limitations:

- The sample covers a limited LAMOST-compatible sky region
- The LAMOST sample does not represent a full survey selection function
- Distances are based on simple parallax inversion
- Galactocentric velocities depend on the default `astropy` frame assumptions
- No orbit integration, action-space analysis, or integrals-of-motion analysis has been performed yet

## Milestone 6 — Candidate-level Diagnostic Analysis and Report Tables

Milestone 6 converts the chemo-kinematic candidate list from Milestone 5 into a candidate-level diagnostic dataset suitable for reporting, interpretation, and later scientific discussion.

### Main goals

- Construct a candidate-level diagnostic table for the Milestone 5 candidate stars.
- Add readable candidate flags based on metallicity, tangential velocity, and Galactocentric total velocity.
- Generate a compact summary table for report and README usage.
- Highlight candidate stars on the Gaia color–magnitude diagram.
- Compare candidate velocity and metallicity distributions against the larger Gaia–LAMOST sample.

### Candidate summary

- Number of candidate stars analysed: 27
- Candidate levels:
  - weak: 12
  - moderate: 9
  - strong: 6
- Candidate score distribution:
  - score 0: 4
  - score 1: 8
  - score 2: 7
  - score 3: 2
  - score 4: 3
  - score 5: 3

### Diagnostic statistics

- Median candidate [Fe/H]: -0.951
- Minimum candidate [Fe/H]: -2.213
- Maximum candidate [Fe/H]: -0.534
- Median candidate tangential velocity: 197.414 km/s
- Maximum candidate tangential velocity: 426.686 km/s
- Median candidate Galactocentric total velocity: 157.611 km/s
- Maximum candidate Galactocentric total velocity: 393.357 km/s

### Outputs

- `notebooks/06_candidate_level_diagnostics.ipynb`
- `data/processed/gaia_lamost_candidate_diagnostic_table.csv`
- `data/processed/gaia_lamost_candidate_summary_table.csv`
- `data/processed/gaia_lamost_candidate_summary_table.md`
- `figures/gaia_lamost_candidate_cmd_highlight.png`
- `figures/gaia_lamost_candidate_velocity_diagnostics.png`
- `figures/gaia_lamost_candidate_metallicity_distribution.png`

### Notes

The candidate levels introduced in this milestone are diagnostic prioritization labels rather than final astrophysical classifications. They are based on simple chemo-kinematic criteria, mainly metallicity, tangential velocity, and Galactocentric total velocity. These labels help identify stars that may be worth closer inspection in later interpretation, visualization, and comparison with known Galactic components such as the disk, stellar halo, and possible accreted structures.
## Project 1 Milestone 7: Scientific Interpretation Draft

- Added a first scientific interpretation draft for the Project 1 Gaia–LAMOST exploratory analysis.
- Interpreted the CMD, metallicity structure, velocity-space behavior, candidate stars, and clustering outputs in conservative scientific language.
- Clarified that current candidate stars should be treated as preliminary chemo-kinematic candidates rather than confirmed accreted-halo or merger-debris members.
- Documented key limitations, including sample size, survey-selection effects, measurement uncertainties, cross-match reliability, and the absence of full orbital analysis.
- Added a transition section explaining how Project 1 motivates a larger and more robust Project 2 analysis.


## Project 1 Final Packaging - README and Final Report Draft

Project 1 has entered the final packaging stage.

Completed in this stage:
- Rewrote the repository README into a public-facing project showcase version.
- Added a Project 1 final report draft under `report/`.
- Clarified the project scope as a proof-of-concept Gaia–LAMOST Galactic archaeology pipeline.
- Summarized the completed milestones from Gaia DR3 querying to scientific interpretation.
- Added limitations and future-work sections to avoid overstating discovery claims.

Scientific positioning:
- The current Project 1 output is not presented as a definitive stellar-population discovery.
- The main value is a reproducible, interpretable pipeline combining Gaia astrometry/photometry and LAMOST spectroscopy.
- The project is now suitable for GitHub presentation, RA outreach, and later expansion into Project 2.


## Project 1 Final Polish

Project 1 final polish was completed after the final packaging stage.

This stage focused on improving the repository-level presentation rather than changing the scientific analysis or restructuring the directory layout. The main README was updated to clearly describe the research motivation, Gaia–LAMOST data combination, Project 1 workflow, main outputs, scientific interpretation, current limitations, and planned next stages.

The repository remains intentionally flat at this stage. A future restructuring into separate project folders will be considered only after Project 2 and Project 3 are developed.

Final polish scope:

- refined the top-level README for external readers
- clarified that Project 1 is complete
- emphasized the exploratory nature of the current candidate selection
- documented current limitations and future directions
- kept notebooks, figures, data products, and directory layout unchanged

Project 1 is now in a presentable portfolio state for research outreach, RA applications, and later multi-project expansion.

## Project 2 Milestone 1: Research Design and Feature-Space Definition

Project 2 was started after Project 1 final packaging and final polish were completed.

The goal of Project 2 is to move from candidate-level exploratory diagnostics toward machine-learning assisted stellar population clustering. The primary input table selected for Project 2 is:

- `data/processed/gaia_lamost_larger_velocity_features.csv`

This table contains the larger Gaia–LAMOST feature set with astrometric, photometric, spectroscopic, Galactic coordinate, and Galactocentric velocity quantities.

Project 2 research question:

Can unsupervised machine learning recover interpretable stellar population structure from Gaia–LAMOST chemo-kinematic features?

Initial Project 2 design:

- use the larger Gaia–LAMOST velocity-feature table as the baseline dataset
- define multiple feature spaces for clustering experiments
- separate physical diagnostic flags from machine-learning input features
- compare clustering behaviour across photometric, chemical, kinematic, and combined feature spaces
- avoid treating exploratory clusters as confirmed astrophysical substructures
- use candidate flags from Project 1 as post-hoc interpretation labels rather than training labels

Planned feature-space groups:

1. Photometric and astrometric space:
   - `bp_rp`
   - `absolute_g_mag`
   - `distance_pc`
   - `pm_total`
   - `reduced_pm_g`

2. Chemical and stellar-parameter space:
   - `feh`
   - `teff`
   - `logg`

3. Local kinematic space:
   - `tangential_velocity_kms`
   - `rv`

4. Galactocentric velocity space:
   - `galcen_vx_kms`
   - `galcen_vy_kms`
   - `galcen_vz_kms`
   - `galcen_vtot_kms`

5. Combined chemo-kinematic space:
   - `feh`
   - `bp_rp`
   - `absolute_g_mag`
   - `tangential_velocity_kms`
   - `rv`
   - `galcen_vx_kms`
   - `galcen_vy_kms`
   - `galcen_vz_kms`
   - `galcen_vtot_kms`

Initial methods to evaluate:

- missing-value filtering
- robust feature scaling
- PCA for baseline dimensionality reduction
- UMAP for nonlinear visualization
- DBSCAN or HDBSCAN for density-based clustering
- Gaussian Mixture Models as a comparison method

Milestone 1 is limited to research design and feature-space definition. Full clustering experiments will be developed in later Project 2 milestones.
