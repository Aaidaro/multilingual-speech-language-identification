# Notebooks

This directory contains the Jupyter notebooks used for the machine learning pipeline.

### 1. `01_Data_Cleaning_and_Feature_Extraction.ipynb`

**Purpose:** Convert raw multilingual speech recordings into a fixed-length numerical dataset.

Main steps:

- Discover `.mp3` files from the local dataset directory
- Load audio using `librosa`
- Resample recordings to 22,050 Hz
- Trim low-energy silence
- Extract 20 MFCC coefficients
- Compute the mean and variance of each MFCC
- Extract spectral centroid statistics
- Extract zero-crossing-rate statistics
- Extract RMS-energy statistics
- Combine the features into a 46-dimensional vector
- Save the resulting feature table as `Dataset.csv`

**Input:** Local audio dataset  
**Output:** `Dataset.csv`

---

### 2. `02_Classification.ipynb`

**Purpose:** Train supervised models to predict the language of each recording.

Models:

- Logistic Regression
- Support Vector Machine with RBF kernel
- Random Forest
- K-Nearest Neighbors
- Multi-Layer Perceptron

Main steps:

- Load `Dataset.csv`
- Split the dataset into training and test subsets
- Standardize numerical features
- Train the classifiers
- Generate predictions
- Evaluate classification performance

The project uses an 80/20 stratified train-test split.

---

### 3. `03_Clustering.ipynb`

**Purpose:** Investigate whether the extracted speech features naturally form meaningful groups without using language labels during model fitting.

Methods:

- K-Means
- Agglomerative / Hierarchical Clustering
- Gaussian Mixture Model
- DBSCAN

Analysis includes:

- Standardization
- PCA
- t-SNE
- Elbow analysis
- Silhouette Score
- Calinski-Harabasz Index
- Davies-Bouldin Index
- Adjusted Rand Index
- Normalized Mutual Information
- Dendrograms
- Cluster composition visualizations

The notebook evaluates multiple cluster configurations before selecting representative settings for comparison.

---

### 4. `04_Evaluation.ipynb`

**Purpose:** Produce the final evaluation and comparison used in the project report.

This notebook brings together the supervised and unsupervised results and includes:

- Classification accuracy
- Weighted precision
- Weighted recall
- Weighted F1-score
- Confusion matrices
- Cluster purity
- ARI
- NMI
- Silhouette scores
- Model-comparison plots

## Data Dependency

To reproduce the full workflow:

1. Run `Data_Cleaning_and_Feature_Extraction.ipynb`.
2. Confirm that `Dataset.csv` has been generated.
3. Run the remaining notebooks.

## Python Dependencies

The notebooks use the following primary packages:

```text
numpy
pandas
librosa
matplotlib
seaborn
scikit-learn
scipy
kneed
jupyter
```

You can install them with:

```bash
pip install numpy pandas librosa matplotlib seaborn scikit-learn scipy kneed jupyter
```

## Reproducibility Notes

Some of the models and dimensionality-reduction procedures use fixed random seeds to improve reproducibility.

Exact numerical results can still depend on package versions, platform differences, and the local copy of the dataset.

## Report

For the full explanation of the methodology and results, see:

[`../report/Phase_2_Report.pdf`](../report/Report.pdf)
