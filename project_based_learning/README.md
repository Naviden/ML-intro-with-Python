# Python for Professionals

A hands-on Python course built for business people with no programming experience.  
No theory-first. No abstract exercises. Two real projects, 15 hours, skills you can use on Monday.

---

## What this is

Most Python courses start with data types, then strings, then lists — topics in isolation, divorced from any real purpose. This course does the opposite: it starts with a problem you'd actually face at work, and introduces concepts only when the project needs them.

By the end you will have written two complete data pipelines from scratch. Both produce files you could open in Excel and share with a colleague today.

---

## Who this is for

- Professionals in business, finance, sales, or operations
- No programming experience required — none at all
- Comfortable opening a file and following instructions
- Curious about automation but not sure where to start

---

## What you will build

### Project 1 — Sales Report Cleaner
You receive a messy CSV export from a CRM. Dates are in three different formats, region names are inconsistently capitalised, amounts are stored as text with a € symbol, and some rows have missing data. You write a Python script that cleans everything automatically and produces a tidy regional summary — the kind of thing you'd normally do by hand in Excel, now running in under a second.

**Concepts introduced:** variables, data types, strings, lists, dictionaries, for loops, if/else, file reading and writing

**Output:** `sales_summary_by_region.csv` — total sales, transaction count, and average deal size per region

---

### Project 2 — Monthly Expense Analyser
Five departments have submitted expense files. Each file has the same structure but the data is messy in different ways — two files contain a formatting bug that would crash a naive script. You write a pipeline that finds all the files automatically, loads and merges them, handles errors gracefully, analyses spend by department and category using pandas, flags unusually large expenses for review, and exports multiple summary reports.

**Concepts introduced:** functions, error handling (try/except), sets, the `os` and `pandas` libraries, boolean filtering, DataFrame operations

**Output:** four CSV files — full cleaned dataset, department summary, category summary, flagged anomalies

---

## Files in this repository

```
├── README.md
│
├── project-1-sales-cleaner/
│   ├── sales_report_cleaner.ipynb   ← the notebook (work here)
│   └── sales_data_raw.csv           ← the messy input file
│
└── project-2-expense-analyser/
    ├── expense_analyser.ipynb       ← the notebook (work here)
    ├── expenses_sales.csv
    ├── expenses_marketing.csv
    ├── expenses_operations.csv
    ├── expenses_hr.csv
    └── expenses_it.csv
```

---

## Getting started

### 1. Install Python

If you do not have Python installed, download it from [python.org](https://www.python.org/downloads/).  
Choose the latest version. During installation, check the box that says **"Add Python to PATH"**.

To confirm it worked, open a terminal and run:

```
python --version
```

You should see something like `Python 3.11.4`.

### 2. Install Jupyter and pandas

In the same terminal, run:

```
pip install notebook pandas
```

This installs Jupyter (the environment where you will write and run code) and pandas (used in Project 2).

### 3. Download the course files

Click the green **Code** button at the top of this page, then **Download ZIP**.  
Unzip the folder somewhere easy to find — your Desktop is fine.

### 4. Open Jupyter

In your terminal, navigate to the folder you just unzipped:

```
cd path/to/the/folder
```

Then start Jupyter:

```
jupyter notebook
```

A browser window will open. Click on a project folder, then open the `.ipynb` file inside.

> **Windows users:** if `jupyter notebook` does not work, try `python -m notebook` instead.

---

## How the notebooks work

Each notebook is divided into steps. Every step has:

- A markdown cell explaining what you are about to do and why
- A code cell with the Python to run (or sometimes a gap for you to fill in)
- A reflection or question after the output

**Run a cell** by clicking on it and pressing `Shift + Enter`.  
**Run all cells in order** — Jupyter remembers what ran before, so skipping cells causes errors.

Some cells in Project 2 contain `# YOUR CODE HERE` — these are exercises. Read the hints above the comment and write your own solution before looking anything up.

---

## Concepts covered

| Topic | Project 1 | Project 2 |
|---|:---:|:---:|
| Variables and data types | ✓ | ✓ |
| Strings | ✓ | ✓ |
| Lists | ✓ | ✓ |
| Dictionaries | ✓ | ✓ |
| Sets | | ✓ |
| Control structures (if, for, continue) | ✓ | ✓ |
| Functions | | ✓ |
| Error handling (try/except) | | ✓ |
| File reading and writing | ✓ | ✓ |
| Libraries (csv, os, pandas) | ✓ | ✓ |
| pandas DataFrames and groupby | | ✓ |

---

## Common problems

**FileNotFoundError** — Python cannot find the CSV file.  
Make sure the CSV files are in the same folder as the notebook. In Jupyter, check File → Open to see what folder you are in.

**ModuleNotFoundError: No module named 'pandas'** — pandas is not installed.  
Run `pip install pandas` in your terminal, then restart the Jupyter kernel (Kernel → Restart).

**The notebook runs but produces no output** — you may have run the cells out of order.  
Go to Kernel → Restart & Run All to start fresh.

**PermissionError when saving a CSV** — the output file is open in Excel.  
Close it in Excel, then re-run the export cell.

---

## Licence

This material is free to use, share, and adapt for educational purposes.  
If you use it in your own teaching, a mention is appreciated but not required.
