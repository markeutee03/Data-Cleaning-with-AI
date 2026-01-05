# Data Cleaning

## Student Information
- Name: John Mark Montilla
- Course Year: BSCS 4
- Date: 2025-10-09

## Dataset
## Dataset
- Source: Kaggle
- Name: Titanic – Machine Learning from Disaster
- Link: https://www.kaggle.com/competitions/titanic/data?select=train.csv
- Raw file used: train.csv (renamed to raw_dataset.csv)

## Why this dataset
I chose Titanic because it contains real-world data quality problems such as missing values (Age, Cabin, Embarked), mixed text formats, and potential outliers (Fare). This makes it ideal for practicing practical data cleaning techniques.

---

## Initial Exploration (Before Cleaning)

### Dataset Shape
- Rows: 891
- Columns: 12


### Checks performed
- `df.info()`
- `df.describe()`
- Missing values per column
- Duplicate rows

### Summary
The dataset contains missing values in the `Age`, `Cabin`, and `Embarked` columns.
No duplicate rows were found. Several numeric columns show potential outliers,
particularly the `Fare` column.

## Issues Found
- Missing values:
  - `Age` has 177 missing values
  - `Cabin` has 687 missing values
  - `Embarked` has 2 missing values
- Duplicates:
  - No duplicate rows were found
- Inconsistencies:
  - Text columns such as `Sex`, `Ticket`, and `Embarked` contain mixed casing and extra whitespace
- Outliers:
  - `Fare` contains extreme values (maximum fare of 512.33)
  - `Age` contains potential outliers (ages up to 80)
---

## Cleaning Steps

1. **Missing Values**
   - Filled `Age` with median.
   - Filled `Embarked` with mode (most common value).
   - For `Cabin`, created `Cabin_missing` indicator and filled missing cabins with `"Unknown"`.

2. **Duplicates**
   - Removed duplicate rows using `drop_duplicates()`.

3. **Standardize Formats**
   - Trimmed spaces and standardized casing:
     - `Sex` → lowercase
     - `Embarked` → uppercase
     - `Ticket` → uppercase + trimmed
     - `Name` → trimmed

4. **Outliers**
   - Used the IQR method to cap outliers (winsorization) for numeric columns such as `Fare` and `Age`.

---

## Before vs After (Snapshots)

### Dataset Shape
- Rows before cleaning: 891
- Columns before cleaning: 12
- Rows after cleaning: 891
- Columns after cleaning: 13

### Sample Rows
- Before cleaning: displayed using `df.sample(5)` in the notebook
- After cleaning: displayed using `cleaned.sample(5)` in the notebook

### Summary Statistics
- Before cleaning: generated using `df.describe()`
- After cleaning: generated using `cleaned.describe()`
---

## AI Prompts Used (Required)

## AI Prompts Used

### Prompt 1
**Prompt:**
> Generate Pandas code to clean the Titanic dataset by handling missing values, removing duplicates, standardizing text formats, and treating outliers using the IQR method.

**AI Response:**
The AI provided Pandas-based examples for:
- Filling missing values using median and mode
- Removing duplicate rows
- Standardizing string formats
- Applying IQR-based outlier detection and treatment

**How the AI was used:**
The AI-assisted response was used as a reference to design the data cleaning workflow and implement best practices in the data_cleaning.ipynb notebook.


---

## Results
- Cleaned dataset saved as `data/cleaned_dataset.csv`
- All missing values were handled appropriately
- Text fields were standardized
- Outliers were treated using IQR-based capping
- A new feature (`Cabin_missing`) was added to preserve information from missing cabin values


---

## Video Presentation (2–3 minutes)
Video link: (paste YouTube unlisted or Google Drive link here)
