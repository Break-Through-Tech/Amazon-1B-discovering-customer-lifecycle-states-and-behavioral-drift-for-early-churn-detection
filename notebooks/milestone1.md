# Milestone 1

## Notebook and dataset flow

The main pipeline starts with the Online Retail II transaction data. Each transaction row is cleaned and filtered in notebook 01; this handles missing values, outliers, and drops cancellations & non-product rows before the cleaned transaction dataset is saved to `data/outliers_handled.parquet`.

```text
data/online_retail_ii.parquet 
  -> notebooks/01_outliers.ipynb 
  -> data/outliers_handled.parquet
```

From `outliers_handled.parquet`, the workflow branches:

```text
data/outliers_handled.parquet
  -> notebooks/02_standardize.ipynb
  -> data/standardized.parquet
```

Notebook 02 adds encoded country columns and log/z-score versions of transaction measures. It preserves the original columns. This is a separate standardized transaction output; notebook 03 does not currently read it. The dataset is saved to `data/standardized.parquet`.

```text
data/outliers_handled.parquet
  -> notebooks/03_features_and_label.ipynb
  -> data/features_and_label.parquet
```

Notebook 03 aggregates the cleaned transactions into customer-month rows, computes behavioral features, and adds the 90-day churn label. `features_and_label.parquet` is the customer-month dataset intended for EDA and model training. `is_churn` is the label.

Awaiting Notebook 04 (EDA)

## Notes

`03_features_and_label`
- total_spend and avg_order_value columns seem to have the same values. 
- days_since_last_purchase column has missing values. 
- days_since_last_purchase column datatype is float. Might be better to cast it to int datatype.
