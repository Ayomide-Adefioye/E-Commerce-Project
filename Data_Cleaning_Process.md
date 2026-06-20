# Data Cleaning & Preparation Process

**Dataset:** Synthetic E-commerce transactions (10,000+ rows) — generated for the E-Commerce Sales & Profitability project.
**Files generated:** `raw_sales_data.xlsx`, `cleaned_sales_data.xlsx`

## 1. Issues introduced in raw dataset
- Inconsistent date formats in `Order Date` and `Ship Date` (DD/MM/YYYY, YYYY-MM-DD, 'Aug 12, 2023').
- ~13 exact duplicate rows intentionally added.
- ~5% missing `Postal Code` values.
- Random capitalization issues in `Country`, `Category`, and `Sub-Category`.
- Numeric fields present but recomputed in cleaning step to ensure consistency.
- Currency: GBP (values are numeric and should be treated as GBP in analysis).

## 2. Cleaning steps performed (Excel & pandas combined approach)
1. **Standardized date formats**
   - Converted `Order Date` and `Ship Date` to ISO `YYYY-MM-DD` using parsing (Excel: TEXT/DATEVALUE; here using pandas parsing).
2. **Removed exact duplicates**
   - Used Excel Data -> Remove Duplicates (or `drop_duplicates()` in pandas).
   - Duplicates removed: 12
3. **Filled missing postal codes**
   - Replaced NULL postal codes with `N/A` to keep data consistent.
4. **Standardized text capitalization**
   - `Country`, `Category`, `Sub-Category` converted to Title Case (Excel: PROPER()).
5. **Validated and recalculated numeric fields**
   - Ensured `Sales`, `Cost`, and `Profit` are numeric.
   - Recomputed `Profit = Sales - Cost` to remove rounding inconsistencies.
6. **Calculated additional fields**
   - `Profit Margin = Profit / Sales` (decimal)
   - `Year`, `Month`, `Order Month` (YYYY-MM) for time grouping.
7. **Final validation**
   - Verified no missing values in critical fields (Order ID, Order Date, Sales).
   - Final row count: 10001

## 3. Notes for reproducibility (how to do this in Excel)
- Use **Data -> Text to Columns** to correct mis-parsed columns.
- Use **Remove Duplicates** under the Data ribbon to remove exact duplicates.
- Use **IFERROR**, **ISNUMBER**, and **DATEVALUE** functions for date parsing where needed.
- Use **=PROPER()** to standardize text capitalization.
- Use helper columns to calculate `Profit Margin` and `Order Month` then copy-paste-values for stability before export.

## 4. Final output files
- `cleaned_sales_data.xlsx` — cleaned, ready for analysis in Power BI and SQL
- `raw_sales_data.xlsx` — raw, intentionally messy version for audit and documentation
- `Data_Dictionary.xlsx` — column definitions
- `Data_Cleaning_Process.md` — this document