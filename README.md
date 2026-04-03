# GORT FITS Archive Processing

## Overview

This project processes astronomical FITS files from the GORT archive and extracts metadata into a structured format (CSV) for analysis.

The notebook (`GORTDB.ipynb`) demonstrates how to:

* Scan a directory of FITS files
* Read FITS headers using `astropy`
* Extract relevant metadata
* Aggregate and clean data
* Export results to a CSV file
* Perform simple analysis (e.g., frame type counts)

---

## Features

* Recursive scanning of FITS files (`.fits`, `.fit`, `.fts`)
* Extraction of header metadata
* Dynamic detection of available FITS header keys
* Data cleaning (e.g., object names)
* Basic summary statistics

---

## Requirements

Install dependencies before running:

```bash
pip install astropy pandas
```

---

## Project Structure

```
GORT_Archive_DB/
│
├── GORT_FITS/              # Folder containing FITS files
├── Gort_summary.csv        # Output CSV file (generated)
└── GORTDB.ipynb            # Main notebook
```

---

## How It Works

### 1. Load FITS Files

The notebook scans a directory and filters valid FITS files:

* Ensures file is valid
* Checks extension (`.fits`, `.fit`, `.fts`)

### 2. Extract Header Information

Each FITS file is opened using:

```python
from astropy.io import fits
```

Metadata is extracted from:

```python
hdul[0].header
```

### 3. Collect Metadata

For each file, relevant header fields are stored in a dictionary and appended to a list.

Example fields include:

* FILENAME
* FRAME_TYPE
* OBJECT
* DATE-OBS
* EXPOSURE

### 4. Save to CSV

The collected data is written to a CSV file using `pandas`.



## Notes

* Paths are currently hardcoded (e.g., `/Users/...`). Update them for your environment.
* Some FITS files may fail to open; errors are handled with try/except blocks.
* Header keys may vary between files.

---

## Future Improvements

* Parallel processing for large datasets
* Database integration (SQLite/PostgreSQL)

