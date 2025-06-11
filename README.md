# Survival Analysis Tabular Datasets

This repository contains numerous benchmark tabular datasets for testing various survival analysis algorithms.

Check also [Classification Tabular Datasets](https://github.com/cezary986/classification_tabular_datasets) and [Regression Tabular Datasets](https://github.com/cezary986/regression_tabular_datasets)

All datasets are splitted to train and test parts. If whole unsplitted dataset was accessible it is also splitted into 10-fold cross validation datasets. Each dataset contains survival status and column named **survival_status**  and survival time column named **survival_time**. Files in parquet data format is used which could be easily loaded using pandas Python package. Survival status columns contains numerical values of 0 and 1 where 1 mean occurrence of event.


## Dataset Overview

| Dataset name                                                                                            | Rows    | Columns | Missing values | Events occurences |
| ------------------------------------------------------------------------------------------------------- | ------- | ------- | -------------- |-------------------|
| [bmt-ch](https://github.com/adaa-polsl/GuideR/blob/master/datasets/bmt/bone-marrow.arff) | 187 | 36 (10 numerical and 26 categorical) | yes  |  85 |
| [cancer](https://cran.r-project.org/web/packages/survival/survival.pdf) | 228 | 8 (8 numerical and 0 categorical) | yes  |  165 |
| [follic](https://cran.r-project.org/web/packages/randomForestSRC/randomForestSRC.pdf) | 541 | 5 (4 numerical and 1 categorical) | no  |  348 |
| [GBSG2](https://cran.r-project.org/web/packages/TH.data/TH.data.pdf) | 686 | 9 (6 numerical and 3 categorical) | no  |  299 |
| [hd](https://cran.r-project.org/web/packages/randomForestSRC/randomForestSRC.pdf) | 865 | 7 (3 numerical and 4 categorical) | no  |  426 |
| [lung](​https://www.stats.ox.ac.uk/pub/datasets/csb) | 1032 | 8 (6 numerical and 2 categorical) | yes  |  764 |
| [Melanoma](https://cran.r-project.org/web/packages/riskRegression/riskRegression.pdf) | 205 | 8 (4 numerical and 4 categorical) | no  |  71 |
| [mgus](https://cran.r-project.org/web/packages/survival/survival.pdf) | 241 | 10 (8 numerical and 2 categorical) | yes  |  184 |
| [pbc](https://cran.r-project.org/web/packages/survival/survival.pdf) | 418 | 18 (17 numerical and 1 categorical) | yes  |  161 |
| [std](https://cran.r-project.org/web/packages/KMsurv/KMsurv.pdf) | 877 | 22 (20 numerical and 2 categorical) | no  |  347 |
| [uis](https://cran.r-project.org/web/packages/quantreg/quantreg.pdf) | 575 | 14 (14 numerical and 0 categorical) | no  |  464 |
| [whas1](https://web.archive.org/web/20170318010915/http://www.umass.edu/statdata/statdata/data/whas1.txt) | 481 | 8 (8 numerical and 0 categorical) | no  |  249 |
| [whas500](https://web.archive.org/web/20170517071528/http://www.umass.edu/statdata/statdata/data/whas500.txt) | 500 | 14 (14 numerical and 0 categorical) | no  |  215 |
| [zinc](https://dceg.cancer.gov/tools/analysis/nested-cohort) | 431 | 56 (47 numerical and 9 categorical) | yes  |  81 |

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