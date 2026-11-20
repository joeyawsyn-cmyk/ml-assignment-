# European Housing Cost Overburden Analysis

A beginner-friendly machine learning project that analyzes housing cost
overburden in European countries using supervised and unsupervised
learning algorithms.

## Project overview

This project uses the `european_housing_cost_overburden.csv` dataset to
explore housing cost overburden patterns and demonstrate four basic
machine learning algorithms:

  -----------------------------------------------------------------------
  Learning type           Algorithm               Task
  ----------------------- ----------------------- -----------------------
  Supervised              Linear Regression       Predict the housing
                                                  cost overburden rate

  Supervised              Decision Tree           Predict the housing
                          Regression              cost overburden rate
                                                  using decision rules

  Supervised              Decision Tree           Classify observations
                          Classification          as Low, Medium, or High

  Unsupervised            K-Means Clustering      Group countries with
                                                  similar overburden
                                                  patterns
  -----------------------------------------------------------------------

The target variable for the regression tasks is `overburden_rate_pct`.

## Dataset

The supplied CSV contains **45,789 rows and 16 columns**. Its fields
include:

-   `country`: country or geographical group name
-   `is_country_group`: indicates whether a row represents a country
    group
-   `poverty_status`: poverty-status category
-   `age_group`: age category
-   `sex`: sex category
-   `year`: observation year
-   `overburden_rate_pct`: housing cost overburden rate, expressed as a
    percentage
-   Additional code, date, and flag fields

The supplied file includes observations from 2003--2025. Not every
country necessarily has observations for every year or demographic
category.

### Data availability and attribution

Place the CSV file in the project root using this exact filename:

`european_housing_cost_overburden.csv`

The dataset's original publisher, source URL, and reuse licence were not
provided with the uploaded file. Add the correct attribution and dataset
licence here before redistributing the CSV. **The MIT licence in this
repository applies to the project code and documentation; it does not
automatically grant rights to the dataset.**

## Repository structure

``` text
european-housing-cost-overburden/
├── european_housing_cost_overburden.csv
├── main.py
├── README.md
├── LICENSE
└── requirements.txt
```

`main.py` should contain the Python implementation supplied with this
project. The script expects the CSV file to be in the same directory.

## Requirements

-   Python 3.9 or later
-   pandas
-   NumPy
-   Matplotlib
-   Seaborn
-   scikit-learn

Install the dependencies:

``` bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Alternatively, create a `requirements.txt` file containing:

``` text
pandas
numpy
matplotlib
seaborn
scikit-learn
```

Then install with:

``` bash
pip install -r requirements.txt
```

## How to run

1.  Clone or download this repository.
2.  Put `european_housing_cost_overburden.csv` in the project root.
3.  Make sure the Python script is named `main.py`.
4.  Install the required packages.
5.  Run:

``` bash
python main.py
```

The script prints dataset information, model evaluation metrics,
classification results, and clustering results. It also displays
exploratory-analysis and model-visualization plots.

## Algorithms and evaluation

### 1. Linear Regression

Predicts the numerical `overburden_rate_pct` target using country,
country-group status, poverty status, age group, sex, and year.

Evaluation metrics: - Mean Absolute Error (MAE) - Mean Squared Error
(MSE) - Root Mean Squared Error (RMSE) - R² score

### 2. Decision Tree Regression

Predicts the numerical overburden rate using a decision tree. The
supplied implementation limits tree depth to help keep the model
manageable.

Evaluation metrics: MAE, MSE, RMSE, and R².

### 3. Decision Tree Classification

Creates three target classes (`Low`, `Medium`, and `High`) from the
dataset's overburden-rate tertiles, then trains a decision tree
classifier.

Evaluation metrics: - Accuracy - Precision, recall, and F1-score -
Confusion matrix

**Important:** These three classes are defined from the distribution of
this dataset. They are not official European housing-risk thresholds.

### 4. K-Means Clustering

Aggregates observations by individual country, standardizes
country-level summary features, and applies K-Means to group countries
with similar overburden patterns. The script compares candidate cluster
counts using the silhouette score and visualizes clusters using PCA.

## Output files

When the script completes, it saves:

-   `model_comparison.csv` --- regression model MAE, RMSE, and R²
    results
-   `country_clustering_results.csv` --- country-level summary features
    and assigned cluster

Plots are displayed during execution.

## Methodological notes and limitations

-   The supplied implementation uses a random train/test split for
    supervised learning. Because records from the same country and
    related demographic groups can appear in both sets, evaluation
    scores may be optimistic when the goal is to generalize to unseen
    countries or future years.
-   For a stronger evaluation, consider a country-based or time-based
    split and compare its results with the random split.
-   The classification thresholds are calculated from the full target
    distribution in the supplied implementation. For a strict predictive
    evaluation, calculate thresholds using training data only and apply
    those thresholds to the test data.
-   K-Means is sensitive to feature scaling and the chosen number of
    clusters. The silhouette score is a guide, not proof that the
    clusters represent meaningful real-world categories.
-   Missing `flag` and `flag_meaning` values are expected in much of the
    supplied file; these fields are not used as model predictors in the
    implementation.
-   Machine learning results show patterns in the available data and
    should not be interpreted as causal explanations.

## Suggested future improvements

-   Add a country-held-out or chronological validation strategy.
-   Tune model hyperparameters using cross-validation.
-   Compare regression results with a simple baseline model.
-   Save trained models and prediction outputs.
-   Add a data dictionary and cite the dataset's original publisher.
-   Add unit tests and a reproducible environment file.

## Licence

The project code and documentation are released under the MIT License.
See [LICENSE](LICENSE).

The dataset may have separate copyright, attribution, and redistribution
conditions. Check its original source before sharing it publicly.
