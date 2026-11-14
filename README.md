# Discovering Customer Lifecycle States and Behavioral Drift for Early Churn Detection

> Fall 2026 Amazon 1B - Break Through Tech AI Studio

---

### 👥 **Team Members**

| Name                   | GitHub Handle         | Contribution                         |
| ---------------------- | --------------------- | ------------------------------------ |
| Cristian Pena          | @cpena-estrada        | Data Engineering, Backend, Pandas    |
| Addrita Biswas         | @aaayushhhh           | Web Design/Web Development, AI/ML    |
| Ashley Cruz Lopez      | @ashleyycruz          | Python/Full Stack, AI/ML integration |
| Medelen Nguyen         | @medelennn24          | Python, Pandas, Sklearn, R           |
| Harshal Patel          | @Hersh3y              | Python, Applied AI, Backend Dev      |
| Joshua Stewart-Roberts | @jroberts2605         | R, Java, Python                      |
| Dayana Pascual Sanchez | @dayanapascualsanchez | Python, Java, & AI/ML                |

---

## Project Highlights

- Building an early-warning system using the public Online Retail II transaction dataset.
- Defining churn at each month-end snapshot as no purchase in the following 90 days; snapshots without a fully observed future window are excluded.
- Creating a complete customer-month panel with zero-purchase months and backward-looking 30-, 60-, and 90-day behavior features.
- Comparing four tuned tabular classifiers with a custom 1D CNN and a GRU using chronological evaluation.

## Setup and Installation

**1. Clone the repository**

```bash
git clone https://github.com/Break-Through-Tech/Amazon-1B-discovering-customer-lifecycle-states-and-behavioral-drift-for-early-churn-detection
cd Amazon-1B-discovering-customer-lifecycle-states-and-behavioral-drift-for-early-churn-detection
```

**2. Create and activate a virtual environment**

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Access the dataset**

The raw dataset is included at [`data/online_retail_ii.parquet`](data/online_retail_ii.parquet):

```python
import pandas as pd

df = pd.read_parquet('data/online_retail_ii.parquet')
```

The source is the [Online Retail II dataset](https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii) from the UCI Machine Learning Repository.

**5. Run the modeling workflow**

Run these notebooks from the repository root, in order:

1. [`notebooks/01_outliers.ipynb`](notebooks/01_outliers.ipynb) prepares purchase transactions and writes `data/outliers_handled.parquet`.
2. [`notebooks/03_features_and_label.ipynb`](notebooks/03_features_and_label.ipynb) builds the customer-month panel and writes `data/features_and_label.parquet`.
3. [`notebooks/06_model_training.ipynb`](notebooks/06_model_training.ipynb) tunes tabular models and benchmarks CNN/GRU sequence models on a later-month holdout.

The other notebooks provide separate standardization, EDA, and visualization work. The modeling path reads `outliers_handled.parquet` directly; rerun notebook 03 whenever feature or label logic changes.

---

## Project Overview

This Fall 2026 Break Through Tech AI Studio project explores public e-commerce transaction data to predict churn, detect behavior changes, and identify lifecycle states. It is an academic project and does not use Amazon customer data or internal systems.

## Data Exploration

The current cleaned purchase input contains 776,591 rows from December 2009 through December 9, 2011. Notebook 03 builds 75,255 customer-month snapshots for 5,224 customers from December 2009 through August 2011; later snapshots are excluded because their full 90-day label windows are not observable.

The saved modeling table has 25 predictors, including order count, spend, quantity, and unique products over trailing 30-, 60-, and 90-day windows, recency, first-month status, and 30-day behavior changes. Customers remain in the panel during months with no purchases. Predictors use transactions strictly before the next month starts.

The labeled table's overall churn rate is 57.86%. Churn prevalence varies by snapshot month, so evaluation uses a chronological split rather than a random row split.

## Model Development

Notebook 06 compares logistic regression, random forest, histogram gradient boosting, and XGBoost. Randomized search selects accuracy on four expanding-window folds; the latest 20% of distinct months are held out. A custom 1D CNN and a GRU process six-month customer histories. The sequence models are fixed-epoch exploratory baselines and are not hyperparameter-tuned.

Because missing a churner is costly, the notebook reports an accuracy-oriented threshold and a separate tabular threshold selected for zero false negatives on out-of-fold training predictions. That threshold does not guarantee zero false negatives on future data. Evaluation includes accuracy, precision, recall, F1, ROC-AUC, PR-AUC, and false-negative counts.

## Results and Key Findings

On the held-out later months, the custom 1D CNN scored 75.3% accuracy, 74.9% precision, and 91.8% recall at threshold 0.50, with 1,305 false negatives. The GRU scored 75.2% accuracy, 74.5% precision, and 92.3% recall, with 1,215 false negatives. These are exploratory fixed-epoch results.

Among tuned tabular models, random forest scored 74.5% accuracy at threshold 0.50, with 1,855 false negatives. The accuracy-selected histogram gradient-boosting threshold scored 73.6% accuracy and 93.1% recall, with 1,090 false negatives.

The random-forest threshold selected for zero false negatives in training cross-validation produced zero false negatives on this test period, but accuracy fell to 64.0% and it flagged many retained customers as churn-risk. This illustrates the tradeoff between avoiding missed churn and limiting false alarms. Rerun notebook 06 after changing features, labels, dependencies, or the data split.

## Next Steps

- Tune the sequence models and assess them on additional future periods.
- Validate the zero-false-negative operating point on additional time periods; zero misses on one holdout is not a guarantee of future performance.
- Continue customer-level behavior and lifecycle-state analysis, then add explainability.
- Treat 90% accuracy as an aspiration, not an achieved result; evaluate it alongside recall and false-negative counts.

## License

The project license has not yet been selected. Confirm the choice with the Challenge Advisor before publishing.

## References

- [Online Retail II dataset, UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii)

## Acknowledgements

Thank the Challenge Advisor, AI Studio Coach, and others who supported the project.
