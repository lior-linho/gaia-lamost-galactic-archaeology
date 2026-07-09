# Project V — Computational Discovery

## Scientific Question

Can unsupervised and statistical methods identify robust candidate structures in Gaia-LAMOST phase-space and chemical-feature space?

## Background and Motivation

This project represents the computational and data-science core of the research program. Instead of relying only on predefined labels, it tests whether independent algorithms can recover consistent candidate groups, outliers, or substructures.

## Data and Methods

Core methods include:

- PCA
- UMAP
- DBSCAN
- HDBSCAN
- Gaussian Mixture Models
- OPTICS
- Hierarchical clustering
- Consensus clustering
- Anomaly detection

Current completed methods include:

- PCA feature-space design
- UMAP embedding
- DBSCAN baseline clustering
- Small DBSCAN parameter sweep
- Cross-method candidate evidence summary

## Existing Repository Outputs

Relevant existing work includes:

- `notebooks/07_project2_feature_space_design.ipynb`
- `notebooks/08_project2_pca_baseline_embedding.ipynb`
- `notebooks/09_project2_umap_embedding.ipynb`
- `notebooks/10_project2_dbscan_baseline_clustering.ipynb`
- `notebooks/11_project2_dbscan_robustness_analysis.ipynb`
- `notebooks/12_project2_candidate_cross_method_summary.ipynb`
- `data/processed/project2_candidate_cross_method_summary.csv`
- `figures/project2_candidate_cross_method_evidence_summary.png`
- `report/project2_scientific_interpretation_and_final_packaging.md`

## Results

The initial computational-discovery layer has been completed. It produced a cross-method candidate summary that compares evidence from multiple feature-space and clustering approaches.

## Validation and Uncertainty

Current validation includes:

- Cross-method comparison
- DBSCAN parameter sensitivity
- Candidate evidence scoring
- Visual inspection of embedding and clustering behavior

Further validation will later include additional algorithms and consensus clustering.

## Discussion

This project is central to the identity of the full research program because it shows how data-science methods can contribute to astrophysical discovery.

## Deliverables

- Computational Discovery Catalogue
- PCA diagnostics
- UMAP diagnostics
- Clustering outputs
- Robustness analysis
- Cross-method candidate evidence summary
- Future consensus-clustering report
