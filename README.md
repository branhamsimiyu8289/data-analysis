# 28-Day Fitness & Performance Data Analysis

A Python project that explores a sample 28-day fitness log with **Pandas** and **NumPy**. It summarizes steps, sleep, water intake, fasting protocols (OMAD and 2MAD), and bench press performance in a terminal report.

The sample data is defined in the script, so no external dataset is required. This project is for learning and demonstration; its small sample cannot establish health recommendations or cause-and-effect relationships.

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Architecture](#architecture)
- [Dataset Structure](#dataset-structure)
- [Features and Pipeline](#features-and-pipeline)
- [Learning Focus](#learning-focus)
- [Prerequisites and Setup](#prerequisites-and-setup)
- [Usage](#usage)
- [Example Output](#example-output)
- [Potential Improvements](#potential-improvements)
- [Author](#author)

## Overview

The script inspects, filters, analyzes, and reports on 28 days of example fitness data. It answers questions such as:

- How many days had at least 10,000 steps and 7.5 hours of sleep?
- How do average steps, sleep, and bench press loads compare between the recorded fasting protocols?
- How did average steps and bench press loads vary by week?
- What is the relationship between daily steps and bench press load in this sample?

## Project Structure

```text
data-analysis/
├── data-analysis-report.py   # Sample data, analysis, and terminal report
├── requirements.txt          # NumPy and Pandas dependencies
├── .gitignore                # Local environments, secrets, and generated files
└── README.md
```

## Architecture

The script follows a linear analysis workflow:

```text
Sample fitness data
	|
	v
DataFrame inspection
(shape, columns, types, missing values)
	|
	v
Filtering and protocol grouping
	|
	v
NumPy statistics and trend calculations
	|
	v
Weekly breakdown and terminal report
```

## Dataset Structure

The initial exploration DataFrame contains 28 records and seven fields:

| Field | Type | Description |
| --- | --- | --- |
| `day` | Integer | Day number, from 1 to 28 |
| `steps` | Integer | Daily step count |
| `sleep_hr` | Float | Sleep duration in hours |
| `water` | Integer | Daily water intake as recorded in the sample |
| `protocol` | String | Recorded fasting protocol: `OMAD` or `2MAD` |
| `cold_shower` | Boolean | Whether a cold shower was recorded |
| `bench_kg` | Integer | Bench press load in kilograms |

Later analysis sections recreate DataFrames from the same sample and use the columns needed for each calculation.

## Features and Pipeline

1. **Data inspection:** Builds a DataFrame and prints its shape, columns, data types, missing-value count, and first three rows.
2. **Filtering and aggregation:** Counts days with at least 10,000 steps and 7.5 hours of sleep, then groups averages by fasting protocol.
3. **Statistics and trends:** Calculates step-count mean, standard deviation, and quartiles; reports the maximum bench press load and day; compares first- and last-week bench press averages; and calculates the Pearson correlation between steps and bench press load.
4. **Summary report:** Prints overall metrics, a week-by-week breakdown, protocol averages, and the three days with the highest step counts.

## Learning Focus

- **Pandas data manipulation:** DataFrame construction and inspection, boolean filtering, and `groupby()` aggregation.
- **NumPy operations:** Array statistics, percentiles, min/max lookup, and correlation calculations.
- **Basic statistical interpretation:** Descriptive comparisons, week-over-week summaries, and correlation.
- **CLI report formatting:** Formatted strings and readable terminal tables.

## Prerequisites and Setup

- Python 3.8 or newer
- pip

From this directory, create and activate a virtual environment, then install the dependencies.

### Windows PowerShell

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### macOS or Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Usage

Run the report from this directory:

```bash
python data-analysis-report.py
```

The script prints its inspection details and analysis to the terminal. It does not read or write external data files.

## Example Output

The report includes summary statistics, weekly averages, protocol comparisons, and the three highest-step days. For the current sample, the final summary includes:

```text
SMP 28-DAY FITNESS ANALYSIS REPORT

OVERALL METRICS
Days tracked:             28
Total steps:              268,700
Avg daily steps:          9,596
Days hitting 10k:         12/28  (43%)
Avg sleep:                7.6 hrs
Bench press range:        78 to 88 kg
Bench press trend:        +1.7 kg (wk1 to wk4)

PROTOCOL COMPARISON
2MAD: avg steps=9,112, sleep=8.4h, bench=82.2kg
OMAD: avg steps=9,790, sleep=7.2h, bench=83.2kg

TOP 3 STEP DAYS
Day 18: 11,500 steps  (OMAD)
Day 11: 11,200 steps  (OMAD)
Day  4: 11,000 steps  (OMAD)
```

Values are determined by the sample data in the script.

## Potential Improvements

- **External data input:** Load fitness records from CSV, JSON, or a database instead of defining the sample in code.
- **Visualizations:** Add charts for daily trends, metric distributions, and relationships between variables.
- **Interactive dashboard:** Provide interactive filters and visual summaries.
- **Input validation:** Check incoming data for missing values, out-of-range values, and invalid protocols.

## Author

Branham Simiyu