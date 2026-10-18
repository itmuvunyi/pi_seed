# Predicting Improved Seed Use in Rwanda with Machine Learning and Deep Learning

## Overview
This project predicts whether a farmer's plot–crop record reports **improved** or **traditional** seed, using ten survey characteristics from the NISR *Seasonal Agricultural Survey 2025, Season A*. It compares three classical models (Logistic Regression, Random Forest, HistGradientBoosting) with four neural-network variants on a segment-aware train/validation/test split. The selected model, a neural network with stronger dropout, reached a test ROC-AUC of 0.945. The full methodology, results and discussion are in the final report submitted with the project.

## Dataset
- **Source:** National Institute of Statistics of Rwanda (NISR), [Seasonal Agricultural Survey 2025](https://microdata.statistics.gov.rw/index.php/catalog/124)
- **File:** `Microdata/Season A/Rwa_raw_SeasonA2025_Production.csv`, tab-delimited, 34,369 rows × 101 columns
- **Target:** `s2q11`. Traditional seeds = 0, Improved seeds = 1. The 155 mixed `1&2` records are excluded, leaving 34,214 rows.
- **Predictors:** `s1q1`, `s1q2`, `s1q3`, `s1q4`, `s1q6`, `s1q7`, `s1q8`, `s1q9`, `s1q14`, `CropCategory`
- The dataset is not included in this repository. `Microdata.zip` is kept in the Drive folder linked above.

## Repository structure
```
├── Rwanda_Improved_Seed.ipynb      # Main notebook, runs top to bottom in Colab
├── requirements.txt                # Python dependencies
└── README.md
```
The dataset, trained models, figures, metrics files and TensorBoard logs are produced by the notebook and stored in the Google Drive folder linked above, in `agricultural_seed_prediction_outputs/`.


## How to run
**Google Colab (recommended)**
1. Upload `Microdata.zip` to `MyDrive/Intro_to_ML/Summative/`.
2. Open `Rwanda_Improved_Seed.ipynb` in Colab.
3. Select **Runtime → Run all** and allow Google Drive access.
4. Outputs are saved to `MyDrive/Intro_to_ML/Summative/agricultural_seed_prediction_outputs/`.

**Local machine**
```bash
git clone repo link
cd <repository-folder>
pip install -r requirements.txt
jupyter notebook Rwanda_Improved_Seed.ipynb
```
Skip the Google Drive mount cell and set `ZIP_PATH` to your local copy of `Microdata.zip`.

**TensorBoard logs**
```bash
tensorboard --logdir agricultural_seed_prediction_outputs/tensorboard
```

## Acknowledgements
- **Data:** National Institute of Statistics of Rwanda (NISR), Seasonal Agricultural Survey 2025.
- **Libraries:** scikit-learn, TensorFlow/Keras, pandas, NumPy, Matplotlib.
