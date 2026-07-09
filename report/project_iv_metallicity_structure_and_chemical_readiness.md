# Project IV — Metallicity Structure and Chemical Readiness

## Scientific Question

What chemical information is currently available for the Gaia-LAMOST candidate sample, and what does the [Fe/H] distribution suggest across the Project III population groups?

## Background and Motivation

This report begins **Project IV — Chemical Evolution** in the research program *Galactic Archaeology with Gaia DR3 & LAMOST DR9*.

The current candidate table contains [Fe/H] but does not yet contain alpha-element or individual abundance dimensions such as Mg, Ca, or Si. Therefore, the first Project IV step focuses on metallicity structure and chemical-readiness assessment.

This step connects the Project III population labels with the available LAMOST metallicity information.

## Data and Methods

Input file:

- `data/processed/project_iii_population_priority_candidates.csv`

Output files:

- `data/processed/project_iv_metallicity_candidates.csv`
- `data/processed/project_iv_metallicity_summary.csv`

Figures:

- `figures/project_iv_feh_distribution.png`
- `figures/project_iv_feh_by_population_group.png`
- `figures/project_iv_feh_by_priority_tier.png`

Available chemical dimensions:

- feh

Missing or not-yet-integrated chemical dimensions:

- alpha, Mg, Ca, Si

The analysis assigns each candidate a metallicity class:

- Very metal-poor: [Fe/H] <= -2.0
- Metal-poor: -2.0 < [Fe/H] <= -1.5
- Moderately metal-poor: -1.5 < [Fe/H] <= -1.0
- Metal-intermediate: -1.0 < [Fe/H] <= -0.5
- Metal-rich relative: [Fe/H] > -0.5

It also assigns a chemical follow-up priority based on metallicity, Project III priority tier, population group, eccentricity, and Zmax.

## Results

Total candidates:

- 27

Candidates with [Fe/H]:

- 27

Candidates missing [Fe/H]:

- 0

Metallicity highlights:

- Very metal-poor candidates: 2
- Metal-poor candidates: 3
- Moderately metal-poor candidates: 8

Chemical follow-up priorities:

- Chemical Priority A: 5
- Chemical Priority B: 9

## Metallicity-Class Counts

| project_iv_metallicity_class   |   n |
|:-------------------------------|----:|
| metal_intermediate             |  14 |
| moderately_metal_poor          |   8 |
| metal_poor                     |   3 |
| very_metal_poor                |   2 |

## Chemical-Readiness Counts

| project_iv_chemical_readiness   |   n |
|:--------------------------------|----:|
| feh_only_ready                  |  27 |

## Chemical Follow-Up Priority Counts

| project_iv_chemical_followup_priority   |   n |
|:----------------------------------------|----:|
| chemical_priority_B                     |   9 |
| chemical_review_only                    |   7 |
| chemical_priority_C                     |   6 |
| chemical_priority_A                     |   5 |

## Metallicity Summary by Population Group

