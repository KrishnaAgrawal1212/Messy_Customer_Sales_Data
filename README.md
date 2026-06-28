# Data Cleaning Project

A Python-based data cleaning pipeline that processes raw datasets to produce clean, analysis-ready data using industry-standard libraries.

# Overview

This project performs end-to-end data cleaning on a raw dataset, addressing common data quality issues such as missing values, duplicate records, inconsistent formatting, outliers, and incorrect data types. The cleaned output is ready for exploratory data analysis (EDA) or machine learning workflows.

# Tools and Libraries Used

Numpy, Pandas, Matplotlib, Seaborn

# Data Cleaning Process

# The cleaning pipeline follows these key steps:

# 1. Data Loading & Initial Inspection


Load the raw dataset using pandas.read_csv() / read_excel()
Inspect shape, column types, and summary statistics (df.info(), df.describe())
Identify columns with null values using df.isnull().sum()


# 2. Handling Missing Values


Numerical columns: filled using mean or median imputation based on skewness
Categorical columns: filled with the mode or a placeholder value ("Unknown")
Rows with excessive nulls (>50% missing) dropped using df.dropna(thresh=...)


# 3. Removing Duplicates


Identified and removed exact duplicate rows with df.drop_duplicates()
Checked for near-duplicates based on key identifier columns


# 4. Data Type Correction


Converted date columns to datetime format using pd.to_datetime()
Converted numeric columns stored as strings using pd.to_numeric(errors='coerce')
Encoded categorical columns appropriately (astype('category'))


# 5. Standardizing Text & Formatting


Stripped leading/trailing whitespace from string columns
Normalized text casing (e.g., .str.lower(), .str.title())
Standardized inconsistent category labels (e.g., "male", "Male", "M" → "Male")


# 6. Outlier Detection & Treatment


Used IQR method and z-score (via scipy.stats) to detect outliers
Outliers were either capped (winsorization) or removed based on domain logic


# 7. Final Validation


Confirmed zero null values and correct dtypes in the cleaned dataset
Compared row counts before and after to log data loss
Exported cleaned data to data/cleaned/cleaned_dataset.csv
