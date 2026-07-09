# Project III — Population Classification Review

## Scientific Question

Which Project III population candidates should be prioritized for later literature comparison, chemical interpretation, and uncertainty propagation?

## Background and Motivation

This report reviews the first-pass Project III stellar-population classification. The purpose is not to create new population labels, but to identify which candidates are most scientifically valuable for later follow-up.

The review combines population label, classification confidence, orbit-angular-momentum consistency, metallicity, eccentricity, Zmax, Lz, Lperp, and distance provenance into a simple priority score.

## Data and Methods

Input file:

- `data/processed/project_iii_population_candidates.csv`

Output files:

- `data/processed/project_iii_population_priority_candidates.csv`
- `data/processed/project_iii_population_review_summary.csv`

The priority score gives higher weight to candidates with:

- Consistent orbit-angular-momentum evidence
- Metal-poor chemistry
- High eccentricity
- High Zmax
- Retrograde angular momentum
- Large Lperp
- Inner-halo-like orbit proxy
- Radial halo, retrograde halo, or high-inclination halo group labels

Priority tiers are defined as:

- Priority A: score >= 16
- Priority B: score >= 12
- Priority C: score >= 9
- Review only: score < 9

The score is heuristic and intended for research triage, not final astrophysical classification.

## Results

Total candidates reviewed:

- 27

Priority tiers:

- Priority A: 6
- Priority B: 14
- Priority C: 4
- Review only: 3

## Priority-Tier Counts

| project_iii_priority_tier   |   n |
|:----------------------------|----:|
| priority_B                  |  14 |
| priority_A                  |   6 |
| priority_C                  |   4 |
| review_only                 |   3 |

## Population-Group Counts

| project_iii_population_group   |   n |
|:-------------------------------|----:|
| retrograde_halo                |  15 |
| radial_halo_or_gse_like        |   4 |
| prograde_hot_or_heated_disk    |   3 |
| retrograde_uncertain           |   3 |
| high_inclination_halo          |   1 |
| general_halo                   |   1 |

## Review Summary

| project_iii_population_group   | project_iii_priority_tier   |   n |   score_median |   feh_median |   ecc_median |   zmax_median_kpc |   Lz_median |   Lperp_median |
|:-------------------------------|:----------------------------|----:|---------------:|-------------:|-------------:|------------------:|------------:|---------------:|
| retrograde_halo                | priority_A                  |   5 |           18   |       -1.196 |     0.868678 |           6.98706 |    -320.509 |        837.896 |
| radial_halo_or_gse_like        | priority_A                  |   1 |           19   |       -1.539 |     0.836985 |          17.7844  |     471.072 |       1303.9   |
| retrograde_halo                | priority_B                  |   6 |           13.5 |       -0.892 |     0.746901 |           2.54544 |    -714.399 |        369.01  |
| prograde_hot_or_heated_disk    | priority_B                  |   3 |           12   |       -1.679 |     0.842909 |           4.00862 |     770.758 |        385.255 |
| radial_halo_or_gse_like        | priority_B                  |   3 |           13   |       -1.311 |     0.949394 |           1.05238 |     149.384 |        192.474 |
| general_halo                   | priority_B                  |   1 |           12   |       -0.534 |     0.947761 |           5.48566 |     110.095 |        407.421 |
| high_inclination_halo          | priority_B                  |   1 |           15   |       -1.472 |     0.667406 |          18.9889  |    2417.3   |       1650.51  |
| retrograde_halo                | priority_C                  |   4 |           11   |       -0.584 |     0.456497 |           3.95593 |   -2370.23  |        573.71  |
| retrograde_uncertain           | review_only                 |   3 |            5   |       -0.768 |     0.523503 |           1.90875 |   -1067.86  |        513.104 |

## Top Priority Candidates

