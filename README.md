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
