# Notebooks

This folder contains exploratory and analysis notebooks for the Gaia–LAMOST Galactic Archaeology Project.

## Purpose

The notebooks document the main scientific workflow, including data querying, catalogue exploration, cross-matching, feature construction, visualization, candidate diagnostics, and machine-learning assisted population analysis.

## Notebook Organization

The notebooks are organized by project stage and milestone.

### Project 1: Gaia–LAMOST chemo-kinematic pipeline

```text
01_gaia_dr3_query.ipynb
02_lamost_catalogue_exploration.ipynb
03_chemo_kinematic_features.ipynb
04_larger_sample_kinematic_preparation.ipynb
05_galactic_velocity_candidate_validation.ipynb
06_candidate_level_diagnostics.ipynb
```

Project 1 builds the core Gaia–LAMOST workflow: Gaia DR3 query, LAMOST exploration, cross-matching, feature construction, larger-sample preparation, and candidate-level physical diagnostics.

### Project 2: Machine-learning assisted candidate prioritization

```text
07_project2_feature_space_design.ipynb
08_project2_pca_baseline_embedding.ipynb
09_project2_umap_embedding.ipynb
10_project2_dbscan_baseline_clustering.ipynb
11_project2_dbscan_robustness_analysis.ipynb
12_project2_candidate_cross_method_summary.ipynb
```

Project 2 extends the pipeline with feature-space design, PCA, UMAP, DBSCAN, robustness checks, and cross-method candidate evidence summaries.

## Notes

Notebooks are used for exploration, validation, figure generation, and milestone-level reproducibility.

Reusable functions and stable analysis code may gradually be moved into the `src/` folder in later stages to improve reproducibility and maintainability.

## Recommended Practice

Each notebook should include:

- a short goal at the beginning
- clear section headings
- comments explaining important steps
- saved outputs when relevant
- links to related milestone notes, reports, or figures
