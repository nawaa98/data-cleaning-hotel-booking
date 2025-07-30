# Data Cleaning Report: Hotel Booking Demand Dataset

---

## 📌 Executive Summary

The Hotel Booking Demand Dataset contains 119,390 records of hotel bookings from July 2015 to August 2017. The primary objective of this data cleaning project is to prepare the dataset for analysis by identifying and addressing quality issues such as missing values, duplicate entries, outliers, and inconsistent data formats.

---

## 🔍 Data Quality Assessment

| Issue Type       | Description                                                   |
|------------------|---------------------------------------------------------------|
| Missing Values   | Present in `children`, `country`, `agent`, `company` columns  |
| Duplicates       | Around 500+ exact duplicate records                           |
| Outliers         | Detected in `adr`, `lead_time`, `adults`, `babies`, etc.      |
| Inconsistencies  | Records with 0 adults, children, and babies were found        |

---

## 🛠️ Cleaning Methodology

**1. Handling Missing Values**
- `children`: Filled missing values with 0
- `country`: Filled missing values using mode (most frequent value)
- `agent`: Filled missing values with 0 (no agent)
- `company`: Filled missing values with 0 (no company)

**2. Duplicate Detection and Removal**
- Used `df.duplicated()` to find exact duplicates
- Removed using `df.drop_duplicates()`

**3. Outlier Detection and Treatment**
- Applied IQR method on numerical columns such as `adr` and `lead_time`
- Removed records outside 1.5 * IQR range
- Visualized using boxplots

**4. Data Inconsistency Fixes**
- Removed records with 0 adults, children, and babies
- Ensured consistent data types and value ranges

---

## 📊 Results and Impact

| Metric                      | Before Cleaning | After Cleaning |
|----------------------------|------------------|----------------|
| Total Rows                 | 119,390          | ~118,000       |
| Missing Value Columns      | 4                | 0              |
| Duplicate Rows             | ~500             | 0              |
| Outliers Removed           | Several          | ✅ Done         |
| Inconsistent Guest Counts  | Present          | ✅ Removed     |

---

## ✅ Final Output

- Cleaned Dataset: `hotel_bookings_cleaned.csv`
- Jupyter Notebook: `data_cleaning_process.ipynb`
- Report File: `data_cleaning_report.pdf`

---

## 💡 Recommendations

- Enforce validation rules during data collection (e.g., guests > 0)
- Ensure all booking agents and companies are properly recorded
- Regularly review and clean raw data before analysis
- Automate cleaning steps for future datasets

---

*End of Report*