| project_iii_population_group   | project_iv_metallicity_class   | project_iv_chemical_followup_priority   |   n |   feh_median |   feh_min |   feh_max |   priority_score_median |   ecc_median |   zmax_median_kpc |   Lz_median |
|:-------------------------------|:-------------------------------|:----------------------------------------|----:|-------------:|----------:|----------:|------------------------:|-------------:|------------------:|------------:|
| retrograde_halo                | metal_intermediate             | chemical_priority_B                     |   4 |      -0.798  |    -0.883 |    -0.583 |                    14.5 |     0.925373 |           4.1264  |    -244.972 |
| retrograde_halo                | metal_intermediate             | chemical_review_only                    |   4 |      -0.584  |    -0.68  |    -0.543 |                    11   |     0.456497 |           3.95593 |   -2370.23  |
| retrograde_uncertain           | metal_intermediate             | chemical_review_only                    |   3 |      -0.768  |    -0.915 |    -0.684 |                     5   |     0.523503 |           1.90875 |   -1067.86  |
| prograde_hot_or_heated_disk    | metal_poor                     | chemical_priority_C                     |   2 |      -1.701  |    -1.723 |    -1.679 |                    12   |     0.754821 |           2.88866 |    1151.15  |
| radial_halo_or_gse_like        | moderately_metal_poor          | chemical_priority_B                     |   2 |      -1.209  |    -1.311 |    -1.107 |                    12.5 |     0.864507 |           1.0459  |     284.473 |
| retrograde_halo                | metal_intermediate             | chemical_priority_C                     |   2 |      -0.892  |    -0.951 |    -0.833 |                    13   |     0.493081 |           4.868   |   -1328.58  |
| retrograde_halo                | moderately_metal_poor          | chemical_priority_A                     |   2 |      -1.2825 |    -1.369 |    -1.196 |                    18   |     0.899842 |           6.26369 |    -300.151 |
| retrograde_halo                | moderately_metal_poor          | chemical_priority_B                     |   2 |      -1.1715 |    -1.317 |    -1.026 |                    14   |     0.746901 |           1.91584 |    -714.399 |
| general_halo                   | metal_intermediate             | chemical_priority_C                     |   1 |      -0.534  |    -0.534 |    -0.534 |                    12   |     0.947761 |           5.48566 |     110.095 |
| high_inclination_halo          | moderately_metal_poor          | chemical_priority_B                     |   1 |      -1.472  |    -1.472 |    -1.472 |                    15   |     0.667406 |          18.9889  |    2417.3   |
| prograde_hot_or_heated_disk    | moderately_metal_poor          | chemical_priority_C                     |   1 |      -1.116  |    -1.116 |    -1.116 |                    15   |     0.887901 |           8.44088 |     548.771 |
| radial_halo_or_gse_like        | metal_poor                     | chemical_priority_A                     |   1 |      -1.539  |    -1.539 |    -1.539 |                    19   |     0.836985 |          17.7844  |     471.072 |
| radial_halo_or_gse_like        | very_metal_poor                | chemical_priority_A                     |   1 |      -2.108  |    -2.108 |    -2.108 |                    14   |     0.949394 |           2.11166 |     149.384 |
| retrograde_halo                | very_metal_poor                | chemical_priority_A                     |   1 |      -2.213  |    -2.213 |    -2.213 |                    21   |     0.708753 |          52.8476  |    -961.146 |

## Interpretation

The current chemical analysis is limited to [Fe/H], but even this single chemical dimension is useful for Galactic archaeology.

Very metal-poor and metal-poor candidates are especially important because they are more likely to trace old halo populations or accreted components. When low metallicity is combined with radial, retrograde, high-inclination, or high-Zmax orbital behavior, the candidate becomes especially valuable for later follow-up.

The Project III radial halo or GSE-like and retrograde halo candidates provide the strongest immediate targets for chemical interpretation. However, without alpha-element or individual abundance information, the current analysis cannot perform full chemical tagging.

The current Project IV result should therefore be interpreted as a metallicity-readiness layer rather than a complete chemical-evolution analysis.

## Validation and Uncertainty

Current limitations:

- Only [Fe/H] is available in the current integrated candidate table.
- Alpha-element and individual abundance columns have not yet been integrated.
- LAMOST abundance calibration and quality flags have not yet been analyzed.
- No uncertainty propagation has been applied to metallicity.
- Chemical tagging is not yet possible with [Fe/H] alone.

## Deliverables

This step produces:

- Project IV metallicity candidate table
- Project IV metallicity summary table
- [Fe/H] distribution figure
- [Fe/H] by population group figure
- [Fe/H] by priority tier figure
- Chemical-readiness report

## Next Steps

The next Project IV tasks are:

1. Search original LAMOST fields for alpha, Mg, Ca, Si, or other abundance columns.
2. Add abundance-quality checks if abundance columns are available.
3. Compare metallicity distributions across Project III population groups.
4. Prepare chemical-tagging analysis if multi-element abundances can be recovered.
5. Carry chemical uncertainty and calibration limitations into Project VI.
