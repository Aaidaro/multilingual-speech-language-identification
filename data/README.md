# Dataset

## Dataset Summary

The final project dataset contains **720 approximately one-minute speech recordings** across four languages:

- German
- Italian
- Korean
- Spanish

The recordings were collected during the data-collection phase of the course project and were later used for feature extraction, classification, and clustering.

The raw audio files are intentionally excluded from this repository.

## Expected Local Dataset Structure

The feature-extraction notebook searches for language directories and, within each language, `Male` and `Female` subdirectories.

A compatible local structure is:

```text
Dataset/
├── German/
│   ├── Male/
│   │   └── *.mp3
│   └── Female/
│       └── *.mp3
├── Italian/
│   ├── Male/
│   │   └── *.mp3
│   └── Female/
│       └── *.mp3
├── Korean/
│   ├── Male/
│   │   └── *.mp3
│   └── Female/
│       └── *.mp3
└── Spanish/
    ├── Male/
    │   └── *.mp3
    └── Female/
        └── *.mp3
```

The preprocessing notebook determines the language label from the top-level language directory.

## Feature Dataset

Running:

```text
notebooks/01_Data_Cleaning_and_Feature_Extraction.ipynb
```

produces a tabular dataset named:

```text
Dataset.csv
```

For each recording, the feature vector contains **46 acoustic features**:

- 20 MFCC means
- 20 MFCC variances
- Spectral centroid mean and variance
- Zero Crossing Rate mean and variance
- RMS energy mean and variance

The language label is stored alongside the extracted features and is used by the supervised evaluation notebooks.

## Reproducing the Dataset Locally

1. Obtain or prepare the required audio recordings separately.
2. Organize them using the directory structure shown above.
3. Make sure the notebook can access the local `Dataset/` directory.
4. Run `01_Data_Cleaning_and_Feature_Extraction.ipynb`.
5. The notebook will generate `Dataset.csv`.
6. Use that file with the classification, clustering, and evaluation notebooks.

