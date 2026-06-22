# Project 3 Milestone 4 — Distance / Parallax Recovery for Angular Momentum Analysis

## Objective

Project 3 Milestone 3 identified that the readiness-aware orbital diagnostics candidate table preserved useful velocity-space diagnostics but did not yet carry explicit parallax or distance information for the 27 Project 3 candidates.

This milestone checks whether the missing distance/parallax information can be recovered from existing processed Gaia–LAMOST larger feature or candidate tables, then writes a distance-recovered candidate table for later angular-momentum analysis.

## Inputs

- Candidate table: `data/processed/project3_orbital_diagnostics_candidates.csv`
- Recovery source selected by notebook: `gaia_lamost_larger_velocity_features.csv`
- Merge key: `source_id`

## Outputs

- `notebooks/15_project3_distance_parallax_recovery.ipynb`
- `data/processed/project3_distance_recovered_candidates.csv`
- `data/processed/project3_distance_recovery_summary.csv`
- `report/project3_milestone4_distance_parallax_recovery.md`

## Recovery summary

- Number of Project 3 candidates: 27
- Candidates with recovered parallax: 0
- Candidates with positive parallax: 0
- Candidates with inverse-parallax distance estimate: 0
- Candidates passing basic angular-momentum readiness check: 0

## Distance quality flags

- missing_parallax: 27

## Notes and limitations

The recovered distance is currently an exploratory inverse-parallax estimate:

`distance_pc = 1000 / parallax_mas`

This is sufficient for Project 3 readiness and pipeline preparation, but it should not be treated as a final publication-grade distance model. Later orbit and angular-momentum analysis should document the adopted Galactic frame, solar parameters, parallax zero-point handling, and whether an external distance catalog or Bayesian distance estimate is used.

## Next step

Project 3 Milestone 5 can use `project3_distance_recovered_candidates.csv` to compute angular-momentum diagnostics such as `Lz`, `Lperp`, and `Ltot`, provided the recovered rows include sky position, proper motions, radial velocity, and a usable distance proxy.
