# M115 Lab 2: Static Malware Detection

`M115_Lab2_Template.ipynb` is the student template for Lab 2 of Module M115 (AI & Intelligent Systems) at ENSIASD Taroudant. You build and evaluate a detector for Windows PE files, then turn its scores into a recommendation for the CISO of AtlasPay, a fictional payment-services company.

The notebook generates its own data: 6,000 synthetic, EMBER-inspired PE-file records. AtlasPay, the costs and the operating figures are teaching assumptions, so results are not evidence of production performance.

## Requirements

- Python 3 with Jupyter support (in VS Code, the Python and Jupyter extensions)
- `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `shap`
- `lightgbm` (optional): if it is missing, use `HistGradientBoostingClassifier` and label it as such

```bash
pip install numpy pandas matplotlib scikit-learn shap lightgbm
```

## Notebook structure

| Section | Work to complete |
|---|---|
| Phase 0: Environment and dataset | Run the supplied setup and data-generation cells |
| Phase 1: Forensic data audit | Check data quality, handle the `99999.0` parser value, remove the identifier and the leaking post-scan field |
| Phase 2: Leakage-safe evaluation | Make a stratified 80/20 split, build pipelines, compare models with 5-fold CV, measure latency |
| Phase 3: Error forensics | Verify a real model disagreement and explain it with TreeSHAP |
| Phase 4: SOC decision | Select cost-based thresholds on out-of-fold predictions, then evaluate once on the test set |
| Phase 5: CISO recommendation | Write about one page on the model, threshold, deployment mode and risks |

## How to use it

1. Open the notebook in VS Code and select a Python kernel.
2. Run the cells in order and complete each `# TODO`.
3. Keep `SEED = 42` and do not change the data generator.

## Rules to respect

- Do not use `SHA256_File_ID` or `VT_PostScan_Detections` as input features.
- Fit imputers and scalers inside the cross-validation pipeline.
- Treat the test set as a lockbox: never use it to select models or tune thresholds.
- Report the outputs you actually obtained, and do not present synthetic patterns as universal malware signatures.

The full requirements and deliverables are in `M115_Lab2_AssignmentSheet.pdf`.
