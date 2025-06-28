**Welcome to our Milestone 2**

**Data Cleaning with Python, Pandas, Pandera, and Jupyter Notebook**

1. Install Python  
Python is a powerful language for data cleaning thanks to its readability, rich ecosystem of libraries, and active community support.  
- **Download & install**:  
  - Windows/macOS: Get the latest installer from [python.org](https://www.python.org/downloads/)  
  - Linux: `sudo apt-get install python3` (Debian/Ubuntu) or use your distro’s package manager
  

2. Install Jupyter Notebook  
  Jupyter Notebook provides an interactive environment where you can run code cell-by-cell, visualize results in place, and document your cleaning steps alongside your code.  
  1. Open a terminal or command prompt.  
2. Create (and activate) a virtual environment (recommended):  
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate      # Linux/macOS
   .\.venv\Scripts\activate       # Windows

3. Install Jupyter Notebook:
 ``` Using bash
  pip install notebook
```
4. Install & Import Pandas and Pandera
```   Using bash
   pip install pandas pandera
```
Then, at the top of your Jupyter notebook, import them:
```
  import pandas as pd           # for flexible, high-performance data structures
  ```
```
  import pandera as pa          # for declarative, schema-based data validation
```


5. Load dataset with pd.read_csv() (or other I/O funcs).
Define a schema in Pandera to enforce data types, ranges, and nullability.

Validate & clean DataFrame by running schema.validate(df).

Export the cleaned result with df.to_csv("cleaned_data.csv", index=False)

**EVENT LOGS**
Steps:
- Load raw data & inspect columns
- Identify key columns
- Initial shape and missing-value overview
- Drop high-null & irrelevant columns
- Parse & clean key fields
- Numeric & categorical fixes
- Outlier filtering on amount
- Pandera schema validation
- Save cleaned data

Revised pipeline with schema checks, error handling, or fallback logic. Strengthening pipeline to detect missing or broken columns.  Validation steps or a fallback plan added.
Steps:
- Load data with error handling
- Detect missing or broken columns
- Define Pandera schema for double-check
- Run schema validation, capture outcome
- Print consolidated report

Notes describing how the problem solved:
- Missing/Broken columns detected: We first verify that all essential columns exist before proceeding; any missing columns are reported but don’t crash the script.
- Schema double check: We use a Pandera schema to validate types and constraints; failures are caught and summarized rather than raising unhandled exceptions.
- Error Handling check: The entire load-and-validate pipeline is wrapped in try/except blocks so that any I/O or unexpected errors are logged and included in the health report.


**MARKETING SUMMARY**
Steps:
- Load raw data & normalize column names
- Detect key columns
- Initial shape and missing-value overview
- Drop high-null & irrelevant columns
- Parse & clean key fields
- Numeric & categorical fixes
- Outlier filtering on numeric metrics
- Define & apply Pandera schema
- Save cleaned data

Revised pipeline with schema checks, error handling, or fallback logic. Strengthening pipeline to detect missing or broken columns.  Validation steps or a fallback plan added.
Steps:
- Load data with error handling
- Detect missing or broken columns
- Define Pandera schema for double-check
- Run schema validation, capture outcome
- Print consolidated report

Notes describing how the problem solved:
- Missing/Broken columns detected: We explicitly check pipeline’s required columns (campaign_id, campaign_date) and log any that are missing without crashing.
- Schema double check: We build a Pandera schema—including your core fields and any numeric columns—and validate the DataFrame, catching and summarizing any errors.
- Error Handling check: We wrap the initial load in a try/except so any I/O issues are captured in the report rather than causing an unhandled exception.



**TREND REPORT**
Steps:
- Load raw data & normalize column names
- Detect date column
- Initial shape and missing-value overview
- Drop high-null & irrelevant columns
- Remove duplicates
- Numeric & categorical fixes
- Define & apply Pandera schema
- Save cleaned data

Revised pipeline with schema checks, error handling, or fallback logic. Strengthening pipeline to detect missing or broken columns.  Validation steps or a fallback plan added.
Steps:
- Track any upstream errors
- Detect missing or broken columns
- Define Pandera schema for double-check
- Run schema validation, capture outcome
- Print consolidated report

Notes describing how the problem solved:
- Missing/Broken columns detected
- By explicitly listing out the “required” fields (date_col plus all numeric metrics) and comparing them to df.columns, we immediately know if any core inputs are absent and  log a warning rather than crashing on a KeyError.
- Schema double check
- We rebuild a minimal Pandera schema over exactly those columns that survived cleaning steps. Running schema.validate(..., lazy=True) catches all type‐ or constraint‐violations in one go (rather than failing at the first), and summarizes them in report_schema. That way you see at a glance whether the “shape” of your cleaned data still matches expectations.
- Error Handling check
- Wrapping the initial pd.read_csv (and any other I/O) in try/except gives you an error_handling flag that records whether your pipeline even managed to load data. Downstream logic then continues or skips as appropriate—so a missing file or bad parse won’t kill your script.

