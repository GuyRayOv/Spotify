# 🎯 Machine Learning Pipeline Project

This repository contains a complete, modular **machine learning pipeline**, developed using Kaggle's Spotify dataset.  
The original dataset documentation by Kaggles is available at: `{REPOSITORY_PATH}/data/README.md`

---

## 📘 Project Overview

The project implements all major stages of a **supervised machine learning workflow**, including:

1. **Data Preparation** – loading, cleaning, and structuring the raw dataset.  
2. **Exploratory Data Analysis (EDA)** – statistical summaries, visualization, and feature insights.  
3. **Data Cleansing** – outlier detection and imputation of missing values.  
4. **Feature Engineering & Selection** – feature transformation, encoding, and importance ranking.  
5. **Model Selection & Hyperparameter Optimization** – model evaluation and tuning using Grid Search.

Each stage is implemented in a dedicated **Jupyter notebook (.ipynb)** to ensure modularity, clarity, and reproducibility.

---

🧩 Project Structure
```
{REPOSITORY_PATH}/
│
├── data/
│   ├── README.md                # Kaggle dataset description
│   └── Spotify Dataset.pptx     # Project presentation with visualizations
│
├── notebooks/
│   ├── 1_spotify_dataprep.ipynb
│   ├── 2_spotify_eda.ipynb
│   ├── 3_spotify_datacleansing.ipynb
│   ├── 4_spotify_fe.ipynb
│   └── 5_spotify_models.ipynb
│
├── src/
│   ├── config.json              # Global project configuration file
│   ├── utils.py                 # Helper functions (shared across notebooks)
│   └── __init__.py
│
├── output/                      # Logs, results, and generated files
├── pickles/                     # Serialized models and data
│
├── requirements.txt             # Python dependencies
├── README.md                    # Project documentation (this file)
└── .gitignore                   # Ignored files and folders
```

---

## ⚙️ Notebook Workflow

Notebooks are **cascading each other** — Notebook *N* executes notebook *N-1* first and loads its serialized output (`N-1.pkl`). 
Notebook '(REPOSITORY_PATH}/notebooks/1_spotify_dataprep.ipynb' starts its execution by downloading the Spotify dataset from Kaggle's webseite.
Each stage can also be run independently. This behavior is controlled via the `chain_df` flag in `config.json`.

A centralized configuration file —  `{REPOSITORY_PATH}/src/config.json` — defines all global parameters, including:
- File paths
- Execution order  
- Algorithms for outlier detection, imputation, and modeling  
- Pipeline control flags (e.g., `split_df`, `chain_notebooks`)

---

## 🧠 Data Leakage Prevention

To ensure robust evaluation and prevent data leakage, the Kaggle dataset is split into two independent subsets:

- **Training DataFrame:** `df`  
- **Testing DataFrame:** `df_test`

Both are processed independently through the pipeline. This behavior is controlled via the `split_df` flag in `config.json`.

---

## 🚀 How to Run

1. **Clone** this repository to your local machine.  
2. Create `.env` file in the root directory of the Runtime, e.g. `/contect/.env`
3. In `.env` define `PROJECT_PATH` to match your local copy. e.g. `PROJECT_PATH=/content/drive/MyDrive/Projects/GitHub/Spotify/`
4. In `{REPOSITORY_PATH}/src/config.json`, If `chain_notebooks : 1`, the entire pipline will be executed. Or `0` for a run of a sinlge notebook.
5. Open `{REPOSITORY_PATH}/notebooks/5_spotify_models.ipynb`, for an execution of the entire pipline. Or any notebook for a partial run.
7. Click **Run All**.

---

## 📊 Project Deliverables

- **Jupyter Notebooks** – one per ML pipeline stage → `{REPOSITORY_PATH}/notebooks/`  
- **Configuration File** – centralized global parameters → `{REPOSITORY_PATH}/src/config.json`  
- **Presentation Deck** – key insights and visualizations → `{REPOSITORY_PATH}/data/Spotify Dataset.pptx`

---