|           source_id | project_iii_priority_tier   |   project_iii_priority_score | project_iii_population_label               | project_iii_population_group   | project_iii_population_confidence   | orbit_am_consistency_label   |    feh |   galpy_eccentricity |   galpy_zmax_kpc |   galpy_rperi_kpc |   galpy_rap_kpc |   Lz_kpc_kms |   Lperp_kpc_kms | distance_recovery_source                 | distance_quality_flag   | project_iii_review_notes                                                                                                                                                                                                                                                                |
|--------------------:|:----------------------------|-----------------------------:|:-------------------------------------------|:-------------------------------|:------------------------------------|:-----------------------------|-------:|---------------------:|-----------------:|------------------:|----------------:|-------------:|----------------:|:-----------------------------------------|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 3089847099636770560 | priority_A                  |                           21 | retrograde_high_inclination_halo_candidate | retrograde_halo                | moderate                            | consistent                   | -2.213 |             0.708753 |         52.8476  |          9.38951  |         55.0885 |     -961.146 |        3531.46  | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_high_inclination_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-2.21; ecc=0.709; Zmax=52.85 kpc; rperi=9.39 kpc; rap=55.09 kpc; Lz=-961.1; Lperp=3531.5; metal-poor; radial orbit; high Zmax; inner-halo-like proxy          |
| 3089534353001157632 | priority_A                  |                           19 | radial_halo_gse_like_candidate             | radial_halo_or_gse_like        | moderate                            | consistent                   | -1.539 |             0.836985 |         17.7844  |          1.94372  |         21.9035 |      471.072 |        1303.9   | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=radial_halo_or_gse_like; label=radial_halo_gse_like_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.54; ecc=0.837; Zmax=17.78 kpc; rperi=1.94 kpc; rap=21.90 kpc; Lz=471.1; Lperp=1303.9; metal-poor; radial orbit; high Zmax; inner-halo-like proxy               |
| 3089780884124744832 | priority_A                  |                           18 | retrograde_halo_candidate                  | retrograde_halo                | moderate                            | consistent                   | -1.369 |             0.868678 |          5.54032 |          0.778699 |         11.0807 |     -279.793 |         837.896 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.37; ecc=0.869; Zmax=5.54 kpc; rperi=0.78 kpc; rap=11.08 kpc; Lz=-279.8; Lperp=837.9; metal-poor; radial orbit; high Zmax; inner-halo-like proxy                             |
| 3084642080312126464 | priority_A                  |                           18 | retrograde_halo_candidate                  | retrograde_halo                | moderate                            | consistent                   | -1.196 |             0.931005 |          6.98706 |          0.674419 |         18.8753 |     -320.509 |         556.688 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.20; ecc=0.931; Zmax=6.99 kpc; rperi=0.67 kpc; rap=18.88 kpc; Lz=-320.5; Lperp=556.7; metal-poor; radial orbit; high Zmax; inner-halo-like proxy                             |
| 3083736976083264768 | priority_A                  |                           17 | retrograde_high_inclination_halo_candidate | retrograde_halo                | moderate                            | consistent                   | -0.583 |             0.801416 |         10.0736  |          1.54802  |         14.0425 |     -450.786 |        1087.38  | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_high_inclination_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-0.58; ecc=0.801; Zmax=10.07 kpc; rperi=1.55 kpc; rap=14.04 kpc; Lz=-450.8; Lperp=1087.4; radial orbit; high Zmax; inner-halo-like proxy                      |
| 3084926441506740992 | priority_A                  |                           16 | retrograde_halo_candidate                  | retrograde_halo                | moderate                            | consistent                   | -0.883 |             0.916952 |          6.30024 |          0.549306 |         12.6794 |     -207.818 |         810.262 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-0.88; ecc=0.917; Zmax=6.30 kpc; rperi=0.55 kpc; rap=12.68 kpc; Lz=-207.8; Lperp=810.3; radial orbit; high Zmax; inner-halo-like proxy                                         |
| 3089944573918027648 | priority_B                  |                           15 | high_inclination_halo_candidate            | high_inclination_halo          | moderate                            | consistent                   | -1.472 |             0.667406 |         18.9889  |          7.54505  |         37.8259 |     2417.3   |        1650.51  | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=high_inclination_halo; label=high_inclination_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.47; ecc=0.667; Zmax=18.99 kpc; rperi=7.55 kpc; rap=37.83 kpc; Lz=2417.3; Lperp=1650.5; metal-poor; high Zmax; inner-halo-like proxy                             |
| 3083553117121981312 | priority_B                  |                           15 | prograde_hot_halo_or_heated_disk_candidate | prograde_hot_or_heated_disk    | moderate                            | consistent                   | -1.116 |             0.887901 |          8.44088 |          1.26824  |         21.3589 |      548.771 |         622.133 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=prograde_hot_or_heated_disk; label=prograde_hot_halo_or_heated_disk_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.12; ecc=0.888; Zmax=8.44 kpc; rperi=1.27 kpc; rap=21.36 kpc; Lz=548.8; Lperp=622.1; metal-poor; radial orbit; high Zmax; inner-halo-like proxy |
| 3089545558572418048 | priority_B                  |                           14 | radial_halo_gse_like_candidate             | radial_halo_or_gse_like        | moderate                            | consistent                   | -2.108 |             0.949394 |          2.11166 |          0.355051 |         13.6768 |      149.384 |         133.539 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=radial_halo_or_gse_like; label=radial_halo_gse_like_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-2.11; ecc=0.949; Zmax=2.11 kpc; rperi=0.36 kpc; rap=13.68 kpc; Lz=149.4; Lperp=133.5; metal-poor; radial orbit; inner-halo-like proxy                            |
| 3089512263986192512 | priority_B                  |                           14 | retrograde_halo_candidate                  | retrograde_halo                | moderate                            | consistent                   | -1.317 |             0.689258 |          3.13832 |          2.23268  |         12.1373 |     -875.155 |         633.534 | gaia_lamost_larger_velocity_features.csv | missing_parallax        | group=retrograde_halo; label=retrograde_halo_candidate; confidence=moderate; orbit_AM=consistent; [Fe/H]=-1.32; ecc=0.689; Zmax=3.14 kpc; rperi=2.23 kpc; rap=12.14 kpc; Lz=-875.2; Lperp=633.5; metal-poor; high Zmax; inner-halo-like proxy                                           |

