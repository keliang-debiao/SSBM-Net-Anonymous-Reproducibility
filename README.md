SSBM-Net Anonymous Reproducibility Package
This repository contains the implementation, configurations, data-preparation utilities, evaluation scripts, manuscript-support files, and validation resources for SSBM-Net.
Repository Contents
src/ssbm_net/
Core Python package for the SSBM-Net workflow.
- brs.py: bubble-risk component definitions, normalization, score construction, thresholding, and proxy-weight estimation.
- features.py: construction of user-level measurement features from interaction, topic, and social-network data.
- social.py: one-hop social-neighborhood feature aggregation and social-evidence availability handling.
- temporal.py: chronological partitioning support and future-outcome construction.
- splits.py: deterministic user-level and chronological split utilities.
- models.py: classification models and calibrated ensemble components.
- calibration.py: probability-calibration utilities.
- evaluation.py: binary, continuous, ranking, correlation, and calibration metrics.
- audit.py: recommendation and exposure-audit utilities.
- recommenders/: popularity, factorization, sequential, and reranking components used by the recommendation audit.
- pipeline.py: end-to-end measurement and validation pipeline.
- config.py: configuration loading and resolved-configuration export.
- io.py: processed-data loading and structured logging utilities.
- randomness.py: random-seed control utilities.
- cli.py: command-line entry support.
scripts/
Executable scripts for data preparation, study workflows, component analyses, sensitivity analyses, recommendation auditing, and release validation.
- prepare_kuairec.py: converts the public KuaiRec source files into the common processed schema.
- prepare_yelp.py: converts the public Yelp source files into the common processed schema.
- run_study.py: launches the main internal and temporal validation workflow.
- run_ablation.py: performs component-ablation analysis.
- run_component_analysis.py: evaluates individual measurement components.
- run_permutation_control.py: performs permutation-based control analysis.
- run_social_degree.py: examines social-degree strata.
- run_edge_removal.py: evaluates social-edge removal settings.
- run_exposure_sensitivity.py: evaluates exposure-related sensitivity settings.
- run_weight_sensitivity.py: evaluates alternative component-weight settings.
- run_weight_transfer.py: evaluates weight-transfer settings across datasets.
- run_threshold_sensitivity.py: evaluates alternative high-risk thresholds.
- run_calibration_comparison.py: compares probability-calibration settings.
- run_recommender_audit.py: runs the recommendation utility and exposure audit.
- check_manuscript_tables.py: checks the structure and consistency of manuscript table files.
- validate_release.py: checks imports, configuration parsing, manuscript tables, tests, and release text.
configs/
YAML configuration files for the study pipeline.
- base.yaml: shared paths, seeds, split settings, measurement parameters, calibration settings, validation settings, and recommendation settings.
- datasets/: dataset-specific configurations for KuaiRec and Yelp.
- experiments/: configurations for internal consistency, temporal validation, recommendation auditing, and sensitivity analyses.
data/
Contains the data contract and the required processed CSV schema. Raw public datasets are not included in this repository.
The processed-data interface uses:
- interactions.csv: user-item interactions and timestamps or interaction order.
- item_topics.csv: item-topic memberships and weights.
- social_edges.csv: directed user-user social links.
results/manuscript_tables/
Contains CSV files corresponding to the manuscript tables used for internal consistency, temporal validation, component analysis, permutation control, social analysis, sensitivity analysis, calibration comparison, and recommendation auditing.
tests/
Unit and pipeline tests covering feature construction, bubble-risk scoring, temporal processing, calibration, recommendation components, audit utilities, and the end-to-end pipeline.
logs/
Contains machine-readable and plain-text release-validation records.
Data Sources Represented
The repository includes preparation adapters and dataset configurations for the public KuaiRec and Yelp datasets. Dataset acquisition files are intentionally excluded; data/README.md documents the recognized source files and the common processed schema expected by the pipeline.
