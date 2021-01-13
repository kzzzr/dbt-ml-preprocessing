# dbt-ml-preprocessing

A package for dbt which enables standardization of data sets. You can use it to build a feature store in your data warehouse, without using external libraries like Spark's mllib or Python's scikit-learn.

The package contains a set of macros that mirror the functionality of the [scikit-learn preprocessing module](https://scikit-learn.org/stable/modules/preprocessing.html). Originally they were developed as part of the 2019 Medium article [Feature Engineering in Snowflake](https://medium.com/omnata/feature-engineering-in-snowflake-4312032e0d53).

Currently they have been tested in Snowflake, Redshift and BigQuery. The test case expectations have been built using scikit-learn (see *.py in [integration_tests/data/sql](integration_tests/data/sql)), so you can expect behavioural parity with it.

The macros are:

| scikit-learn function | macro name | Snowflake | BigQuery | Redshift | Example |
| --- | --- | --- | --- | --- | --- |
| [KBinsDiscretizer](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.KBinsDiscretizer.html#sklearn.preprocessing.KBinsDiscretizer)| k_bins_discretizer  | Y | Y | Y | ![example](images/k_bins.gif) |
| [LabelEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html#sklearn.preprocessing.LabelEncoder)| label_encoder  | Y | Y | Y | ![example](images/label_encoder.gif) |
| [MaxAbsScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MaxAbsScaler.html#sklearn.preprocessing.MaxAbsScaler) | max_abs_scaler | Y | Y | Y |  ![example](images/max_abs_scaler.png) |
| [MinMaxScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html#sklearn.preprocessing.MinMaxScaler) | min_max_scaler | Y | Y | Y |  ![example](images/min_max_scaler.png) |
| [Normalizer](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Normalizer.html#sklearn.preprocessing.Normalizer) | normalizer | Y | Y | Y | ![example](images/normalizer.png) |
| [OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html#sklearn.preprocessing.OneHotEncoder) | one_hot_encoder | Y | Y | Y | ![example](images/one_hot_encoder.gif) |
| [QuantileTransformer](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.QuantileTransformer.html#sklearn.preprocessing.QuantileTransformer) | quantile_transformer | Y | N | Y | ![example](images/quantile_transformer.png) |
| [RobustScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.RobustScaler.html#sklearn.preprocessing.RobustScaler) | robust_scaler | Y | Y | Y | ![example](images/robust_scaler.png) |
| [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html#sklearn.preprocessing.StandardScaler) | standard_scaler | Y | Y | Y | ![example](images/standard_scaler.png) |

## Installation
To use this in your dbt project, create or modify packages.yml to include:
```
packages:
  - git: "https://github.com/omnata-pty-ltd/dbt-ml-preprocessing.git"
    revision: 0.4.0
```
_(replace the revision number with the latest)_

Then run:
```dbt deps``` to import the package.

## Usage
To read the macro documentation and see examples, simply [generate your docs](https://docs.getdbt.com/reference/commands/cmd-docs/), and you'll see macro documentation in the Projects tree under ```dbt_ml_preprocessing```:

![docs screenshot](images/docs_screenshot.png)



