# Campus Water Infrastructure: Predictive Modelling & Sensor Health Diagnostics

> **End-to-end Python pipeline for forecasting daily water usage and automatically diagnosing sensor health across 13 campus meter points.**



## Overview

This project uses historical water pressure and volume data from the **Central University of Technology campus** to:

1. **Forecast next-day water usage** (volume and pressure) using a Random Forest model
2. **Diagnose sensor health** — automatically classifying each meter as Active, Partially Active, or Inactive

The data consisted of hourly readings from 13 meter points, stored across hundreds of CSV files with inconsistent naming and formatting.

## Dataset

| Source | Files | Meter Points |
|--------|-------|-------------|
| Volume CSVs | 545 files | 11 campus meters (FNB Stadium, Park Road Gate, Orion, ZR, etc.) |
| Pressure CSVs | 395 files | 2 pressure sensors (CUT Maintenance Centre, Technikon Residence) |

**Total: 940 CSV files** loaded, cleaned, and merged programmatically.



## Pipeline


Raw CSVs (940 files)
      │
      ▼
Load & Merge (os, glob, pandas)
      │
      ▼
Clean & Fix Timestamps (datetime, pandas)
      │
      ▼
Resample to Daily (volume = sum, pressure = mean)
      │
      ▼
Feature Engineering
  - Lag features: lag1, lag7 (volume & pressure)
  - Rolling averages: 3-day, 7-day (volume & pressure)
  - Time features: year, month, day, day-of-week
      │
      ▼
Train Random Forest Regressors
  - Model 1: Predict next-day Total Volume
  - Model 2: Predict next-day Total Pressure
      │
      ▼
Sensor Health Diagnostics
  - Active / Partially Active / Inactive classification
      │
      ▼
Visualisations (matplotlib)




## Model Results

| Model | MAE | RMSE |
|-------|-----|------|
| Random Forest — Volume | 1263.01 | 4344.10 |
| Random Forest — Pressure | **4.41** | 5.48 |

**Top features for volume prediction:** 3-day rolling average, day of month, 7-day lag  
**Top features for pressure prediction:** Current total pressure (0.47), 3-day rolling pressure average (0.20)



## Sensor Health Report

| Status | Count |
|--------|-------|
| ✅ Active (Healthy) | 4 meters |
| ⚠️ Partially Active (Unreliable) | 2 meters |
| ❌ Inactive (Dead Sensor) | 6 meters |

Dead sensors were automatically detected by a zero-reading ratio threshold — no manual inspection required.



## Tech Stack

| Tool | Purpose |
|------|---------|
| `pandas` | Data loading, cleaning, resampling, merging |
| `os`, `glob`, `shutil` | File navigation and batch loading |
| `datetime` | Timestamp parsing and formatting |
| `scikit-learn` | Random Forest Regressor, train/test split, metrics |
| `numpy` | Numerical operations |
| `matplotlib` | Visualisations |
| `JupyterLab` | Development and documentation |
| `Excel` | Ground truth validation |



## Key Learnings

- Real-world sensor data is messy — inconsistent file names, missing timestamps, and dead sensors are the norm, not the exception
- Rolling average features were the strongest predictors for volume forecasting
- Automating sensor health diagnostics is more scalable than manual inspection at any meaningful data volume



## Author

**Monica Tenene**  
BTech in Computer Systems Engineering | Master's Researcher (IAQ Monitoring), CUT  
[github.com/tenenem](https://github.com/tenenem)
