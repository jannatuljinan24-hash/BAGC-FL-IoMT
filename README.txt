BAGC-FL THESIS SOURCE CODE

Title:
BAGC-FL: A New Benign-Anchor Gradient-Correction-Oriented Federated Learning Approach for Medical IoT Intrusion Detection

Students:
Jannatul Jinan — ID: UG02-61-22-012
Jannatul Ferdouse Shifa — ID: UG02-61-22-040

Department:
Department of Computer Science and Engineering

University:
State University of Bangladesh

Supervisor:
Md. Alamgir Hossain
Assistant Professor, Department of CSE


1. ABOUT THIS SOURCE CODE

This folder contains the main notebooks I used for my thesis work on IoMT intrusion detection.

The experiments include supporting machine learning and deep learning benchmarks, federated learning baselines, and the final proposed BAGC-FL method.

The main focus of the thesis is the federated learning part. BAGC-FL was developed to reduce the effect of class imbalance and Non-IID client data on benign traffic detection by applying a server-side benign-anchor gradient correction step.


2. NOTEBOOKS

01_ML_Binary_Classification.ipynb
Binary machine learning benchmark with multiple classifiers, evaluation metrics, statistical testing, SHAP, and LIME.

02_ML_Multiclass_Classification.ipynb
Multiclass machine learning benchmark with multiple classifiers, evaluation, statistical testing, SHAP, and LIME.

03_DL_Binary_Classification.ipynb
Binary deep learning experiments using FNN, CNN, RNN, GRU, LSTM, CNN-LSTM, and CNN-LSTM-ResNet.
This notebook also creates the shared binary preprocessing files required by the FL experiments.

04_DL_Multiclass_Classification.ipynb
Multiclass deep learning experiments using FNN, CNN, Simple RNN, GRU, LSTM, CNN-LSTM, and CNN-LSTM-ResNet.

05_FL_Baselines_IID_NonIID.ipynb
Federated learning baseline experiments using five clients under IID and Non-IID settings.
The notebook includes FedAvg, FedSGD, FedProx, FedAdam, and FedDyn with the common CNN-LSTM-ResNet model.

06_BAGC_FL_Proposed_Method.ipynb
Final proposed-method notebook.
It compares:
E0 - FedAvg
E1 - Balanced FedAvg
E2 - BAGC-FL (Proposed)

Both IID and Non-IID settings are evaluated. The notebook also includes final evaluation, statistical comparison, SHAP, and LIME.


3. MAIN EXPERIMENTAL SETTINGS

Binary DL/FL data protocol:
72% training
8% validation
20% final test

Random seed: 42
FL clients: 5
Communication rounds: 20
Main FL model: CNN-LSTM-ResNet
Final binary threshold: 0.50


4. RECOMMENDED ENVIRONMENT

The notebooks were developed and run in Google Colab.

Google Drive is used to store the dataset, preprocessing files, trained models, checkpoints, result files, and figures.

A GPU runtime is recommended for the deep learning and federated learning notebooks.


5. ORIGINAL GOOGLE DRIVE PATHS

The notebooks mainly use these locations:

/content/drive/MyDrive/cybersecurity-2024
/content/drive/MyDrive/IoMT_Thesis_2024

If the notebooks are run from another Google Drive account, these paths should be changed to match the new folder location.


6. IMPORTANT SHARED FILES

The binary DL notebook creates or uses the following shared files:

dl_train_full.csv
dl_test_full.csv

binary_dl_preprocessed/StandardScaler.joblib
binary_dl_preprocessed/feature_names.npy
binary_dl_preprocessed/validation_indices.npy
binary_dl_preprocessed/protocol_manifest.json

The FL baseline notebook prepares the Non-IID client partition used in the final BAGC-FL experiment.


7. RECOMMENDED RUNNING ORDER

The ML notebooks are supporting benchmark experiments and can be run independently.

For the main BAGC-FL workflow, the important order is:

03_DL_Binary_Classification.ipynb
then
05_FL_Baselines_IID_NonIID.ipynb
then
06_BAGC_FL_Proposed_Method.ipynb

The binary DL notebook prepares the common preprocessing protocol.
The FL baseline notebook prepares and evaluates the FL setup and required partitions.
The BAGC-FL notebook performs the final E0-E2 comparison.


8. INSTALLATION

The required Python packages are listed in requirements.txt.

For a normal Python environment:

pip install -r requirements.txt

In Google Colab, many of the required packages are already installed. Some packages such as SHAP or LIME may need to be installed depending on the runtime.


9. DATASET

The raw dataset is not included in this source-code package because of its size.

The user should place the required CSV files in the correct Google Drive folder or update the dataset path in the notebooks.

The experiments use the Label field for binary classification and the Attack Name field where multiclass attack labels are required.


10. OUTPUTS

The notebooks can produce trained models, preprocessing files, client partitions, result CSV files, classification reports, confusion matrices, ROC/PR curves, training/validation loss figures, statistical test results, SHAP explanations, and LIME explanations.

Large generated model and dataset files are not included in the GitHub repository.


11. REPRODUCIBILITY NOTE

The final BAGC-FL notebook uses a fixed random seed and checks the preprocessing protocol and required source files.

E0, E1, and E2 are evaluated under the same experimental conditions and on the same frozen final test set.

The source notebooks are kept close to the versions used for the thesis experiments so that the original workflow and results remain traceable.
