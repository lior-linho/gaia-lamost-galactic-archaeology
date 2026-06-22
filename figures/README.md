# Figures

This folder stores generated figures and visual outputs for the Gaia–LAMOST Galactic Archaeology Project.

## Purpose

Figures are used to document exploratory analysis, validate data quality, and present preliminary scientific results.

## Expected Figure Types

- Sky distribution plots
- Color-magnitude diagrams
- Distance and parallax distributions
- Proper motion distributions
- Metallicity distributions
- Chemo-kinematic visualizations
- Clustering and dimensionality reduction outputs

## Naming Convention

Figure files should use clear and descriptive names, for example:

    gaia_dr3_cmd.png
    gaia_lamost_distance_distribution.png
    metallicity_distribution.png
    velocity_feature_space.png
    clustering_umap_projection.png

## Notes

Generated figures should be linked or discussed in milestone notes, development logs, or the final research-style report.

Large or temporary figures should be avoided unless they are directly relevant to the project documentation.


## Project 2 Figures

Project 2 adds machine-learning diagnostic figures, including:

```text
project2_pca_combined_chemo_kinematic_by_feh.png
project2_pca_combined_chemo_kinematic_by_vtot.png
project2_pca_combined_chemo_kinematic_candidates.png
project2_umap_combined_chemo_kinematic_by_feh.png
project2_umap_combined_chemo_kinematic_by_vtot.png
project2_umap_combined_chemo_kinematic_candidates.png
project2_pca_dbscan_candidate_overlay.png
project2_umap_dbscan_candidate_overlay.png
project2_umap_dbscan_clusters.png
project2_candidate_cross_method_evidence_summary.png
```

These figures should be interpreted as diagnostic visualizations for candidate prioritization. PCA and UMAP show how candidate stars appear in different embedding spaces, while DBSCAN overlays and cross-method evidence plots summarize whether candidates remain interesting across multiple unsupervised views.

The figures are not standalone discovery evidence. They are supporting diagnostics for the Project 2 scientific interpretation and final packaging report.
