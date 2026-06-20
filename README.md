# E-Commerce Project

## Data Cleaning & Preparation Process

**Dataset:** Synthetic E-commerce Transactions (10,000+ rows)  
**Project:** E-Commerce Sales & Profitability Analysis  

### Generated Files

| File | Description |
|---|---|
| `raw_sales_data.xlsx` | Raw dataset containing intentionally introduced data issues |
| `cleaned_sales_data.xlsx` | Cleaned dataset ready for analysis |
| `Data_Dictionary.xlsx` | Column definitions and metadata |
| `Data_Cleaning_Process.md` | Documentation of cleaning workflow |

---

## 1. Issues Introduced in Raw Dataset

The raw dataset was intentionally generated with common real-world data quality problems.

### Data Quality Issues

| Issue | Description |
|---|---|
| Date inconsistencies | `Order Date` and `Ship Date` contained mixed formats (`DD/MM/YYYY`, `YYYY-MM-DD`, `Aug 12, 2023`) |
| Duplicate records | ~13 exact duplicate rows intentionally added |
| Missing values | ~5% of `Postal Code` values were missing |
| Text inconsistencies | Random capitalization issues in `Country`, `Category`, and `Sub-Category` |
| Numeric inconsistencies | Numeric fields were recalculated during cleaning for accuracy |
| Currency format | Values stored as numeric GBP (£) amounts for analysis |

---

# 2. Data Cleaning Process

Cleaning was performed using a combined **Excel + pandas workflow**.

## 2.1 Standardized Date Formats

Converted all date fields into ISO format:

Affected columns:

- `Order Date`
- `Ship Date`

Methods used:

- Excel:
  - `TEXT()`
  - `DATEVALUE()`

- pandas:
  - Date parsing and conversion

---

## 2.2 Removed Duplicate Records

Removed exact duplicate rows.

Methods:

- Excel:
- pandas:
```python
drop_duplicates()
