# Project II — galpy Baseline Orbit Integration

## Scientific Question

What orbital parameters are obtained for the Gaia-LAMOST candidate sample when integrated in a baseline Milky Way potential?

## Background and Motivation

This report extends **Project II — Orbital Dynamics** from angular-momentum diagnostics into baseline orbit integration.

The previous Project II steps established:

- Candidate-level angular-momentum diagnostics
- Orbital-family interpretation labels
- A galpy orbit-integration readiness audit

The readiness audit showed that all 27 candidates have the required 6D input quantities for baseline orbit integration. This report presents the first orbit-integrated candidate table using `galpy`.

## Data and Methods

Input file:

- `data/processed/project_ii_orbital_family_candidates.csv`

Output files:

- `data/processed/project_ii_galpy_orbit_candidates.csv`
- `data/processed/project_ii_galpy_orbit_summary.csv`

Figures:

- `figures/project_ii_galpy_orbit_eccentricity.png`
- `figures/project_ii_galpy_orbit_zmax.png`
- `figures/project_ii_galpy_orbit_rap_rperi.png`

Orbit integration setup:

- Tool: `galpy`
- Potential: `MWPotential2014`
- Solar radius parameter, ro: 8.2 kpc
- Solar velocity parameter, vo: 232.0 km/s
- Solar motion: Schoenrich et al. convention as implemented in galpy
- Integration time: 5.0 Gyr
- Number of time steps: 1001

Input observables:

- Right ascension
- Declination
- Distance
- Proper motion in right ascension
- Proper motion in declination
- Radial velocity

Computed orbital quantities:

- Eccentricity
- Pericenter
- Apocenter
- Zmax
- Baseline orbital energy proxy from galpy

## Results

Total candidates:

- 27

Candidates ready for galpy input:

- 27

Successful baseline orbit integrations:

- 27

Failed baseline orbit integrations:

- 0

Derived diagnostic counts:

- Radial-orbit candidates with eccentricity >= 0.7: 16
- High-Zmax candidates with Zmax >= 3 kpc: 16
- Inner-halo-like orbit candidates by baseline orbit proxy: 24
- Disk-confined orbit candidates by baseline orbit proxy: 0

## Orbit Summary by Previous Orbital-Family Interpretation

| orbital_family_interpretation             | rotation_class   | inclination_proxy_class   |   n |   galpy_success_n |   ecc_median |   ecc_min |   ecc_max |   rperi_median_kpc |   rap_median_kpc |   zmax_median_kpc |   feh_median |   Lz_median |   Lperp_median |
|:------------------------------------------|:-----------------|:--------------------------|----:|------------------:|-------------:|----------:|----------:|-------------------:|-----------------:|------------------:|-------------:|------------:|---------------:|
| retrograde_low_inclination_halo_like      | retrograde       | low_Lperp                 |   9 |                 9 |     0.523503 |  0.255368 |  0.804544 |          2.99677   |         12.1373  |          2.76383  |      -0.768  |  -1125.14   |        540.73  |
| radial_metal_poor_halo_like               | low_Lz_or_radial | low_Lperp                 |   6 |                 6 |     0.940777 |  0.778207 |  0.950807 |          0.477412  |         13.7931  |          2.03211  |      -1.1515 |    101.215  |        200.292 |
| radial_metal_poor_halo_like               | low_Lz_or_radial | moderate_Lperp            |   4 |                 4 |     0.852832 |  0.801416 |  0.916952 |          1.16336   |         13.3609  |          8.18692  |      -1.126  |   -243.806  |        962.639 |
| prograde_hot_or_metal_poor_candidate      | prograde         | low_Lperp                 |   3 |                 3 |     0.842909 |  0.666734 |  0.887901 |          1.63164   |         19.4812  |          4.00862  |      -1.679  |    770.758  |        385.255 |
| retrograde_moderate_inclination_halo_like | retrograde       | moderate_Lperp            |   2 |                 2 |     0.552568 |  0.537064 |  0.568073 |          2.99795   |         10.4597  |          5.27501  |      -0.76   |   -895.579  |        963.357 |
| low_Lz_or_radial_candidate                | low_Lz_or_radial | low_Lperp                 |   1 |                 1 |     0.98073  |  0.98073  |  0.98073  |          0.0887948 |          9.12697 |          0.467095 |      -0.796  |    -54.9331 |        150.91  |
| prograde_high_inclination_halo_like       | prograde         | high_Lperp                |   1 |                 1 |     0.667406 |  0.667406 |  0.667406 |          7.54505   |         37.8259  |         18.9889   |      -1.472  |   2417.3    |       1650.51  |
| retrograde_high_inclination_halo_like     | retrograde       | high_Lperp                |   1 |                 1 |     0.708753 |  0.708753 |  0.708753 |          9.38951   |         55.0885  |         52.8476   |      -2.213  |   -961.146  |       3531.46  |

## Interpretation

This baseline orbit-integration step provides the first direct orbital parameters for the Project II candidate sample.

The eccentricity distribution helps distinguish radial or dynamically hot candidates from more circular orbit candidates. High-eccentricity candidates are especially important for later comparison with radial halo structures and merger-related debris.

The Zmax distribution helps separate disk-confined candidates from stars with more vertically extended or halo-like orbits. Candidates with large Zmax values should be prioritized in later stellar-population analysis.

The apocenter-pericenter relation provides a first view of orbit size and radial extent. Stars with small pericenters and large apocenters may be dynamically hot or halo-like, while candidates with smaller radial excursions may be more disk-like.

These orbit-derived quantities should be compared directly with the earlier angular-momentum-based orbital-family labels. Agreement between angular-momentum interpretation and orbit-integrated behavior strengthens the candidate classification, while disagreement highlights stars requiring further inspection.

## Validation and Uncertainty

This is a baseline integration, not a final orbit solution.

Current limitations:

- No Monte Carlo uncertainty propagation has been applied.
- The result depends on the adopted Galactic potential.
- Distances are based on the current recovered distance column.
- Gaia astrometric covariance has not yet been propagated.
- The output should not yet be treated as a final population classification.

Future validation should include:

- Monte Carlo sampling of astrometric and radial-velocity uncertainties
- Distance uncertainty propagation
- Potential-model sensitivity tests
- Literature comparison with known merger-remnant regions
- Action-space and Energy-Lz diagnostics

## Deliverables

This step produces:

- Baseline galpy orbit candidate table
- Baseline galpy orbit summary table
- Eccentricity diagnostic figure
- Zmax diagnostic figure
- Apocenter-pericenter diagnostic figure
- Project II baseline orbit-integration report

## Next Steps

The next Project II tasks are:

1. Inspect outliers in eccentricity, Zmax, apocenter, and pericenter.
2. Compare baseline orbit parameters with angular-momentum orbital-family labels.
3. Add Energy-Lz diagnostics.
4. Add Toomre-style diagnostics using the orbit-integrated sample.
5. Prepare Monte Carlo uncertainty propagation in Project VI.
