# An Introduction to Polars - Structuring, Joining and Validating Tabular Data

A quick introduction to polars and its capabilities, including high-performance tabular data manipulation, relational mapping, etc. for financial validation. Polars is a fast DataFrame library implemented in Rust.

---

## Project Overview

This repository performs an audit of global datacenter procurement transactions for the fiscal year 2023. Using Polars, we:
1. **Standardize and Structure** disparate raw data schemas.
2. **Perform Relational Mapping** (inner joins) to map orders to geographic and power capacity contexts.
3. **Aggregate National Spend** to identify the top 5 spenders/vendors in each operating country.
4. **Audit and Validate Ledger Records** by aggregating quarterly transaction line-items to reconstruct expected order totals, then flagging discrepancies against the master summary ledger.

---

## Tech Stack & Concepts

- **Core Library:** [Polars](https://pola.rs/) (leveraging parallel query execution and expression optimization).
- **Environment:** Jupyter Notebooks (`ipykernel`).
- **Relational Concepts:** Inner Joins, Group By Aggregations, Schema Casting, Data Validation.

---

## Repository Structure

```directory
Intro-to-Polars/
├── .gitignore               # Standard gitignore for Python & Jupyter
├── README.md                # Project documentation and quick start
├── requirements.txt         # Project dependencies
├── data/                    # Raw CSV data files
│   ├── datacenter_locations.csv
│   ├── order_summary_2023.csv
│   └── order_detail_2023_Q[1-4].csv
├── notebooks/               # Source Jupyter notebooks
│   └── intro_to_polars.ipynb
└── output/                  # Audit output CSV results
    ├── vendor_spend_summary.csv
    └── mismatches.csv
```

---

## Getting Started (Installation)

Follow these steps to set up your local environment using `uv` and run the notebook:

### 1. Create a Virtual Environment

Use `uv` to create a virtual environment with Python 3.12:
```bash
uv venv --python 3.12
```

### 2. Activate the Virtual Environment

Activate the environment based on your operating system:

```bash
# On macOS / Linux / Git Bash:
source .venv/bin/activate

# On Windows (PowerShell):
source .venv/scripts/activate
```

### 3. Install Dependencies

Install the project packages (including `ipykernel` and `polars`):
```bash
uv pip install -r requirements.txt
```

### 4. Register the Jupyter Kernel

Register the virtual environment's kernel with a user-friendly display name so it's selectable inside Jupyter or VS Code:
```bash
python -m ipykernel install --user --name=intro-to-polars --display-name="Python (Intro to Polars)"
```

---

## Running the Notebook

1. Open your IDE (e.g., VS Code or Jupyter Lab).
2. Open `notebooks/intro_to_polars.ipynb`.
3. Select the custom kernel **"Python (Intro to Polars)"** or the `.venv` interpreter in the top right.
4. Run all cells.

---

## Key Results

- **vendor_spend_summary.csv**: Contains the top 5 vendors by spend per country.
- **mismatches.csv**: Lists all discrepancies (> $0.01) between the summary ledger and line-item details, providing actionable audit leads.