## Interpretation

The stricter priority-tier definition produces a more useful follow-up list. Priority A candidates represent the strongest cases because they combine multiple independent lines of evidence, such as metal-poor chemistry, high eccentricity, large vertical excursions, retrograde motion, or strong halo-like orbit proxies.

The highest-priority objects include very metal-poor retrograde or high-inclination candidates, radial halo or GSE-like candidates, and dynamically hot candidates with strong orbit-integrated support.

Priority B and Priority C candidates remain scientifically useful, but they should be treated as secondary follow-up targets until uncertainty propagation and literature-region comparison are completed.

Retrograde uncertain candidates remain useful for review, but their orbit-integrated diagnostics are less extreme than the strongest halo-like cases.

## Validation and Uncertainty

This review is a triage layer.

Current limitations:

- The priority score is heuristic.
- No Monte Carlo uncertainty propagation has been applied.
- Literature-defined structure boundaries have not yet been used.
- Chemical abundance dimensions beyond [Fe/H] have not yet been incorporated.
- The result should guide follow-up analysis, not replace physical validation.

## Deliverables

This step produces:

- Priority candidate table
- Review summary table
- Project III population classification review report
- Notebook entry point for reviewing priority candidates

## Next Steps

The next Project III tasks are:

1. Inspect Priority A and Priority B candidates manually.
2. Add literature-informed comparison regions.
3. Prepare Project IV chemical-evolution inputs.
4. Move uncertainty propagation to Project VI.
