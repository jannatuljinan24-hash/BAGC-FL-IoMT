# BAGC-FL: A New Benign-Anchor Gradient-Correction-Oriented Federated Learning Approach for Medical IoT Intrusion Detection

This repository contains the main notebooks I used during my thesis work on IoMT intrusion detection. The experiments include machine learning and deep learning benchmarks, federated learning baselines, and the final proposed BAGC-FL method.

The main focus of the thesis is the federated learning part, especially the effect of class imbalance and Non-IID client data on benign traffic detection. The proposed method, BAGC-FL, uses a server-side benign-anchor gradient correction step to reduce harmful aggregation effects on the benign class.

## Thesis Information

**Title:** BAGC-FL: A New Benign-Anchor Gradient-Correction-Oriented Federated Learning Approach for Medical IoT Intrusion Detection

**Students:**
- Jannatul Jinan — ID: UG02-61-22-012
- Jannatul Ferdouse Shifa — ID: UG02-61-22-040

**Department:** Department of Computer Science and Engineering

**University:** State University of Bangladesh

**Supervisor:** Md. Alamgir Hossain, Assistant Professor, Department of CSE

## Repository Contents

The notebooks are arranged in the same order as the main experimental workflow.

| No. | Notebook | Purpose |
|---|---|---|
| 01 | `01_ML_Binary_Classification.ipynb` | Binary machine learning benchmark. It includes multiple classifiers, evaluation metrics, statistical testing, SHAP, and LIME analysis. |
| 02 | `02_ML_Multiclass_Classification.ipynb` | Multiclass machine learning benchmark using several classifiers with evaluation, statistical testing, SHAP, and LIME analysis. |
| 03 | `03_DL_Binary_Classification.ipynb` | Binary deep learning experiments using FNN, CNN, RNN, GRU, LSTM, CNN-LSTM, and CNN-LSTM-ResNet. This notebook also creates the shared binary preprocessing artifacts used by the FL experiments. |
| 04 | `04_DL_Multiclass_Classification.ipynb` | Multiclass deep learning experiments using FNN, CNN, Simple RNN, GRU, LSTM, CNN-LSTM, and CNN-LSTM-ResNet. |
| 05 | `05_FL_Baselines_IID_NonIID.ipynb` | Federated learning baseline experiments using five clients under IID and Non-IID settings. It includes FedAvg, FedSGD, FedProx, FedAdam, and FedDyn with the common CNN-LSTM-ResNet model. |
| 06 | `06_BAGC_FL_Proposed_Method.ipynb` | Final proposed-method notebook. It compares E0 FedAvg, E1 Balanced FedAvg, and E2 BAGC-FL under both IID and Non-IID settings and also includes final evaluation, statistical comparison, SHAP, and LIME. |

### Final FL Methods

- **E0 — FedAvg:** standard binary cross-entropy with FedAvg aggregation.
- **E1 — Balanced FedAvg:** globally weighted binary cross-entropy with FedAvg.
- **E2 — BAGC-FL (Proposed):** standard binary cross-entropy with FedAvg and server-side Benign-Anchor Gradient Correction.

The internal artifact name `E2_AnchorFedAvg` is kept in the notebook for reproducibility, while `E2_BAGC_FL` is used as the reporting name.

## Dataset

The raw dataset is not included in this GitHub repository because of its size.

## Generated Outputs

Depending on the notebook, the code can generate:

- trained model files
- preprocessing artifacts
- client partition files
- result CSV files
- classification reports
- confusion matrices
- ROC and precision-recall curves
- training and validation loss figures
- statistical comparison results
- SHAP explanations
- LIME explanations

These large generated files are not required to be stored in the GitHub repository. They can be reproduced by running the notebooks with the correct dataset and paths.
