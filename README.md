Machine Learning Pipeline Project

This repository contains a complete, modular machine learning pipeline, developed using a Kaggle dataset. The original dataset documentation is available at:
{REPOSITORY_PATH}/data/README.md

📘 Project Overview
The project implements all major stages of a supervised machine learning workflow, including:

1) Data Preparation – loading, cleaning, and structuring the raw dataset.
2) Exploratory Data Analysis (EDA) – statistical summaries, visualization, and feature insights.
3) Data Cleansing – outlier detection and imputation of missing values.
4) Feature Engineering & Selection – feature transformation, encoding, and importance ranking.
5) Model Selection & Hyperparameter Optimization – model evaluation and tuning using Grid Search.

Each stage is implemented in a dedicated Jupyter notebook (.ipynb) to ensure modularity, clarity, and reproducibility.

🧩 Project Structure
{REPOSITORY_PATH}/
│
├── data/
│   ├── README.md                # Kaggle dataset description
│   └── Spotify Dataset.pptx     # Project presentation with visualizations
│
├── notebooks/
│   ├── 1_spotiy_dataprep.ipynb
│   ├── 2_spotify_eda.ipynb
│   ├── 3_spotify_datacleansing.ipynb
│   ├── 4_spotify_fe.ipynb
│   ├── 5_spotify_models.ipynb
│
├── src/
│   ├── config.json              # Global configuration file
│   ├── utils.py                 # Helper functions (optional)
│   └── __init__.py
│
├── output/                      # Executed notebooks and logs
├── pickles/                     # Executed notebooks and logs
|
├── requirements.txt             # Python dependencies
├── README.md                    # Project documentation (this file)
└── .gitignore                   # Ignored files and folders

⚙️ Notebook Workflow

The notebooks are executed sequentially, where:

Notebook N loads the serialized output (.pkl) from N−1.

Notebook N processes and exports data for N+1.

Each stage can be re-run independently, promoting flexibility and reproducibility.

A centralized configuration file {PROJECT_PATH}/src/config.json defines all global parameters, including:

File paths and execution order

Algorithms for outlier detection, imputation, and modeling

Grid search and model parameters

Pipeline control flags (e.g., "split_df")

🧠 Data Leakage Prevention

To ensure robust evaluation and prevent data leakage, the dataset is split into two independent subsets:

Training DataFrame (df)

Testing DataFrame (df_test)

Both are processed independently through the pipeline.
This behavior is controlled via the "split_df" flag in config.json.

🚀 How to Run
1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

2. Set up the environment
python -m venv venv
source venv/bin/activate     # On Windows: venv\Scripts\activate
pip install -r requirements.txt

3. Configure parameters

Edit {PROJECT_PATH}/src/config.json to define:

Input/output paths

Algorithms and model parameters

Split control ("split_df")

4. Execute the pipeline

Run notebooks manually (Jupyter/VS Code) or automatically with Papermill:

papermill notebooks/1_data_prep.ipynb notebooks/output/1_data_prep_output.ipynb
papermill notebooks/2_eda.ipynb notebooks/output/2_eda_output.ipynb
papermill notebooks/3_cleansing.ipynb notebooks/output/3_cleansing_output.ipynb
papermill notebooks/4_feature_engineering.ipynb notebooks/output/4_feature_engineering_output.ipynb
papermill notebooks/5_model_selection.ipynb notebooks/output/5_model_selection_output.ipynb

📊 Project Deliverables

Jupyter Notebooks – one per ML pipeline stage

Configuration File – centralized global parameters

Serialized Files (.pkl) – intermediate artifacts for reproducibility

Presentation Deck – key insights and visualizations:
{PROJECT_PATH}/data/Spotify Dataset.pptx

🧠 Key Libraries

Developed using Python 3.x and the following main dependencies:

pandas
numpy
matplotlib
seaborn
scikit-learn
joblib
papermill


(Full dependency list available in requirements.txt.)
