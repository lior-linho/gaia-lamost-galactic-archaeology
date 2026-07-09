# Project II — galpy Orbit Integration Preparation

## Scientific Question

Can the current Project II candidate table support full orbit integration in a Milky Way potential?

## Background and Motivation

This report prepares the next stage of **Project II — Orbital Dynamics** in the research program *Galactic Archaeology with Gaia DR3 & LAMOST DR9*.

The previous Project II step produced candidate-level orbital-family interpretation labels using angular momentum, velocity diagnostics, metallicity flags, and distance provenance. The next scientific step is to move from angular-momentum diagnostics to full orbit integration.

The planned orbit-integration tool is `galpy`.

## Input Data

Primary input file:

- `data/processed/project_ii_orbital_family_candidates.csv`

Orbit-integration preparation audit:

- `data/processed/project_ii_galpy_input_audit.csv`

Notebook entry point:

- `notebooks/18_project_ii_galpy_orbit_integration_preparation.ipynb`

## Required Input Quantities

Full orbit integration requires, at minimum:

- Right ascension
- Declination
- Proper motion in right ascension
- Proper motion in declination
- Radial velocity
- Distance estimate
- Distance provenance
- Distance-quality flag

## Input Availability

Total candidates:

- 27

Candidates currently ready for basic 6D orbit input:

- 27

Candidates not ready for basic 6D orbit input:

- 0

## Required-Column Audit

| column                        | available   |   non_null_count |   total_rows |   non_null_fraction |
|:------------------------------|:------------|-----------------:|-------------:|--------------------:|
| source_id                     | True        |               27 |           27 |                   1 |
| ra_gaia                       | True        |               27 |           27 |                   1 |
| dec_gaia                      | True        |               27 |           27 |                   1 |
| pmra_recovered                | True        |               27 |           27 |                   1 |
| pmdec_recovered               | True        |               27 |           27 |                   1 |
| rv                            | True        |               27 |           27 |                   1 |
| distance_for_l_kpc            | True        |               27 |           27 |                   1 |
| distance_recovery_source      | True        |               27 |           27 |                   1 |
| distance_quality_flag         | True        |               27 |           27 |                   1 |
| feh                           | True        |               27 |           27 |                   1 |
| orbital_family_interpretation | True        |               27 |           27 |                   1 |
| rotation_class                | True        |               27 |           27 |                   1 |
| inclination_proxy_class       | True        |               27 |           27 |                   1 |

## Orbital-Family Context

The current candidate sample contains the following orbital-family interpretation groups:

| orbital_family_interpretation             |   n |
|:------------------------------------------|----:|
| radial_metal_poor_halo_like               |  10 |
| retrograde_low_inclination_halo_like      |   9 |
| prograde_hot_or_metal_poor_candidate      |   3 |
| retrograde_moderate_inclination_halo_like |   2 |
| retrograde_high_inclination_halo_like     |   1 |
| prograde_high_inclination_halo_like       |   1 |
| low_Lz_or_radial_candidate                |   1 |

## Distance-Provenance Context

| distance_recovery_source                 |   n |
|:-----------------------------------------|----:|
| gaia_lamost_larger_velocity_features.csv |  27 |

## Distance-Quality Context

| distance_quality_flag   |   n |
|:------------------------|----:|
| missing_parallax        |  27 |

## Planned Method

The next orbit-integration stage will use `galpy` to integrate each candidate orbit in a Milky Way-like gravitational potential.

Planned steps:

1. Confirm the coordinate convention used by the existing Galactocentric velocity and angular-momentum calculations.
2. Convert Gaia astrometric observables and LAMOST radial velocities into `galpy` orbit inputs.
3. Select a baseline Milky Way potential, such as `MWPotential2014`.
4. Integrate each orbit over a physically motivated time interval.
5. Compute orbital parameters:
   - Eccentricity
   - Apocenter
   - Pericenter
   - Zmax
   - Guiding radius
   - Orbital energy, where available
6. Compare orbit-derived quantities with the existing angular-momentum interpretation labels.
7. Export an initial Project II orbital catalog.

## Planned Outputs

Future outputs should include:

- `data/processed/project_ii_galpy_orbit_candidates.csv`
- `data/processed/project_ii_galpy_orbit_summary.csv`
- Orbit diagnostic figures
- Energy-Lz diagram
- Toomre diagram
- Orbit-family comparison plots
- Project II orbit-integration report

## Validation and Uncertainty

This preparation step does not yet perform Monte Carlo uncertainty propagation.

Important future validation tasks include:

- Propagating parallax and distance uncertainty
- Propagating proper-motion uncertainty
- Propagating radial-velocity uncertainty
- Testing sensitivity to the adopted Galactic potential
- Comparing orbit-derived families with literature-defined structures

## Discussion

This step confirms whether the current Project II candidate table is ready for full orbit integration. It also establishes the method plan for the next notebook.

The current orbital-family interpretation remains heuristic until orbit integration, uncertainty propagation, and literature comparison are completed.

## Next Step

The next active task should be:

**Project II — galpy Orbit Integration Baseline**

This will create the first orbit-integrated version of the candidate catalogue.
