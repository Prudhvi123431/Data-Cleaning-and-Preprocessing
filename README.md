📊 Netflix Dataset Cleaning
🧠 Overview
The objective was to clean and prepare a raw dataset for analysis using Excel and/or Python (Pandas). I chose the Netflix Movies and TV Shows dataset from Kaggle and performed a series of preprocessing steps to ensure data quality and consistency.
🛠️ Tools Used
Microsoft Excel (for initial inspection and cleaning)
Python (Pandas library, for deeper preprocessing)
Kaggle Notebook (for execution and file management)
📂 Dataset Description
The dataset includes metadata about Netflix titles such as:

Title, Director, Cast
Country of origin
Date added to Netflix
Release year, Rating, Duration
Genre classification
Description
🔍 Cleaning & Preprocessing Steps
Handled Missing Values: Identified nulls using .isnull() and filled or dropped based on context.
Removed Duplicates: Verified uniqueness using Excel’s “Remove Duplicates” and drop_duplicates() in Pandas.
Standardized Formats:
Unified date formats using pd.to_datetime()
Cleaned column headers (lowercase, no spaces)
Normalized categorical values (e.g., country names)
Verified Data Types: Ensured correct types for each column (e.g., integers for year, datetime for dates).
📈 Summary of Changes
The dataset was cleaned to remove inconsistencies, missing entries, and formatting issues. These changes improve its readiness for analysis, visualization, or modeling tasks.
📎 Files Included
cleaned_netflix_titles.xlsx: Final cleaned dataset
task_1_summary.txt: Brief overview of cleaning steps
Screenshots (optional): Visuals from Excel preprocessing
README.md: This file
💡 Learning Outcomes
Strengthened skills in data cleaning using Excel and Pandas
Gained hands-on experience with real-world datasets
Improved understanding of preprocessing workflows
Prepared a dataset suitable for further analysis or machine learning
