# Harmonization & Cleaning

The harmonization process ensures consistency across the data collected in the different countries and clinical sites. This is critical for enabling reliable downstream analysis and comparisons.

---

## Standardization Workflow

The NBS Study applies a standardized workflow to:

- Rename and recode variables to a **common format**
- Align column names across different source files and hospitals
- Map site-specific codes to **harmonized dictionary values**
- Standardize units (e.g., age in days, temperature in °C)
- Uniformly format dates, missing values, and booleans

This workflow is implemented using **R scripts**, with automatic logging of all changes and errors.

---

## Missing Data Checks

Data quality control includes:

- Flagging and imputing **missing or invalid entries**
- Checking ranges for continuous variables (e.g., birthweight, gestational age)
- Detecting **duplicate records or conflicting IDs**
- Identifying **impossible values** (e.g., negative age, future dates)
- Generating **summary reports** per site to track QC status

Automated imputation (e.g., using median/mode filling) is selectively applied only when justified.
