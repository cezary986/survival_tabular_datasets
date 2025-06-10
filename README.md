# Survival Analysis Tabular Datasets

This repository contains numerous benchmark tabular datasets for testing various survival analysis algorithms.

All datasets are splitted to train and test parts. If whole unsplitted dataset was accessible it is also splitted into 10-fold cross validation datasets. Each dataset contains survival status and column named **survival_status**  and survival time column named **survival_time**. Files in parquet data format is used which could be easily loaded using pandas Python package.


## Dataset Overview

| Dataset Name | Rows | Columns | Missing Values |
| :------------------------------------------------------------------------------------------------------ | :----- | :-------------------------------- | :------------- |


Dataset summary is also available in csv file [datasets_summary.csv](https://github.com/cezary986/survival_tabular_datasets/blob/main/datasets_summary.csv) in root repo directory.

## Reading datasets using Python package

This repository also contains a tiny Python package which allows you to use datasets without the need to clone whole repository.

 To install it use the following command:

```bash
pip install git+https://github.com/cezary986/survival_tabular_datasets
```

The package exports two functions: `read_full_dataset` and `read_dataset_train_test`.
The first one reads full dataset and returns a tuple of X and y, where X is data and y are labels.
The second one reads dataset splitted to train and test parts and returns a tuple of X_train, y_train, X_test, y_test. 

Example:

```python
import survdatasets

# print list of all available datasets
print(", ".join(survdatasets.AVAILABLE_DATASETS))

# reads whole dataset without train/test split
X, y = survdatasets.read_full_dataset("follic")

# reads dataset splitted into train/test
X_train, y_train, X_test, y_test = survdatasets.read_dataset_train_test("follic")

# reads given dataset cross-validation fold
X_train, y_train, X_test, y_test = survdatasets.read_dataset_train_test("follic",  cv_fold=3)
```