# Pokémon Mega Evolution Classification

A machine learning project that classifies Pokémon as **Mega Evolution** or **Regular Pokémon** using their battle statistics and Pokémon types.

## Overview

This project applies supervised machine learning to predict whether a Pokémon is a Mega Evolution Pokémon or a regular Pokémon. It uses Pokémon attributes such as HP, Attack, Defense, Special Attack, Special Defense, Speed, Total stats, and Pokémon types to train a Logistic Regression classifier.

The project covers data preprocessing, feature engineering, categorical encoding, model training, and evaluation using classification visualizations.

## Dataset

The project uses a Pokémon dataset containing 800 records.

The dataset includes the following features:

| Feature | Description |
|---|---|
| Type 1 | Primary Pokémon type |
| Type 2 | Secondary Pokémon type |
| Total | Combined base-stat total |
| HP | Hit points |
| Attack | Physical attack stat |
| Defense | Physical defense stat |
| Sp. Atk | Special attack stat |
| Sp. Def | Special defense stat |
| Speed | Speed stat |

The target variable, `Mega_evolution`, is created from the Pokémon's name:

- `Yes` — The name contains the word `Mega`.
- `No` — Otherwise.

The original `Name` column is removed after creating the target variable. The columns `#`, `Generation`, and `Legendary` are also dropped during preprocessing.

**Dataset requirement:** The notebook loads the dataset from `Pokemon.csv`. This file must be available in the notebook's working directory before running the code.

## Technologies Used

- **Python** — Programming language
- **Pandas** — Data manipulation and preprocessing
- **Scikit-learn** — Data splitting, encoding, Logistic Regression, and evaluation
- **Matplotlib** — Visualization of model evaluation results
- **Jupyter Notebook / Google Colab** — Interactive development environment

## Methodology

### 1. Data Loading and Preprocessing

The dataset is loaded using Pandas. Unnecessary columns are removed, and a binary target variable named `Mega_evolution` is created from the Pokémon names.

The original `Name` column is subsequently removed from the feature set.

### 2. Feature Selection

The model uses the following numerical and categorical features:

- Total
- HP
- Attack
- Defense
- Sp. Atk
- Sp. Def
- Speed
- Type 1
- Type 2

### 3. Train-Test Split

The dataset is divided into training and testing sets using an 80:20 split with `random_state=42`.

- **Training set:** 640 records
- **Testing set:** 160 records

The target labels are mapped to numerical values:

- `No` → `0`
- `Yes` → `1`

### 4. Categorical Encoding

The categorical features `Type 1` and `Type 2` are transformed using Scikit-learn's `OneHotEncoder`.

The encoder is fitted on the training data and then applied to both training and testing data. The encoded features are combined with the numerical features before model training.

### 5. Model Training

The project uses **Logistic Regression** for binary classification.

The model is initialized with `max_iter=1000` and trained on the preprocessed training data to learn patterns associated with Mega Evolution Pokémon.

### 6. Model Evaluation

The trained classifier predicts labels for the test set. Its outputs are examined using the following visualizations:

**Confusion Matrix**

Displays the counts of correct and incorrect predictions for the two classes.

**Precision-Recall Curve**

Illustrates the relationship between precision and recall at different classification thresholds.

**ROC Curve**

Shows the relationship between the true positive rate and false positive rate at different thresholds.

These visualizations help examine classification performance from different perspectives.

## Project Structure

```text
pokemon_classification/
├── README.md
└── pokemon.ipynb
```

The notebook uses `Pokemon.csv` as an input dataset. Ensure that this file is available in the expected location before executing the notebook.

## Getting Started

### Prerequisites

- Python 3
- Jupyter Notebook or Google Colab
- The `Pokemon.csv` dataset

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/Rachel602144/pokemon_classification.git
cd pokemon_classification
```

**2. Install the required libraries**

```bash
pip install pandas scikit-learn matplotlib jupyter
```

**3. Add the dataset**

Place `Pokemon.csv` in the notebook's working directory.

**4. Run the notebook**

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `pokemon.ipynb` and execute the cells in order.

Alternatively, open the notebook in Google Colab and upload the dataset when prompted by the execution environment.

## Limitations

- The target label is derived from Pokémon names, so the model learns to predict this label from the remaining attributes rather than independently verifying whether a Pokémon has an official Mega Evolution.
- The project uses a single train-test split, so results may vary with a different split.
- Logistic Regression may not capture complex nonlinear relationships between features.
- The notebook visualizes classification results but does not currently report a complete set of numerical evaluation metrics in its documented workflow.

## Future Improvements

- Calculate accuracy, precision, recall, F1-score, and ROC-AUC.
- Compare Logistic Regression with other classification algorithms.
- Use stratified splitting and cross-validation to evaluate model stability.
- Investigate class imbalance and its effect on predictions.
- Build a simple interface for entering Pokémon attributes and viewing predictions.

## Author

**Rachel Patni**

[GitHub Profile](https://github.com/Rachel602144)

---

This project demonstrates a basic supervised machine learning workflow involving data preprocessing, feature engineering, binary classification, and model evaluation.
