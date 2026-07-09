# Project II — Orbit–Angular Momentum Consistency Analysis

## Scientific Question

Are the angular-momentum-based orbital-family interpretations supported by the baseline galpy orbit integration?

## Background and Motivation

This report links two layers of **Project II — Orbital Dynamics**:

1. Angular-momentum diagnostics and orbital-family interpretation.
2. Baseline orbit integration with `galpy`.

The goal is to test whether candidate labels inferred from Lz, Lperp, Ltotal, rotation class, and inclination proxy are consistent with orbit-derived eccentricity, pericenter, apocenter, and Zmax.

This step is important because angular momentum alone is diagnostic but incomplete. Orbit integration provides an independent check on whether the inferred orbital-family labels are dynamically plausible.

## Data and Methods

Input file:

- `data/processed/project_ii_galpy_orbit_candidates.csv`

Output files:

- `data/processed/project_ii_orbit_angular_momentum_consistency.csv`
- `data/processed/project_ii_orbit_angular_momentum_consistency_summary.csv`

Figures:

- `figures/project_ii_orbit_eccentricity_vs_lz.png`
- `figures/project_ii_orbit_zmax_vs_lperp.png`
- `figures/project_ii_orbit_family_consistency.png`

The consistency analysis compares:

- Lz with galpy eccentricity
- Lperp with galpy Zmax
- Angular-momentum-based orbital-family labels with orbit-derived flags
- Radial or low-Lz expectations with high-eccentricity behavior
- High-Lperp expectations with high-Zmax behavior
- Disk-like expectations with disk-confined orbit proxies

## Results

Total candidates:

- 27

Successful galpy orbit integrations:

- 27

Consistency counts:

- Consistent: 24
- Partially consistent: 3
- Tension: 0
- Mixed or uncertain: 0

## Consistency-Label Counts

| orbit_am_consistency_label   |   n |
|:-----------------------------|----:|
| consistent                   |  24 |
| partially_consistent         |   3 |

## Expected Orbit Behavior from Angular-Momentum Labels

| am_expected_orbit_behavior           |   n |
|:-------------------------------------|----:|
| retrograde_halo_like_expected        |  11 |
| radial_or_high_eccentricity_expected |  11 |
| dynamically_hot_expected             |   3 |
| high_zmax_or_extended_orbit_expected |   2 |

## Consistency Summary by Orbital Family

| orbit_am_consistency_label   | orbital_family_interpretation             | rotation_class   | inclination_proxy_class   |   n |   ecc_median |   zmax_median_kpc |   rperi_median_kpc |   rap_median_kpc |   feh_median |   Lz_median |   Lperp_median |
|:-----------------------------|:------------------------------------------|:-----------------|:--------------------------|----:|-------------:|------------------:|-------------------:|-----------------:|-------------:|------------:|---------------:|
| consistent                   | radial_metal_poor_halo_like               | low_Lz_or_radial | low_Lperp                 |   6 |     0.940777 |          2.03211  |          0.477412  |         13.7931  |      -1.1515 |    101.215  |        200.292 |
| consistent                   | retrograde_low_inclination_halo_like      | retrograde       | low_Lperp                 |   6 |     0.553674 |          3.14526  |          3.94226   |         15.554   |      -0.7565 |  -1418.5    |        563.92  |
| consistent                   | radial_metal_poor_halo_like               | low_Lz_or_radial | moderate_Lperp            |   4 |     0.852832 |          8.18692  |          1.16336   |         13.3609  |      -1.126  |   -243.806  |        962.639 |
| consistent                   | prograde_hot_or_metal_poor_candidate      | prograde         | low_Lperp                 |   3 |     0.842909 |          4.00862  |          1.63164   |         19.4812  |      -1.679  |    770.758  |        385.255 |
| consistent                   | retrograde_moderate_inclination_halo_like | retrograde       | moderate_Lperp            |   2 |     0.552568 |          5.27501  |          2.99795   |         10.4597  |      -0.76   |   -895.579  |        963.357 |
| consistent                   | low_Lz_or_radial_candidate                | low_Lz_or_radial | low_Lperp                 |   1 |     0.98073  |          0.467095 |          0.0887948 |          9.12697 |      -0.796  |    -54.9331 |        150.91  |
| consistent                   | prograde_high_inclination_halo_like       | prograde         | high_Lperp                |   1 |     0.667406 |         18.9889   |          7.54505   |         37.8259  |      -1.472  |   2417.3    |       1650.51  |
| consistent                   | retrograde_high_inclination_halo_like     | retrograde       | high_Lperp                |   1 |     0.708753 |         52.8476   |          9.38951   |         55.0885  |      -2.213  |   -961.146  |       3531.46  |
| partially_consistent         | retrograde_low_inclination_halo_like      | retrograde       | low_Lperp                 |   3 |     0.523503 |          1.90875  |          2.99677   |          9.85267 |      -0.768  |  -1067.86   |        513.104 |

## Interpretation

The consistency analysis provides a bridge between angular-momentum diagnostics and orbit-integrated dynamics.

Candidates labelled as radial or low-Lz are expected to show high eccentricity. When these stars also have high galpy eccentricity, the angular-momentum interpretation is strengthened.

Candidates with high Lperp or high-inclination labels are expected to show large vertical excursions. When these stars also have high Zmax, the orbit integration supports the angular-momentum interpretation.

Retrograde candidates are expected to remain dynamically hot or halo-like in orbit-integrated diagnostics. They may not all be high-eccentricity objects, but retrograde angular momentum combined with elevated Zmax, broad radial excursions, or non-disk-confined behavior supports a halo-like interpretation.

Cases marked as tension are scientifically useful. They may indicate limitations of the heuristic angular-momentum labels, sensitivity to distance estimates, or genuinely complex orbital behavior. These candidates should be prioritized for later uncertainty propagation and manual inspection.

## Validation and Uncertainty

This is a consistency check, not a final population classification.

Current limitations:

- The orbit integration uses a single baseline Galactic potential.
- No Monte Carlo uncertainty propagation has been applied.
- Distance, proper-motion, and radial-velocity errors have not yet been propagated.
- The consistency labels are heuristic and should not be interpreted as final astrophysical classes.
- Literature-defined regions for known merger remnants have not yet been applied.

## Deliverables

This step produces:

- Candidate-level orbit-angular-momentum consistency table
- Group-level consistency summary table
- Eccentricity versus Lz diagnostic figure
- Zmax versus Lperp diagnostic figure
- Consistency-count diagnostic figure
- Project II consistency report

## Next Steps

The next Project II steps are:

1. Inspect candidates marked as tension or partially consistent.
2. Add Energy-Lz diagnostics.
3. Add action-space diagnostics when available.
4. Prepare Project III initial stellar-population classification using both angular-momentum and orbit-integrated evidence.
5. Move uncertainty propagation into Project VI.
