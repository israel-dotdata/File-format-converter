# File Format Converter
## Overview
This project converts CSV files obtained from a MySQL database into JSON format for improved efficiency in downstream data engineering pipelines. JSON is often preferred over CSV due to its flexibility, nested structure support, and compatibility with various applications.

The program reads CSV files according to a schema definition, processes them using **Pandas**, and outputs the equivalent JSON files in a specified target directory.

---

## Data Model Details
![Data Model](https://github.com/israel-dotdata/File-format-converter/blob/main/images/2023-05-26_09-51-15-b44475f68043ebe48cc1f14ef90afdb8.png)

---

## Design
![Design Diagram](https://github.com/israel-dotdata/File-format-converter/blob/main/images/2023-05-26_09-51-15-86caf821669130d1481ea3e36226349f.png)

---

## Features
- Reads schema definitions from a `schemas.json` file.
- Dynamically assigns column names to CSV files based on schema.
- Converts CSV files to JSON format with line-delimited records.
- Handles multiple datasets in a single run.
- Creates output directories automatically.

---

  ## Technologies Used
- **Python** – Core programming language.
- **Pandas** – For reading CSV into DataFrames and converting DataFrames into JSON.
- **Glob & OS** – For file handling and directory operations.
- **JSON** – For schema parsing and JSON file writing.

---

  ## How It Works
1. The script reads the `schemas.json` file to obtain the column structure for each dataset.
2. CSV files matching the dataset name are located in the source directory.
3. Each CSV file is read into a Pandas DataFrame with proper column names.
4. DataFrames are converted to line-delimited JSON files.
5. Output files are saved in the target directory under their dataset name.

---

## Usage

### 1. Environment Variables
Set the source and target directories:
```powershell
$Env:SRC_BASE_DIR = "Data/retail_db"  
$Env:TGT_BASE_DIR = "Data/retail_db_json"
```

### 2. Run for all datasets:
```powershell
python app.py
```

### 3. Run for specific datasets:
```powershell
python app.py '[\"order\", \"order_items\"]'
```
---
## Output Format (JSON)
```json
{"column1": "value1", "column2": "value2", "column3": "value3"}
{"column1": "value4", "column2": "value5", "column3": "value6"}
```

