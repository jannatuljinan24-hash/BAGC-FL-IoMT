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

## Main Experimental Setup

The binary DL and FL experiments use a common 72/8/20 protocol:

- 72% training
- 8% validation
- 20% final held-out test
- Random seed: 42
- Number of FL clients: 5
- Communication rounds: 20
- Main FL architecture: CNN-LSTM-ResNet
- Final binary decision threshold: 0.50


### Final FL Methods

- **E0 — FedAvg:** standard binary cross-entropy with FedAvg aggregation.
- **E1 — Balanced FedAvg:** globally weighted binary cross-entropy with FedAvg.
- **E2 — BAGC-FL (Proposed):** standard binary cross-entropy with FedAvg and server-side Benign-Anchor Gradient Correction.

The internal artifact name `E2_AnchorFedAvg` is kept in the notebook for reproducibility, while `E2_BAGC_FL` is used as the reporting name.

## Recommended Environment

I developed and ran these notebooks in **Google Colab** with Google Drive mounted.

A GPU runtime is recommended for the DL and FL notebooks because the dataset and models are large. The notebooks also contain memory-saving and resume-related logic for long runs.

## Folder and Google Drive Paths

The notebooks were originally run with the following main Google Drive locations:

```text
/content/drive/MyDrive/cybersecurity-2024
/content/drive/MyDrive/IoMT_Thesis_2024
```

The ML notebooks read the original CSV files from the `cybersecurity-2024` folder.

The DL and FL notebooks mainly use:

```text
/content/drive/MyDrive/IoMT_Thesis_2024
```

If another user wants to run the notebooks, the Google Drive paths should be changed to match that user's own Drive structure.

## Important Shared Files

The binary DL notebook creates or uses the shared preprocessing files required by the FL experiments:

```text
dl_train_full.csv
dl_test_full.csv

binary_dl_preprocessed/
├── StandardScaler.joblib
├── feature_names.npy
├── validation_indices.npy
└── protocol_manifest.json
```

The FL baseline notebook prepares the Non-IID client partition used in the final BAGC-FL experiment.

Because of these dependencies, the proposed BAGC-FL notebook should not be treated as a completely independent notebook when starting from the raw dataset.

## Recommended Execution Order

For the full research workflow, I recommend the following order:

```text
01_ML_Binary_Classification.ipynb
02_ML_Multiclass_Classification.ipynb

03_DL_Binary_Classification.ipynb
04_DL_Multiclass_Classification.ipynb

05_FL_Baselines_IID_NonIID.ipynb
06_BAGC_FL_Proposed_Method.ipynb
```

The two ML notebooks are supporting benchmark experiments and can be run independently.

For reproducing the main BAGC-FL workflow from the required intermediate files, the important sequence is:

```text
03_DL_Binary_Classification.ipynb
        ↓
05_FL_Baselines_IID_NonIID.ipynb
        ↓
06_BAGC_FL_Proposed_Method.ipynb
```

`03_DL_Binary_Classification.ipynb` prepares the common binary preprocessing protocol.  
`05_FL_Baselines_IID_NonIID.ipynb` prepares and evaluates the FL baseline setup and the required client partitions.  
`06_BAGC_FL_Proposed_Method.ipynb` performs the final E0-E2 comparison and proposed BAGC-FL evaluation.

## Installation

The notebooks are intended mainly for Google Colab.

If the repository is cloned into a Python environment, the required Python packages are listed in `requirements.txt`.

Example:

```bash
pip install -r requirements.txt
```

Google Colab already provides many of the core packages. Some optional analysis packages such as SHAP or LIME may need to be installed depending on the runtime. Some notebook cells also check or install these packages when needed.

## Dataset

The raw dataset is not included in this GitHub repository because of its size.

To reproduce the experiments, place the required CSV files in the expected Google Drive folder or update the path variables in the notebooks.

The code expects the target information used in the experiments to be available in the dataset, including the binary `Label` field and, for multiclass ML experiments, the `Attack Name` field.

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

## Notes on Reproducibility

The final BAGC-FL notebook uses a fixed random seed and checks the preprocessing protocol and required source artifacts before training or evaluation.

The final E0-E2 study uses the same experimental conditions for the compared methods and evaluates them on the same frozen test set.

The notebooks also contain checks for missing files, inconsistent feature order, invalid partitions, incomplete rounds, and previously completed runs.

## Repository Use

This repository was prepared as the source-code submission for my thesis defense. The notebooks are kept close to the versions used for the thesis experiments so that the original experimental workflow and saved results remain traceable.
