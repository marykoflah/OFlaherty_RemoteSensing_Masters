## 📂 `README_GEE.md` – For Your Google Earth Engine Script

````markdown
# Sentinel-2 NDSI Time Series Export via Google Earth Engine

This script uses Google Earth Engine (GEE) to calculate and export 5-day normalized difference snow index (NDSI) composites using Sentinel-2 imagery.

## 📌 Purpose

To generate cloud-masked and NDSI-filtered median snow cover images over a user-defined Area of Interest (AOI) at a 5-day interval, and export:

- GeoTIFF images of median NDSI values per window
- Tabular summary statistics (mean, standard deviation, pixel count) as a FeatureCollection

## 🛰️ Key Features

- Sentinel-2 Surface Reflectance (`COPERNICUS/S2_SR`)
- Cloud mask filtering using `MSK_CLDPRB`
- Custom AOI and time window
- `normalizedDifference(['B3', 'B11'])` used to compute NDSI
- Optional export to Google Drive as CSV and TIFF

## 🗺️ AOI and Time Range

```js
var AOI = ee.Geometry.Rectangle([-112, 44.5, -108.5, 46]);
// Update these lines for your time period:
var startDate = ee.Date('YYYY-MM-DD');
var endDate = ee.Date('YYYY-MM-DD');
````

## 📤 Exports

* Cloud-free median NDSI raster per time window
* Optional CSV summary per time window

## 🛠️ Author

* **Original GEE Logic**: Adapted by Mary O'Flaherty
* **Base Logic Inspired By**: Common GEE NDSI time series workflows

## 📄 License

This code is intended for research and educational use.

````

---

## 📂 `README_SNOTEL.md` – For Your R Script (Hourly → Midnight)

```markdown
# SNOTEL Midnight-Only Time Series Extractor (USDA AWDB API)

This R script downloads and compiles hourly SNOTEL atmospheric and snow data from the USDA NRCS AWDB REST API, filters for only midnight values, and generates a complete daily time series with missing values handled.

## 📌 Purpose

To extract midnight-calibrated values from the HOURLY SNOTEL dataset for snowpack modeling and atmospheric validation purposes.

## 📊 Variables Extracted

- WTEQ (Snow Water Equivalent)
- SNWD (Snow Depth)
- PREC (Precipitation)
- TAVG (Temperature Average)
- RHUM (Relative Humidity)
- WSPDV (Wind Speed)
- SWINV (Incoming Solar Radiation)

## 📅 Time Period

User-defined via:

```r
start_dateapi <- "YYYY-MM-DD"
end_dateapi   <- "YYYY-MM-DD"
````

## 📂 Output

* A single CSV file with:

  * Column 1: `DateTime` (UTC midnight only)
  * Columns 2+: atmospheric and snow variables
  * Missing data shown as `NA`

## ⚙️ Dependencies

* `httr`, `tibble`, `dplyr`, `purrr`, `glue`, `lubridate`

## 🧠 How It Works

* Builds a REST API query for each variable
* Pulls hourly records, filters for hour == 0
* Joins each variable to a master timestamp
* Outputs a clean, joined time series as `.csv`

## 🛠️ Author & Credits

* **Original Author**: Hayden Libby
* **Modified and Adapted by**: Mary O'Flaherty
* **Institution**: Montana State University, 2025
* **Use Case**: Snowpack estimation and atmospheric error comparison using HRRR and SNOTEL

## 📄 License

This script is intended for academic and non-commercial research use. Please credit appropriately.

```

# README Created with the help of ChatGPT
