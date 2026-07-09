# Project III — Initial Stellar Population Classification

## Scientific Question

Which broad Galactic stellar populations are suggested by the current Gaia-LAMOST candidate sample?

## Background and Motivation

This report begins **Project III — Stellar Population Analysis** in the research program *Galactic Archaeology with Gaia DR3 & LAMOST DR9*.

Project II established angular-momentum diagnostics, baseline `galpy` orbit integration, and an internal consistency analysis between angular-momentum labels and orbit-derived quantities. Project III uses this evidence to assign first-pass population interpretation labels.

This is an initial population classification, not a final claim of membership in specific known structures.

## Data and Methods

Input file:

- `data/processed/project_ii_orbit_angular_momentum_consistency.csv`

Output files:

- `data/processed/project_iii_population_candidates.csv`
- `data/processed/project_iii_population_summary.csv`

Figures:

- `figures/project_iii_population_counts.png`
- `figures/project_iii_population_feh_eccentricity.png`
- `figures/project_iii_population_lz_zmax.png`

The classification uses:

- Orbital-family interpretation labels from Project II
- Orbit-angular-momentum consistency labels
- galpy eccentricity
- galpy pericenter
- galpy apocenter
- galpy Zmax
- Lz, Lperp, and Ltotal
- [Fe/H]
- Retrograde and metal-poor flags
- Distance provenance and quality flags

The labels are heuristic population-level interpretation tags.

## Results

Total candidates:

- 27

Broad population-group counts:

- Halo-like candidates: 21
- Radial halo or GSE-like candidates: 4
- Retrograde halo candidates: 15
- Retrograde uncertain candidates: 3
- High-inclination halo candidates: 1
- Prograde hot or heated-disk candidates: 3
- Disk-like candidates: 0

## Population-Group Counts

| project_iii_population_group   |   n |
|:-------------------------------|----:|
| retrograde_halo                |  15 |
| radial_halo_or_gse_like        |   4 |
| prograde_hot_or_heated_disk    |   3 |
| retrograde_uncertain           |   3 |
| high_inclination_halo          |   1 |
| general_halo                   |   1 |

## Population-Label Counts

| project_iii_population_label               |   n |
|:-------------------------------------------|----:|
| retrograde_halo_candidate                  |  13 |
| radial_halo_gse_like_candidate             |   4 |
| prograde_hot_halo_or_heated_disk_candidate |   3 |
| retrograde_uncertain_candidate             |   3 |
| retrograde_high_inclination_halo_candidate |   2 |
| high_inclination_halo_candidate            |   1 |
| radial_halo_candidate                      |   1 |

## Confidence Counts

| project_iii_population_confidence   |   n |
|:------------------------------------|----:|
| moderate                            |  24 |
| limited                             |   3 |

## Population Summary

| project_iii_population_group   | project_iii_population_label               |   n |   feh_median |   feh_min |   feh_max |   ecc_median |   zmax_median_kpc |   rperi_median_kpc |   rap_median_kpc |   Lz_median |   Lperp_median |
|:-------------------------------|:-------------------------------------------|----:|-------------:|----------:|----------:|-------------:|------------------:|-------------------:|-----------------:|------------:|---------------:|
| retrograde_halo                | retrograde_halo_candidate                  |  13 |       -0.833 |    -1.369 |    -0.543 |     0.757349 |           3.94563 |           2.23268  |         12.6794  |    -845.864 |        587.109 |
| radial_halo_or_gse_like        | radial_halo_gse_like_candidate             |   4 |       -1.425 |    -2.108 |    -1.107 |     0.89319  |           1.58202 |           0.925364 |         12.8341  |     310.228 |        200.292 |
| prograde_hot_or_heated_disk    | prograde_hot_halo_or_heated_disk_candidate |   3 |       -1.679 |    -1.723 |    -1.116 |     0.842909 |           4.00862 |           1.63164  |         19.4812  |     770.758 |        385.255 |
| retrograde_uncertain           | retrograde_uncertain_candidate             |   3 |       -0.768 |    -0.915 |    -0.684 |     0.523503 |           1.90875 |           2.99677  |          9.85267 |   -1067.86  |        513.104 |
| retrograde_halo                | retrograde_high_inclination_halo_candidate |   2 |       -1.398 |    -2.213 |    -0.583 |     0.755084 |          31.4606  |           5.46876  |         34.5655  |    -705.966 |       2309.42  |
| general_halo                   | radial_halo_candidate                      |   1 |       -0.534 |    -0.534 |    -0.534 |     0.947761 |           5.48566 |           0.373048 |         13.9094  |     110.095 |        407.421 |
| high_inclination_halo          | high_inclination_halo_candidate            |   1 |       -1.472 |    -1.472 |    -1.472 |     0.667406 |          18.9889  |           7.54505  |         37.8259  |    2417.3   |       1650.51  |

## Interpretation

The initial Project III classification suggests that the candidate sample is dominated by halo-like and dynamically hot populations.

The radial halo or GSE-like candidates are characterized by low-Lz or radial angular-momentum behavior, high eccentricity, and generally metal-poor chemistry. These stars are important candidates for later comparison with Gaia-Sausage-Enceladus-like debris, but this report does not yet claim firm membership in that structure.

The retrograde halo candidates show negative or retrograde angular-momentum behavior combined with halo-like orbit diagnostics. These candidates may be relevant for later comparison with retrograde accretion debris such as Sequoia-like structures, but literature-region comparison is still required.

The retrograde uncertain candidates show retrograde angular-momentum behavior but less extreme orbit-integrated diagnostics. They are retained as a separate group rather than treated as ordinary disk-like stars.

The high-inclination halo candidates show large vertical orbital excursions, often reflected in high Zmax and high Lperp behavior. These are important for later action-space and orbital-family analysis.

The prograde hot or heated-disk candidates are prograde but dynamically hot, metal-poor, or vertically extended. These stars may represent heated disk, splash-like, or inner-halo populations. They should not be interpreted as ordinary thin-disk stars without further validation.

The current classification does not identify a strong disk-confined component. This is consistent with the Project II baseline orbit results, where no candidate was classified as disk-confined by the current orbit proxy.

## Validation and Uncertainty

This classification is exploratory and heuristic.

Current limitations:

- No Monte Carlo uncertainty propagation has been applied.
- The population labels do not yet use literature-defined boundaries for Gaia-Sausage-Enceladus, Helmi Stream, Sequoia, Nyx, or Splash.
- The `galpy` orbit integration uses a single baseline Galactic potential.
- Distance, astrometric, and radial-velocity uncertainties are not yet propagated.
- Population labels are broad interpretation tags, not final membership assignments.

## Deliverables

This step produces:

- Candidate-level Project III population classification table
- Population summary table
- Population-count diagnostic figure
- Metallicity-eccentricity diagnostic figure
- Lz-Zmax diagnostic figure
- Initial Project III classification report

## Next Steps

The next Project III tasks are:

1. Add literature-informed comparison regions for known merger remnants.
2. Separate broad halo-like candidates into more specific comparison groups.
3. Compare population labels with chemical-abundance information when available.
4. Prepare Project IV chemical-evolution inputs.
5. Move uncertainty propagation and classification confidence tests into Project VI.
