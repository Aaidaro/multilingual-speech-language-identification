# Dataset

The dataset used in this project is **not included in the public GitHub repository**.

This directory contains documentation only.

## Dataset Summary

The final project dataset contains **720 approximately one-minute speech recordings** across four languages:

- German
- Italian
- Korean
- Spanish

The recordings were collected during the data-collection phase of the course project and were later used for feature extraction, classification, and clustering.

## Why the Data Is Not Included

The raw audio files are intentionally excluded from this repository.

This keeps the repository focused on the machine learning implementation and avoids redistributing source audio through the project repository.

The generated feature file, `Dataset.csv`, is also not committed to the repository. It can be reproduced locally by running the feature-extraction notebook on an available copy of the audio dataset.

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
notebooks/Data_Cleaning_and_Feature_Extraction.ipynb
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
4. Run `Data_Cleaning_and_Feature_Extraction.ipynb`.
5. The notebook will generate `Dataset.csv`.
6. Use that file with the classification, clustering, and evaluation notebooks.

If you change the local location of the dataset, update the dataset path in the feature-extraction notebook accordingly.

## Recommended `.gitignore` Entries

To prevent accidental publication of the local dataset, add entries such as the following to the repository's `.gitignore`:

```gitignore
# Local project data
Dataset/
Dataset.csv

# Raw audio
*.mp3
```

If you later store generated data in a different directory, add that location to `.gitignore` as well.

## Data Availability

The public repository contains the code, documentation, report, and project results, but **does not provide the raw audio recordings**.
