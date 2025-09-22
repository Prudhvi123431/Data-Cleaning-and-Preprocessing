**overview**
The objective was to clean and prepare a raw dataset for analysis using Excel and/or Python (Pandas). I chose the Netflix Movies and TV Shows dataset from Kaggle and performed a series of preprocessing steps to ensure data quality and consistency.


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

