# Multilingual Speech Language Identification

A classical machine learning project for identifying the spoken language of audio recordings using engineered acoustic features.

The project was developed as a final project for a Machine Learning course and includes both **supervised classification** and **unsupervised clustering** of multilingual speech.

## Project Overview

The dataset contains **720 approximately one-minute speech recordings** from four languages:

- German
- Italian
- Korean
- Spanish

The overall pipeline is:

1. Collect and organize multilingual speech recordings
2. Resample audio and trim silence
3. Extract fixed-length acoustic features
4. Standardize the feature representation
5. Train and evaluate supervised classifiers
6. Explore the feature space using unsupervised clustering
7. Compare model performance using quantitative metrics and visualizations

## Feature Extraction

Each audio recording is represented by **46 acoustic features**:

| Feature group | Representation | Number of features |
|---|---|---:|
| MFCC | Mean and variance of 20 MFCC coefficients | 40 |
| Spectral Centroid | Mean and variance | 2 |
| Zero Crossing Rate | Mean and variance | 2 |
| RMS Energy | Mean and variance | 2 |
| **Total** |  | **46** |

Audio is loaded at a sampling rate of **22,050 Hz**, and silence is trimmed before feature extraction.

## Supervised Classification

Five classifiers were evaluated:

- Logistic Regression
- Support Vector Machine with RBF kernel
- Multi-Layer Perceptron
- K-Nearest Neighbors
- Random Forest

The dataset was split using an **80/20 stratified train-test split**, resulting in a balanced test set of 144 recordings.

### Classification Results

| Model | Test Accuracy |
|---|---:|
| Logistic Regression | 1.00 |
| SVM (RBF Kernel) | 1.00 |
| Multi-Layer Perceptron | 1.00 |
| K-Nearest Neighbors | 1.00 |
| Random Forest | 0.99 |

Evaluation included accuracy, weighted precision, weighted recall, weighted F1-score, and confusion matrices.

## Unsupervised Clustering

Four clustering approaches were investigated:

- K-Means
- Hierarchical / Agglomerative Clustering with Ward linkage
- Gaussian Mixture Model
- DBSCAN

The clustering analysis used internal and external evaluation criteria including:

- Silhouette Score
- Adjusted Rand Index (ARI)
- Normalized Mutual Information (NMI)
- Cluster Purity
- Davies-Bouldin Index
- Calinski-Harabasz Index

PCA and t-SNE were also used to visualize the structure of the feature space.

Among the tested clustering methods, **Hierarchical Clustering with Ward linkage** produced the strongest overall alignment with the true language labels.

## Repository Structure

```text
.
├── README.md
├── notebooks/
│   ├── README.md
│   ├── 01_Data_Cleaning_and_Feature_Extraction.ipynb
│   ├── 02_Classification.ipynb
│   ├── 03_Clustering.ipynb
│   └── 04_Evaluation.ipynb
├── data/
    ├──README.md
    └──Dataset.csv
├── report/
│   └── Report.pdf
└── results/
    └── figures/
```

> The raw audio dataset is intentionally **not included** in this public repository. See [`data/README.md`](data/README.md) for details.

## Notebooks

The notebooks are intended to be read and executed in the following order:

1. [`01_Data_Cleaning_and_Feature_Extraction.ipynb`](notebooks/01_Data_Cleaning_and_Feature_Extraction.ipynb)  
   Loads the audio recordings, trims silence, extracts the 46-dimensional feature representation, and creates the tabular dataset used by the remaining notebooks.

2. [`02_Classification.ipynb`](notebooks/02_Classification.ipynb)  
   Trains and evaluates the supervised classification models.

3. [`03_Clustering.ipynb`](notebooks/03_Clustering.ipynb)  
   Explores the feature space using K-Means, hierarchical clustering, GMM, and DBSCAN, together with PCA and t-SNE visualizations.

4. [`04_Evaluation.ipynb`](notebooks/04_Evaluation.ipynb)  
   Produces the final model comparisons, evaluation metrics, confusion matrices, and clustering summaries used in the project report.

More details are available in [`notebooks/README.md`](notebooks/README.md).

## Running the Project

The notebooks use Python and the following main libraries:

- NumPy
- pandas
- librosa
- Matplotlib
- seaborn
- scikit-learn
- SciPy
- kneed
- Jupyter

A basic environment can be created with:

```bash
python -m venv .venv
source .venv/bin/activate
pip install numpy pandas librosa matplotlib seaborn scikit-learn scipy kneed jupyter
```

Run the feature-extraction notebook to generate `Dataset.csv`.

After that, the classification, clustering, and evaluation notebooks can be run using the generated feature dataset.

## Report

The complete report contains the methodology, model descriptions, figures, results, and discussion:

**[View the full project report](report/Report.pdf)**

## Authors

- Mohammadhossein Altafi
- Fateme Roshani
