# Simulated RF Threat Detection Dataset

## Overview

This repository contains a simulated radio-frequency (RF) dataset created for a machine-learning study on the detection and classification of RF signal threats.

The dataset contains three classes:

- `0` — Normal signal
- `1` — Jamming signal
- `2` — Spoofing signal

The data are synthetic and were generated through simulation. They are not measurements collected from a live RF system or operational communication network.

## Repository contents

```text
rf-threat-detection-dataset/
├── data/
│   └── rf_dataset.csv
├── README.md
├── DATA_DICTIONARY.md
├── LICENSE
└── CITATION.cff
```

At present, the primary research dataset is provided as one CSV file:

- `data/rf_dataset.csv`

## Dataset summary

| Item | Value |
|---|---:|
| Total observations | 450 |
| Total input features | 3 |
| Target column | `Label` |
| Number of classes | 3 |
| Missing values | 0 |
| Exact duplicate rows | 0 |
| Normal-signal observations | 150 |
| Jamming-signal observations | 150 |
| Spoofing-signal observations | 150 |

The classes are evenly balanced, with 150 observations in each class.

## Columns

The CSV contains the following columns:

| Column | Type | Role |
|---|---|---|
| `CN0` | Floating-point number | Input feature |
| `PDR` | Floating-point number | Input feature |
| `JSR` | Floating-point number | Input feature |
| `Label` | Integer | Target class |

Full column definitions, observed ranges, and class mappings are provided in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).

## Label mapping

| Label | Class |
|---:|---|
| `0` | Normal signal |
| `1` | Jamming signal |
| `2` | Spoofing signal |

## Data origin

The dataset was generated using simulated RF-feature values for normal, jamming, and spoofing conditions.

Before publication, the authors should add the exact simulation details used in the research, including:

- Software or programming language used
- Feature-generation equations or rules
- Probability distributions
- Parameter ranges
- Noise assumptions
- Random seed
- Number of generated samples
- Class-balancing method
- Preprocessing steps
- Any filtering or removal of generated observations

Do not describe this dataset as real-world experimental RF data unless physical measurements were genuinely used.

## Important dataset characteristic

The rows in the current CSV are grouped by class:

- Rows 1–150: normal signals
- Rows 151–300: jamming signals
- Rows 301–450: spoofing signals

Users should shuffle the dataset before creating training, validation, and test subsets. A fixed random seed should be used and reported to support reproducibility.

### Example split in Python

```python
import pandas as pd
from sklearn.model_selection import train_test_split

data = pd.read_csv("data/rf_dataset.csv")

X = data[["CN0", "PDR", "JSR"]]
y = data["Label"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y,
)
```

This example is provided only as a reproducible splitting method. The paper should report the exact split, random seed, and preprocessing procedure actually used in the study.

## Intended use

The dataset is intended for:

- Academic research
- Defensive RF-threat detection
- Machine-learning classification experiments
- Reproducibility and comparison studies
- Educational analysis of simulated RF conditions

## Out-of-scope use

This dataset is not intended to provide operational instructions for disrupting, interfering with, imitating, or manipulating real communication systems.

## Limitations

Users should consider the following limitations:

1. The dataset is simulated rather than collected from real RF hardware.
2. Each class contains the same number of observations.
3. The current classes have strongly separated feature ranges.
4. Performance on this dataset may not represent performance in noisy, changing, or real-world RF environments.
5. The dataset does not independently establish that a trained model will generalise to unseen hardware, frequencies, environments, attack methods, or signal protocols.
6. The original dataset is supplied as one file; separate training, validation, and test files are not included.
7. The exact meanings and units of `CN0`, `PDR`, and `JSR` must be confirmed by the authors in the final repository documentation.

## Reproducibility

For a reproducible publication, the repository should state:

- Exact software versions
- Model configuration
- Hyperparameters
- Random seeds
- Preprocessing procedure
- Train/validation/test method
- Evaluation metrics
- Dataset version used in the paper

Where possible, publish the genuine code used for data generation, preprocessing, training, and evaluation. Reconstructed code should be clearly identified as reconstructed and should not be presented as the original experiment code.

## Ethical and privacy statement

The CSV contains numeric RF features and class labels only. No names, email addresses, account details, location records, or other obvious personal identifiers are included.

The dataset is intended for defensive research into RF-threat detection.

## Associated paper

**Paper title:** `[INSERT FULL PAPER TITLE]`

**Authors:** `[INSERT AUTHOR NAMES]`

**Institution:** `[INSERT UNIVERSITY OR RESEARCH INSTITUTION]`

**Publication status:** `[SUBMITTED / ACCEPTED / PUBLISHED]`

## Data availability statement

The simulated dataset supporting this study is publicly available in this repository. The dataset is provided in `data/rf_dataset.csv`, together with its class definitions, feature documentation, limitations, and version information.

After creating a permanent archive and DOI, replace the statement above with:

> The simulated dataset supporting the findings of this study is publicly available at [DATASET DOI]. The associated documentation and version history are available in the GitHub repository at [GITHUB REPOSITORY URL].

## Citation

Until a DOI is created, cite the repository using the following format:

> [Author surname], [Initials]. ([Year]). *Simulated RF Threat Detection Dataset* (Version 1.0.0) [Data set]. GitHub. [Repository URL]

After archiving a release through a research repository such as Zenodo, use the DOI-based citation generated for that archived release.

## Licence

`[INSERT SELECTED DATASET LICENCE]`

Add a `LICENSE` file before publication. Confirm that the selected licence complies with the requirements of the authors, university, funder, and target journal.

## Contact

For questions about the dataset or associated research:

- **Name:** `[INSERT CONTACT NAME]`
- **Institution:** `[INSERT INSTITUTION]`
- **Email:** `[INSERT ACADEMIC EMAIL]`

## Version history

### Version 1.0.0

- Initial public release
- 450 simulated observations
- Three RF-signal classes
- Three numerical input features
- Balanced class distribution
