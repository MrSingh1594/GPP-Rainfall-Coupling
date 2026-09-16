# README — GPP–Rainfall Coupling and Entropy-Index Analysis

## 1. Purpose

This folder contains the input datasets, intermediate files, output files, and analysis codes used for:

1. **GPP–rainfall coupling analysis** using MATLAB.
2. **Rainfall variability / entropy-index calculations** using Python.
3. Preparation and storage of the CSV/NetCDF datasets used in these analyses.

The workflow is organized so that the NetCDF (`.nc`) files provide the gridded GPP/rainfall time-series input for MATLAB coupling analysis, while the CSV files are used as input/output for the Python-based calculation of entropy and rainfall variability indices.

---

## 2. General Workflow

```text
Rainfall + GPP datasets
        │
        ├── NetCDF (.nc)
        │       │
        │       ▼
        │   MATLAB coupling analysis
        │       │
        │       ▼
        │   GPP–rainfall coupling results
        │
        └── CSV (.csv)
                │
                ▼
        Python entropy-index analysis
                │
                ├── SVI_ME
                ├── SVI_AE
                └── SVI_IE
                │
                ▼
        CSV output tables
```

---

# 3. MATLAB Analysis Files

### `Kali_Daily_Rainfall_2001_2023_QC.nc`

Quality-controlled daily rainfall dataset for the **Kali basin**, covering 2001–2023.

**Role:** Input NetCDF dataset for rainfall-related analysis and GPP–rainfall coupling.

---

### `Changthang_Daily_Rainfall_2001_2023_QC.nc`

Quality-controlled daily rainfall dataset for the **Changthang region**, covering 2001–2023.

**Role:** Input NetCDF dataset for rainfall-related analysis and GPP–rainfall coupling.

---

### `GPP_Monthly_Kali.nc`

Monthly GPP dataset for the **Kali basin**.

**Role:** Input GPP dataset for coupling GPP with rainfall in MATLAB.

---

### `GPP_Monthly_Changthang.nc`

Monthly GPP dataset for the **Changthang region**.

**Role:** Input GPP dataset for coupling GPP with rainfall in MATLAB.

---

### `MI_analysis_step_1.m`

MATLAB code used for the **GPP–rainfall coupling / mutual-information analysis**.

The MATLAB code uses the relevant rainfall and GPP NetCDF datasets as input and performs the coupling analysis.

**Main input files:**
- `Kali_Daily_Rainfall_2001_2023_QC.nc`
- `Changthang_Daily_Rainfall_2001_2023_QC.nc`
- `GPP_Monthly_Kali.nc`
- `GPP_Monthly_Changthang.nc`

---

# 4. Python Entropy-Index Analysis

The Python files calculate rainfall variability/entropy indices from the rainfall CSV datasets.

The main indices include:

- **SVI_ME** — entropy/variability index associated with mean rainfall intensity.
- **SVI_AE** — entropy/variability index associated with rainfall amount.
- **SVI_IE** — entropy/variability index associated with rainfall occurrence / rainy days.

The CSV files serve as either **input data**, **intermediate data**, or **calculated output**, depending on the filename.

---

## 5. Kali Basin CSV Files

### `Final_IMD_rainfall_Kali_data_2001_2023.csv`

Processed IMD rainfall dataset for the Kali basin.

**Role:** Main rainfall input for Python entropy-index calculations.

---

### `AE_output_IMD_rainfall_Kali_data_2001-2023_final.csv`

Calculated **AE-related entropy/variability results** for the Kali basin.

**Role:** Python analysis output.

---

### `1mm_IE_output_IMD_rainfall_Kali_data_2001-2023_final.csv`

Calculated **IE-related entropy/variability results** using the 1-mm rainfall threshold.

**Role:** Python analysis output.

---

### `SVI_ME_2002_2023_output.csv`

Calculated **SVI_ME results** for 2002–2023.

**Role:** Python analysis output.

---

# 6. Changthang CSV Files

### `Final_IMD_rainfall_Changthang_data_2001_2023.csv`

Processed IMD rainfall dataset for the Changthang region.

**Role:** Main rainfall input for Python entropy-index calculations.

---

### `AE_output_IMD_rainfall_Changthang_data_2001-2023_final.csv`

