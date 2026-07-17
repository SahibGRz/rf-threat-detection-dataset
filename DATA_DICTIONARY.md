# Data Dictionary

## Dataset file

```text
data/rf_dataset.csv
```

## Dataset dimensions

| Property | Value |
|---|---:|
| Rows | 450 |
| Columns | 4 |
| Input features | 3 |
| Target columns | 1 |
| Missing values | 0 |
| Exact duplicate rows | 0 |

## Column definitions

### `CN0`

| Property | Description |
|---|---|
| Data type | Floating-point number |
| Role | Input feature |
| Observed minimum | 0.158704 |
| Observed maximum | 49.906890 |
| Missing values | 0 |
| Required clarification | The authors must confirm the complete technical definition, calculation method, and unit used in the simulation. |

**Publication note:** Do not automatically describe this variable as carrier-to-noise-density ratio or assign a unit unless that interpretation matches the original simulation and research paper.

### `PDR`

| Property | Description |
|---|---|
| Data type | Floating-point number |
| Role | Input feature |
| Observed minimum | 0.005785 |
| Observed maximum | 0.998689 |
| Missing values | 0 |
| Required clarification | The authors must confirm the complete technical definition and whether the values represent a fraction, percentage, probability, or another measurement. |

**Publication note:** If `PDR` means packet delivery ratio in the original study, document the calculation formula and state whether values are recorded from `0` to `1` or from `0%` to `100%`.

### `JSR`

| Property | Description |
|---|---|
| Data type | Floating-point number |
| Role | Input feature |
| Observed minimum | -19.824755 |
| Observed maximum | 19.942163 |
| Missing values | 0 |
| Required clarification | The authors must confirm the complete technical definition, sign convention, calculation method, and unit used in the simulation. |

**Publication note:** Do not automatically assign a decibel unit unless that unit matches the original simulation and research paper.

### `Label`

| Property | Description |
|---|---|
| Data type | Integer |
| Role | Target class |
| Allowed values | `0`, `1`, `2` |
| Missing values | 0 |

## Label definitions

| Label | Class | Definition |
|---:|---|---|
| `0` | Normal signal | A simulated RF observation representing normal signal behaviour without a simulated jamming or spoofing threat. |
| `1` | Jamming signal | A simulated RF observation representing a jamming condition in the study's simulation. |
| `2` | Spoofing signal | A simulated RF observation representing a spoofing condition in the study's simulation. |

## Class distribution

| Label | Class | Observations | Percentage |
|---:|---|---:|---:|
| `0` | Normal signal | 150 | 33.33% |
| `1` | Jamming signal | 150 | 33.33% |
| `2` | Spoofing signal | 150 | 33.33% |
|  | **Total** | **450** | **100.00%** |

## Observed feature ranges by class

Values below describe the uploaded dataset and are rounded to six decimal places.

| Class | CN0 minimum | CN0 maximum | PDR minimum | PDR maximum | JSR minimum | JSR maximum |
|---|---:|---:|---:|---:|---:|---:|
| Normal signal (`0`) | 38.057128 | 44.898172 | 0.802919 | 0.998689 | -19.824755 | -5.184411 |
| Jamming signal (`1`) | 0.158704 | 24.843188 | 0.005785 | 0.499620 | 5.030414 | 19.942163 |
| Spoofing signal (`2`) | 40.035414 | 49.906890 | 0.601185 | 0.899657 | -4.794136 | 9.939737 |

## Row ordering

The original file is ordered by target class:

| Row range, excluding header | Label | Class |
|---|---:|---|
| 1–150 | `0` | Normal signal |
| 151–300 | `1` | Jamming signal |
| 301–450 | `2` | Spoofing signal |

The dataset should be shuffled before model splitting. The random seed and splitting method should be reported in any associated experiment.

## Data-quality checks

| Check | Result |
|---|---|
| Missing values | None found |
| Exact duplicate rows | None found |
| Invalid label values | None found |
| Non-numeric values in feature columns | None found |
| Class imbalance | None; all three classes contain 150 observations |
| Obvious personal identifiers | None found |

## Precision

The original feature values contain many decimal places because they were generated computationally. This precision should not be described as physical measurement precision unless the data were generated from or validated against equipment with corresponding accuracy.

The unmodified original values should be retained for reproducibility. A rounded derivative file may be added separately, but it must be clearly named and documented.

## Interpretation warning

The three classes occupy strongly separated feature ranges. Consequently, very high classification performance may partly reflect the simulation rules rather than the ability of a model to generalise to complex real-world RF conditions.

Researchers should report this limitation and, where possible, evaluate future models using:

- Overlapping class ranges
- Borderline observations
- Additional noise
- Different RF environments
- Multiple simulation seeds
- Independently generated test data
- Real or hardware-in-the-loop validation

## Required author-supplied metadata

Before final publication, replace or complete the following items:

- Full technical meaning of `CN0`
- Unit of `CN0`
- Full technical meaning of `PDR`
- Calculation method for `PDR`
- Full technical meaning of `JSR`
- Unit and sign convention of `JSR`
- Simulation software
- Simulation equations or rules
- Parameter distributions
- Noise model
- Random seed
- Preprocessing method
- Exact dataset split used in the paper
- Dataset-generation date
- Dataset author or authors
- Associated paper title
- Dataset licence
- Permanent DOI, when available

## Machine-readable schema

```yaml
dataset:
  file: data/rf_dataset.csv
  rows: 450
  columns: 4
  origin: simulated
  task: multiclass classification

features:
  CN0:
    type: float
    unit: to_be_confirmed
  PDR:
    type: float
    unit: to_be_confirmed
  JSR:
    type: float
    unit: to_be_confirmed

target:
  Label:
    type: integer
    classes:
      0: normal_signal
      1: jamming_signal
      2: spoofing_signal
```
