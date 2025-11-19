# Earthquake Data Analysis using Python & MongoDB

This project analyzes global earthquake activity using data from the **USGS Earthquake API**, processed through a Python-based **ELT pipeline** and stored in **MongoDB**.  
The dataset covers the **30 days,  including October 10, 2025**, intentionally selected to keep the dataset manageable while still capturing meaningful seismic patterns.

The project includes data extraction, transformation, geospatial indexing, visualizations, and a full analytical report.

---

## Project Overview

This analysis demonstrates:

- Extracting earthquake data from the **USGS API**
- Loading and structuring the data into a **MongoDB** database
- Applying **geospatial indexing (2dsphere)** for geographic queries
- Exploring:
  - Magnitude distributions  
  - Depth characteristics  
  - Spatial clustering  
  - Time-based trends  
  - Tsunami-flagged events
- Visualizing results with **Matplotlib**
- Creating a final **PDF report** summarizing insights

This project represents a **snapshot analysis** based on a fixed 30-day window ending on **October 10, 2025**.

---

## Repository Contents

| File | Description |
|------|-------------|
| `earthquake_analysis_notebook.ipynb` | Main Jupyter Notebook containing the entire workflow (API extraction → MongoDB loading → transformations → analysis → visualization). |
| `earthquake_analysis_report.pdf` | PDF report summarizing all insights, figures, and conclusions from the notebook. |
| `diagram.png` | Workflow/pipeline diagram used inside the notebook and report. |
| `magnitude.png` | Magnitude distribution plot generated in the notebook. |
| `.gitignore` | Automatically generated file to keep unnecessary files (e.g., checkpoints, cache) out of the repo. |

---

## How to Run the Notebook
Follow these steps to reproduce the analysis:

### 1. Clone the repository
git clone https://github.com/Barbara433/Earthquake-Data-Analysis-using-Python-MongoDB.git

### 2. Install required Python packages
pip install -r requirements.txt

### 3. Start a local MongoDB instance
The notebook expects a local MongoDB server running at:
mongodb://localhost:27017
No authentication is required for this project.

### 4. Open and run the notebook
Start Jupyter Notebook:
jupyter notebook
Then open:  earthquake_analysis_notebook.ipynb
Run all cells from top to bottom to reproduce the complete ELT workflow, data loading, analysis, and visualizations.


## Requirements & Configuration
This project uses the following key packages:
geopandas 1.1.1
pandas 2.3.3
pymongo 4.15.1
requests 2.32.5
cartopy
matplotlib

### Import Setup (as used in the notebook)
import pandas as pd
import requests
import datetime as dt
from pymongo import MongoClient
import cartopy.crs as ccrs
import cartopy.feature as cfeature
import matplotlib.pyplot as plt
from datetime import datetime, timedelta
from pprint import pprint

### pandas display configuration
pd.set_option('display.precision', 2)
pd.set_option('display.max_rows', 30)

### API & Database Configuration
API_URL = "https://earthquake.usgs.gov/fdsnws/event/1/query"
CNX_STR = "mongodb://localhost:27017"
DB_NAME = "earthquakes_db"
COLL_NAME = "earthquakes"

### Fetch last 30 days of data
START_UTC = datetime.utcnow() - timedelta(days=30)

## Notes
The dataset covers the last 30 days up to October 10, 2025.
Running the notebook today will retrieve a different (current) 30-day period from the USGS API.
This project demonstrates:
API integration
Data engineering (ELT pipeline)
Geospatial analysis and 2dsphere indexing
Visual analytics with Python
Use of MongoDB for analytical workloads



