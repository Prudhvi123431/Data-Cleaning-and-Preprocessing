import pandas as pd

# Load dataset
df = pd.read_csv(r"C:\Users\PRUDHVI\Documents\cleaned_dataset.csv")
# ------------------------------
# Track initial info
# ------------------------------
initial_shape = df.shape
initial_missing = df.isnull().sum().sum()
initial_duplicates = df.duplicated().sum()

print("Shape before cleaning:", initial_shape)
print("Missing values before cleaning:", initial_missing)
print("Duplicates before cleaning:", initial_duplicates)

# ------------------------------
# 1. Remove duplicate rows
# ------------------------------
df = df.drop_duplicates()

# ------------------------------
# 2. Handle missing values
# ------------------------------
# Drop rows if too many missing values
df = df.dropna(thresh=len(df.columns) // 2)

# Fill missing numeric values with median, categorical with mode
for col in df.columns:
    if df[col].dtype in ['int64', 'float64']:
        df[col] = df[col].fillna(df[col].median())
    else:
        df[col] = df[col].fillna(df[col].mode()[0] if not df[col].mode().empty else "Unknown")

# ------------------------------
# 3. Standardize column names
# ------------------------------
df.columns = df.columns.str.lower().str.strip().str.replace(' ', '_')

# ------------------------------
# 4. Clean text columns
# ------------------------------
for col in df.select_dtypes(include=['object']).columns:
    df[col] = df[col].astype(str).str.strip()

# ------------------------------
# 5. Fix numeric conversion (if possible)
# ------------------------------
for col in df.columns:
    if df[col].dtype == 'object':
        try:
            df[col] = pd.to_numeric(df[col])
        except:
            pass

# ------------------------------
# Track final info
# ------------------------------
final_shape = df.shape
final_missing = df.isnull().sum().sum()
removed_duplicates = initial_duplicates
removed_rows = initial_shape[0] - final_shape[0]

# ------------------------------
# Save cleaned dataset
# ------------------------------
df.to_csv("final_cleaned_dataset.csv", index=False)

# ------------------------------
# Generate Summary Report
# ------------------------------
summary = f"""
📊 Data Cleaning Summary Report
---------------------------------
✅ Initial rows: {initial_shape[0]}, columns: {initial_shape[1]}
✅ Final rows: {final_shape[0]}, columns: {final_shape[1]}

🗑️ Duplicates removed: {removed_duplicates}
⚠️ Missing values fixed: {initial_missing - final_missing}
🧹 Rows dropped (too many missing values): {removed_rows}
📌 Columns standardized: {len(df.columns)}

✅ Cleaned dataset saved as: final_cleaned_dataset.csv
"""

print(summary)

# Optional: save summary as text file for GitHub
with open(r"C:\Users\PRUDHVI\Desktop\output.txt", "w", encoding="utf-8") as f:
    f.write(summary)


Here’s a clear summary of your code:

---

### **Purpose:**

This Python script uses **pandas** to clean a dataset (`cleaned_dataset.csv`) and generate a summary report of the cleaning process.

---

### **Steps in the Code:**

1. **Load Dataset**

   * Reads the CSV file into a pandas DataFrame.
   * Tracks initial shape, missing values, and duplicates.

2. **Remove Duplicates**

   * Drops all duplicate rows from the DataFrame.

3. **Handle Missing Values**

   * Drops rows where more than half of the columns are missing.
   * Fills remaining missing numeric values with the **median**.
   * Fills missing categorical/text values with the **mode** or `"Unknown"` if mode is unavailable.

4. **Standardize Column Names**

   * Converts all column names to lowercase.
   * Strips whitespace.
   * Replaces spaces with underscores.

5. **Clean Text Columns**

   * Strips leading/trailing spaces from all string-type columns.

6. **Convert Numeric Columns**

   * Attempts to convert object-type columns to numeric if possible.

7. **Track Final Info**

   * Computes final shape, remaining missing values, and number of rows removed.

8. **Save Cleaned Dataset**

   * Saves the cleaned DataFrame as `final_cleaned_dataset.csv`.

9. **Generate Summary Report**

   * Prints and saves a summary of:

     * Initial vs final rows and columns
     * Duplicates removed
     * Missing values handled
     * Rows dropped
     * Columns standardized

