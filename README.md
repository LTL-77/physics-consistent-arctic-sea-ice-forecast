[中文版 README](README_zh.md)

# Physics-Consistent Lightweight Deep Learning for Seasonal Prediction of Arctic Sea Ice Concentration (1–6 Months)

This repository provides a reproducible **Jupyter + Python** data science project for
**seasonal prediction of Arctic Sea Ice Concentration (SIC)** with lead times of **1–6 months**.

The core objective of this project is to develop a **physics-consistent and lightweight deep learning framework** under **limited computational resources**, achieving competitive predictive performance while improving **physical realism, stability, and reproducibility**.

---

## Core Ideas

* Design a **lightweight model architecture** suitable for **compute-constrained environments**, avoiding reliance on large-scale networks and high-end hardware
* Explicitly incorporate **key physical variables** to enhance physical constraints in seasonal prediction
* Apply **season-aware temporal modeling**, with special emphasis on the **spring transition period**, to mitigate the *Spring Predictability Barrier*
* Introduce **physics-consistent regularization** in the loss function, including spatial continuity and temporal smoothness constraints

---

## Key Features

* **Physics-informed input variables**
  Sea ice concentration (SIC) combined with key physical factors such as sea ice thickness (or its proxy) and near-surface air temperature anomalies

* **Season-aware temporal modeling module**

  * *Winter stable phase*: background states are compressed via temporal aggregation
  * *Spring transition phase*: lightweight temporal units are used to explicitly model rapid evolution

* **Physics-consistent loss function**
  Regularization terms are introduced to suppress non-physical spatial discontinuities and abrupt temporal fluctuations

* **Lightweight and reproducible design**
  The model architecture is compact, with low training and inference cost, suitable for single-GPU or resource-limited environments

---

## Data Sources

### Primary Data Source (Recommended, consistent with the paper setup)

* **Sea Ice Concentration (SIC)**

  * Provider: NSIDC
  * Product type: Passive microwave sea ice concentration products
  * Example product: NSIDC-0051 (and other long-term SIC records)

### Physics-informed Input Variables (Recommended)

* **Sea Ice Thickness (SIT) or proxy**

  * Source: PIOMAS (or other reanalysis / reconstruction datasets)

* **Near-surface air temperature anomaly (SAT anomaly)**

  * Source: ERA5 reanalysis

### Optional Data Source (for cross-validation)

* **OSI SAF Sea Ice Concentration products (CDR / ICDR)**
  Useful for testing model robustness and generalization across different SIC products

> ⚠️ Each dataset has its own license and access requirements. Please consult the official documentation before use.

---

## Repository Structure

```text
├── notebooks/      # Step-by-step Jupyter workflows (download → preprocessing → training → evaluation)
├── src/            # Reusable code modules (dataset / model / loss / train / utils)
├── experiments/    # Experiment configurations and results
├── figures/        # Automatically generated figures and spatial visualizations
└── requirements.txt
```

---

## Quick Start

### 1️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

---

### 2️⃣ Run Jupyter notebooks in order

```text
01_data_download.ipynb
02_preprocessing.ipynb
04_baselines.ipynb
05_physics_consistent_model.ipynb
```

These notebooks cover data acquisition, preprocessing, baseline experiments, and training of the physics-consistent model.

---

### 3️⃣ Train the model (script-based)

```bash
python -m src.train --config experiments/configs/base.yaml
```

---

## Baseline Methods

* Climatology
* Persistence
* Linear regression
* Lightweight U-Net (optional, for deep learning comparison)

---

## Evaluation Metrics

* **RMSE / MAE**
  Computed over valid Arctic ice–ocean grid cells to assess overall prediction error

* **Spatial pattern analysis**
  Focus on spatial consistency, especially in marginal ice zones and representative seasonal cases

---

## Citation

If you use the code, workflow, or experimental design from this repository in your research or applications, please cite the corresponding paper or technical report.

---

## Acknowledgements

We acknowledge the following institutions and projects for providing high-quality open datasets:

* NSIDC
* ERA5
* PIOMAS
* OSI SAF
