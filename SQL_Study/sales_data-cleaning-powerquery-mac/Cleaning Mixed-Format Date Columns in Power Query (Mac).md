# Cleaning Mixed-Format Date Columns in Power Query (Mac)

## Project Overview
This project demonstrates how to clean and standardize date columns in Excel for Mac using the Power Query Editor.  
The dataset contains multiple date columns with mixed formats (e.g., `MM/DD/YYYY`, `DD-MM-YY`, `YYYY-MM-DD`, timestamps, placeholders like "N/A").  
The goal is to transform all date columns into a consistent, error-free Date type for accurate analysis.

**Tools Used:**
- Excel for Mac v16+
- Power Query Editor (Mac UI)
- GitHub for documentation

---

## Dataset
- **Source:** [Sample Superstore CSV](#) *(replace with link if public)*
- **Key Date Columns:**  
  - `Order Date`
  - `Ship Date`

---

## Steps & Screenshots

### 1. Import CSV into Power Query
**Actions:**
- Data → Get Data → From Text/CSV
- Select file → Import → Transform Data

**Screenshot:**
![Step 1 - Import](images/step1-import.png)

---

### 2. Profile the Columns
**Actions:**
- View → Data Preview dropdown → enable:
  - Show column quality details
  - Show column value distribution
  - Show column profile in details pane

**Screenshot:**
![Step 2 - Column Profiling](images/step2-column-profile.png)

---

### 3. Duplicate the Original Column
**Actions:**
- Right-click `Order Date` → Duplicate Column
- Rename to `Order Date (Clean)`

**Screenshot:**
![Step 3 - Duplicate Column](images/step3-duplicate.png)

---

### 4. Clean the Duplicate Column
**Actions:**
1. Trim & Clean text:
   - Transform → Format → Trim
   - Transform → Format → Clean
2. Replace placeholders:
   - Transform → Replace Values:
     - `N/A` → blank
     - `—` (em dash) → blank
     - `-` (simple dash) → blank
3. Extract Date Only if needed:
   - Transform → Extract → Date → Date Only

**Screenshot:**
![Step 4 - Cleaning](images/step4-cleaning.png)

---

### 5. Convert Using Locale
**Actions:**
- Transform → Data Type → Using Locale…
- Data Type: Date
- Locale: English (United States) *(or UK if day-first)*

**Screenshot:**
![Step 5 - Using Locale](images/step5-using-locale.png)

---

### 6. Validate Column
**Actions:**
- Confirm Valid = 100%, Error = 0% in column profile
- Sort ascending to visually check for outliers

**Screenshot:**
![Step 6 - Validation](images/step6-validation.png)

---

### 7. Apply Same Steps to Other Date Columns
**Actions:**
- Duplicate `Ship Date` → repeat cleaning steps → validate

**Screenshot:**
![Step 7 - Clean Ship Date](images/step7-clean-ship-date.png)

---

### 8. Remove Original Columns (Optional)
**Actions:**
- Right-click original date columns → Remove

**Screenshot:**
![Step 8 - Remove Originals](images/step8-remove-originals.png)

---

### 9. Close & Load
**Actions:**
- Home → Close & Load To…
- Table → New Worksheet

**Screenshot:**
![Step 9 - Loaded Table](images/step9-loaded-table.png)

---

## Results
**Before Cleaning:**
- Mixed date formats, placeholders, potential locale errors.

**After Cleaning:**
- All date columns standardized to correct Date type.
- 0% errors, 100% valid dates.

**Example Output Table:**
| Order Date (Clean) | Ship Date (Clean) |
|--------------------|-------------------|
| 11/8/2016          | 11/11/2016        |
| 6/12/2016          | 6/16/2016         |
| ...                | ...               |

---

## Key Learnings
- Mac Power Query’s column profiling is under **View → Data Preview** rather than the Windows “Column Quality” button.
- Locale conversion is critical when datasets mix date formats.
- Duplicating columns before cleaning preserves the original data for reference.

---

## Files in This Repository
- `powerquery-mac-clean-date-columns.md` *(this file)*
- `images/` *(folder with screenshots)*