Calculated **AE-related entropy/variability results** for Changthang.

**Role:** Python analysis output.

---

### `1mm_IE_output_IMD_rainfall_Changthang_data_2001-2023_final.csv`

Calculated **IE-related entropy/variability results** using the 1-mm rainfall threshold.

**Role:** Python analysis output.

---

# 7. Python Notebooks

### `SVI_ME_Calculation.ipynb`

Python notebook used to calculate the **SVI_ME** entropy/variability index.

**Typical workflow:**

```text
Processed rainfall CSV
        ↓
Python calculation
        ↓
SVI_ME calculation
        ↓
CSV output
```

---

### `SVI_IE_AE_Calculation.ipynb`

Python notebook used for calculation of the **SVI_IE and SVI_AE** indices.

**Typical workflow:**

```text
Processed rainfall CSV
        ↓
Rainfall-event / rainfall-amount processing
        ↓
SVI_IE / SVI_AE calculation
        ↓
CSV output
```

---

# 8. File Classification

| File | Format | Main role |
|---|---|---|
| `Kali_Daily_Rainfall_2001_2023_QC.nc` | NetCDF | MATLAB rainfall input |
| `Changthang_Daily_Rainfall_2001_2023_QC.nc` | NetCDF | MATLAB rainfall input |
| `GPP_Monthly_Kali.nc` | NetCDF | MATLAB GPP input |
| `GPP_Monthly_Changthang.nc` | NetCDF | MATLAB GPP input |
| `MI_analysis_step_1.m` | MATLAB | GPP–rainfall coupling code |
| `Final_IMD_rainfall_Kali_data_2001_2023.csv` | CSV | Python rainfall input |
| `Final_IMD_rainfall_Changthang_data_2001_2023.csv` | CSV | Python rainfall input |
| `SVI_ME_Calculation.ipynb` | Python | SVI_ME calculation |
| `SVI_IE_AE_Calculation.ipynb` | Python | SVI_IE/SVI_AE calculation |
| `SVI_ME_2002_2023_output.csv` | CSV | SVI_ME output |
| `AE_output_IMD_rainfall_Kali_data_2001-2023_final.csv` | CSV | Kali AE output |
| `1mm_IE_output_IMD_rainfall_Kali_data_2001-2023_final.csv` | CSV | Kali IE output |
| `AE_output_IMD_rainfall_Changthang_data_2001-2023_final.csv` | CSV | Changthang AE output |
| `1mm_IE_output_IMD_rainfall_Changthang_data_2001-2023_final.csv` | CSV | Changthang IE output |

---

# 9. Recommended Execution Order

## A. GPP–Rainfall Coupling

1. Check the rainfall NetCDF files.
2. Check the monthly GPP NetCDF files.
3. Open `MI_analysis_step_1.m` in MATLAB.
4. Set the input file paths if required.
5. Run the MATLAB coupling analysis.
6. Save/export the resulting coupling or mutual-information results.

## B. Entropy-Index Calculation

1. Use the processed rainfall CSV files as Python inputs.
2. Run `SVI_ME_Calculation.ipynb` for SVI_ME.
3. Run `SVI_IE_AE_Calculation.ipynb` for SVI_IE and SVI_AE.
4. The resulting CSV files contain the calculated entropy/variability indices.
5. These output tables can subsequently be used for statistical analysis, figures, and manuscript tables.

---

# 10. Important Notes

- **NetCDF (`.nc`) files** are the primary gridded/time-series input files for the MATLAB GPP–rainfall coupling workflow.
- **MATLAB (`.m`)** contains the coupling-analysis code.
- **Python notebooks (`.ipynb`)** contain the entropy-index calculation procedures.
- **CSV files** are used for processed rainfall input and for storing Python-calculated results.
- The Kali and Changthang datasets should be kept separate during processing so that basin-specific/regional results are not mixed.
- Before rerunning the calculations, verify the date range, rainfall threshold, missing-value handling, and input/output file paths in the notebooks/code.

---

# 11. Software

The workflow requires:

- **MATLAB** — for GPP–rainfall coupling analysis.
- **Python/Jupyter Notebook** — for entropy-index calculations.
- Standard Python packages required by the notebooks.

