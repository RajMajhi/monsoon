# 🌧️ MONSOON – LPS Analysis Project

## starts with creating an account in ECMWF

Before anything, create an account in **ECMWF Climate Data Store (CDS)**.

* Go to: [https://cds.climate.copernicus.eu](https://cds.climate.copernicus.eu)
* Register
* Generate your API key
* Save the API key inside:

```bash
~/.cdsapirc
```

Example:

```text
url: https://cds.climate.copernicus.eu/api/v2
key: <your_uid>:<your_api_key>
```

---

# Download

besure to download the latest versions you can download them using python package index

### Install OpenSSL

```bash
pip install pyOpenSSL
```

### Install cdsapi

```bash
pip install cdsapi
```

---

# before strating we need to install some libraries

We will create a clean environment for the project.

## using Anaconda bash

```bash
conda create -n lps_env python=3.10
conda activate lps_env
conda install -c conda-forge xarray netcdf4 cartopy cdsapi scipy matplotlib pandas
```

---

## using jupyter notebook

If working inside notebook:

```python
!pip install xarray netCDF4 cartopy cdsapi scipy matplotlib pandas
```

---

# We going to use

These libraries will be used for monsoon and LPS analysis:

* **xarray** → handling multi-dimensional climate datasets
* **numpy** → numerical computation
* **pandas** → time-series handling
* **matplotlib** → plotting graphs
* **cartopy** → plotting maps
* **scipy** → scientific calculations
* **netCDF4** → reading ERA5 data
* **cdsapi** → downloading ECMWF datasets

---

# download datasets

We will download ERA5 datasets from ECMWF.

Example script:

```python
import cdsapi

c = cdsapi.Client()

c.retrieve(
    'reanalysis-era5-pressure-levels',
    {
        'product_type': 'reanalysis',
        'variable': [
            'u_component_of_wind',
            'v_component_of_wind'
        ],
        'pressure_level': '850',
        'year': '2020',
        'month': '06',
        'day': ['01','02','03'],
        'time': ['00:00','06:00','12:00','18:00'],
        'format': 'netcdf'
    },
    'era5_lps_data.nc'
)
```

---

# Flow of the Project

```
Create ECMWF Account
        ↓
Setup API Key
        ↓
Create Conda Environment
        ↓
Install Required Libraries
        ↓
Download ERA5 Data
        ↓
Load Data using Xarray
        ↓
Visualize using Cartopy
        ↓
Analyze Monsoon Low Pressure Systems (LPS)
```

---

# Goal

* Study monsoon circulation
* Analyze 850 hPa wind fields
* Identify Low Pressure Systems (LPS)
* Perform spatial-temporal analysis

---
