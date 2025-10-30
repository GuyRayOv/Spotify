# Spotify

This is an ML project based on Kaggle's dataset. Kaggle's readme file in avaialbe here {PROJECT_PATH}/data/README.md

The project includes the classic steps of the ML pipeline, including: data preperation, eda, outliers detection, impute, feature engineering, model selecton, and grid reserach.

Each step of the ML pipeline is coded on a seperate notebook (.ipynb):
1) date prep
2) eda
3) cleansing (outliers, imput)
4) feature engneering/selection
5) model selection and grid reaserch

Each notebook (N) calling its previous notebook (N-1) before executing itself, while dropping .pkl files for notebook N+1 to start its execution from.
A centrlized {PROJECT_PATH}/src/config.json file holds shared global parameters across all notebooks. Including: file paths, order of execution, outliers detection algorithm, impute algorithm, and model algorithm.
To prevent data leakage along the ML process, we split the data to df and df_test, processing them independently. "split_df" parameter in config.json control this option.

Project slides, including visualiziton of the data, is availbe in {PROJECT_PATH}/data/Spotify Dataset.pptx

