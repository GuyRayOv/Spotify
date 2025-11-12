# 🎯 Machine Learning Pipeline Project

This repository contains a complete, modular **machine learning pipeline**, developed using Kaggle's Spotify dataset.  
The original dataset documentation by Kaggles is available [here](data/README.md.md).


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
│   └── ProjectPresentation.pptx # Project presentation with visualizations
│
├── notebooks/
│   ├── 1spotify_dataprep.ipynb
│   ├── 2spotify_eda.ipynb
│   ├── 3spotify_datacleansing.ipynb
│   ├── 4spotify_fe.ipynb
│   └── 5spotify_models.ipynb
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

Notebooks are **cascading each other** — Notebook *N* executes notebook *N-1* first and loads its serialized output (*N-1.pkl*). 
The cascade ends with [notebooks/1spotify_dataprep.ipynb](notebooks/1spotify_dataprep.ipynb) `1spotify_dataprep.ipynb`, which downloads the Spotify dataset from Kaggle.
Each stage can also be run independently - this behavior is controlled with the `chain_notebooks` flag in [config.json](src/config.json), the project's configuration file that defines all global parameters. 
Including:
- File paths
- Execution order  
- Algorithms for Outlier Detection, Imputation, and Modeling  
- Pipeline control flags (e.g. `split_df` , `chain_notebooks`)

---

## 🧠 Data Leakage Prevention

To ensure robust evaluation and prevent data leakage, the Kaggle dataset is split into two independent subsets:

- **Training DataFrame:** `df`  
- **Testing DataFrame:** `df_test`

Both subsets are processed independently throughout the pipeline. This behavior is controlled via the `split_df` flag in `config.json`.

---

## 🚀 How to Run

1. **Clone** this repository to your local machine.  
2. Create `.env` file in the root directory of the Runtime, e.g. `/contect/.env`
3. In `.env` define `PROJECT_PATH` to point to your local copy. e.g. `PROJECT_PATH=/content/drive/MyDrive/Projects/GitHub/Spotify/`
4. In `.env` define your Kaggles API params: `KAGGLE_USERNAME=username` and `KAGGLE_API_KEY=apikey`   
5. Keep `chain_notebooks : 1` in  [config.json](src/config.json) for an execution of the entire pipline.
6. Open [notebooks/5_spotify_models.ipynb](notebooks/5spotify_models.ipynb), for a full execution, or any notebook for a partial run.
7. Click **Run All**

---

## 📊 Project Deliverables

- **Jupyter Notebooks**. One per ML pipeline stage under [notebooks/](notebooks/)  
- **Configuration File**. A centralized global parameters, [config.json](src/config.json)  
- **Presentation Deck**. Key insights and visualizations, `data/Project Presentation.pptx`

---
