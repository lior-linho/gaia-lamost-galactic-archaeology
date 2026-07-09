# Project VI — Validation Roadmap and Uncertainty Inventory

## Scientific Question

What are the main uncertainty sources and validation priorities for the current Gaia-LAMOST candidate sample?

## Background and Motivation

This report begins **Project VI — Scientific Validation** in the research program *Galactic Archaeology with Gaia DR3 & LAMOST DR9*.

Projects II, III, and IV produced angular-momentum diagnostics, baseline orbit integration, population labels, priority candidates, and metallicity-readiness information. Project VI now organizes the major uncertainty sources and identifies candidates that require the highest validation priority.

This is a validation roadmap and uncertainty inventory, not a full Monte Carlo uncertainty propagation study.

## Data and Methods

Input file:

- `data/processed/project_iv_metallicity_candidates.csv`

Output files:

- `data/processed/project_vi_uncertainty_inventory.csv`
- `data/processed/project_vi_validation_priority_candidates.csv`

The inventory tracks:

- Distance provenance and distance-quality flags
- Orbit-angular-momentum consistency
- Population classification confidence
- Chemical-readiness limitations
- Metallicity availability
- Baseline galpy orbit quantities
- Candidate follow-up priority from Project III
- Chemical follow-up priority from Project IV

## Results

Total candidates:

- 27

Candidates with missing-parallax distance-quality flag:

- 27

Candidates with partially consistent orbit-angular-momentum evidence:

- 3

Candidates with limited population-classification confidence:

- 3

Candidates currently limited to [Fe/H]-only chemistry:

- 27

## Validation-Priority Counts

| project_vi_validation_priority   |   n |
|:---------------------------------|----:|
| validation_priority_B            |   9 |
| validation_priority_C            |   9 |
| validation_review_only           |   7 |
| validation_priority_A            |   2 |

## Validation-Risk Counts

| project_vi_validation_risk   |   n |
|:-----------------------------|----:|
| lower_validation_risk        |  24 |
| high_validation_risk         |   3 |

## Validation Summary by Population Group

| project_iii_population_group   | project_vi_validation_priority   | project_vi_validation_risk   |   n |   feh_median |   ecc_median |   zmax_median_kpc |   project_iii_priority_score_median |
|:-------------------------------|:---------------------------------|:-----------------------------|----:|-------------:|-------------:|------------------:|------------------------------------:|
| retrograde_halo                | validation_priority_B            | lower_validation_risk        |   6 |      -0.8415 |     0.923978 |           5.92028 |                                16.5 |
| retrograde_halo                | validation_priority_C            | lower_validation_risk        |   4 |      -0.9885 |     0.628666 |           3.14526 |                                14   |
| retrograde_halo                | validation_review_only           | lower_validation_risk        |   4 |      -0.584  |     0.456497 |           3.95593 |                                11   |
| prograde_hot_or_heated_disk    | validation_priority_C            | lower_validation_risk        |   3 |      -1.679  |     0.842909 |           4.00862 |                                12   |
| retrograde_uncertain           | validation_review_only           | high_validation_risk         |   3 |      -0.768  |     0.523503 |           1.90875 |                                 5   |
| radial_halo_or_gse_like        | validation_priority_B            | lower_validation_risk        |   2 |      -1.6075 |     0.9501   |           1.57554 |                                13.5 |
| general_halo                   | validation_priority_C            | lower_validation_risk        |   1 |      -0.534  |     0.947761 |           5.48566 |                                12   |
| high_inclination_halo          | validation_priority_B            | lower_validation_risk        |   1 |      -1.472  |     0.667406 |          18.9889  |                                15   |
| radial_halo_or_gse_like        | validation_priority_A            | lower_validation_risk        |   1 |      -1.539  |     0.836985 |          17.7844  |                                19   |
| radial_halo_or_gse_like        | validation_priority_C            | lower_validation_risk        |   1 |      -1.311  |     0.778207 |           1.05238 |                                12   |
| retrograde_halo                | validation_priority_A            | lower_validation_risk        |   1 |      -2.213  |     0.708753 |          52.8476  |                                21   |

## Interpretation

The current sample has strong internal dynamical structure, but several validation steps are still required before final scientific interpretation.

The most important limitation is distance uncertainty. The present orbit integration and angular-momentum calculations rely on the currently recovered distance information, and many candidates carry a missing-parallax quality flag. This does not invalidate the analysis, but it means that future uncertainty propagation is essential.

A second limitation is the use of a single Galactic potential in the baseline galpy integration. Potential-model dependence should be tested before final orbital claims are made.

A third limitation is chemical dimensionality. The current Project IV analysis is limited to [Fe/H]. Full chemical tagging requires alpha-element or individual abundance dimensions such as Mg, Ca, and Si.

Candidates with high Project III priority, high chemical follow-up priority, and elevated validation risk should be prioritized for Monte Carlo sampling, distance-quality review, and literature comparison.

## Validation Roadmap

Future Project VI work should include:

1. Monte Carlo sampling of distance and parallax uncertainties.
2. Proper-motion and radial-velocity uncertainty propagation.
3. Recalculation of Lz, Lperp, Ltotal, eccentricity, rperi, rap, and Zmax across sampled realizations.
4. Confidence intervals for orbit-derived quantities.
5. Sensitivity tests against different Galactic potentials.
6. Literature-region comparison for Gaia-Sausage-Enceladus, Helmi Stream, Sequoia, Nyx, and Splash.
7. Chemical-abundance uncertainty assessment if additional abundance columns are recovered.

## Deliverables

This step produces:

- Candidate-level uncertainty inventory
- Candidate-level validation priority table
- Validation roadmap report
- Notebook entry point for Project VI uncertainty inventory review

## Next Steps

The next Project VI step should be a small-scale Monte Carlo prototype on a limited number of high-priority candidates before scaling to the full sample.
