# 🏙️ Metro → ZIP Sale Price & Affordability Explorer

An interactive Streamlit application for exploring U.S. housing affordability across metropolitan areas and ZIP codes.  
This tool supports metro-level comparison, ZIP-level detail analysis, affordability metrics (PTI), basemap switching, and historical trend visualization.

---

## 📊 What This App Visualizes

- 🏡 Median Sale Price  
- 💰 Price-to-Income Ratio (PTI)  
- 📈 Multi-Metro Affordability Comparison Dashboard  
- 🔍 Metro → ZIP drill-down navigation  
- ⏱ ZIP-level historical trend charts (with metro-average overlay)  
- 🗺 Selectable basemap styles (Carto-Positron / OpenStreetMap)  
- 🧭 Quick Metro Search  
- 🏆 Rankings, percentiles, YoY change, affordability labels  

---

## 🚀 Live Demo

Deploy on Streamlit Cloud:

1. Visit: https://share.streamlit.io  
2. Connect your GitHub repo  
3. Set:
   - Repository: haiguo123/data511  
   - Branch: main  
   - Main file: app.py  

---

## 📁 Project Structure

data511/  
│  
├── app.py                  # Main Streamlit UI + logic  
├── charts.py               # Plotly chart builders (metro and ZIP trends)  
├── events.py               # Map click/selection event extraction  
├── geo_utils.py            # Shapefile loading + CBSA/ZCTA polygon merging  
├── config_data.py          # Global settings, PTI logic, color scales  
├── requirements.txt        # Python dependencies  
│  
├── data/  
│   ├── house_ts_agg.csv    # Cleaned sale-price and income dataset  
│   ├── cbsa_shapes.zip     # Metro shapefile bundle  
│   └── zcta_shapes.zip     # ZIP shapefile bundle  
│  
└── .streamlit/  
    └── config.toml         # (Optional) UI theme overrides  

---

## 🗄️ Data Sources

### 1️⃣ House Price & Income Dataset  
File: data/house_ts_agg.csv  
Contains:
- city, city_clean, city_full  
- zip_code_str  
- year  
- median_sale_price  
- per_capita_income  
- lat, lon  

### 2️⃣ CBSA Metro Shapefiles  
File: data/cbsa_shapes.zip  
Used to render metro boundaries.

### 3️⃣ ZCTA ZIP Shapefiles  
File: data/zcta_shapes.zip  
Used to render ZIP polygons within selected metro.

---

## ✨ Key Features

### 🗺 Metro-Level View
- Metro choropleth (PTI or sale price)  
- Hover tooltips with ranking + values  
- Metro ranking and YoY stats  
- Click any metro to enter ZIP mode  
- Basemap switcher (Carto-Positron / OpenStreetMap)  

### 📍 ZIP-Level View
- ZIP choropleth  
- Detailed selected-ZIP metrics:  
  - rank  
  - percentile  
  - YoY change  
  - comparison vs metro average  
- ZIP historical trend line chart  
  - metro average line above chart (custom positioned)  
- Download ZIP-level CSV  

### 📈 Multi-Metro Dashboard
- PTI trend comparison  
- Color-coded affordability bands  
- COVID 2020–2021 percent change bar chart  
- Legend toggle  

---

## 📊 Metric Definitions

### 🏡 Median Sale Price
Average ZIP-level median monthly sale price.

### 💰 Price-to-Income Ratio (PTI)
PTI = median_sale_price / per_capita_income  

Affordability bands:
- 0.0–2.9 → Affordable  
- 3.0–3.9 → Moderately Unaffordable  
- 4.0–4.9 → Seriously Unaffordable  
- 5.0–8.9 → Severely Unaffordable  
- 9.0+ → Impossibly Unaffordable  

---

## ▶️ Run Locally

1. pip install -r requirements.txt
2. streamlit run app.py

---

## 🚢 Deploy to Streamlit Cloud

1. Go to https://share.streamlit.io  
2. Link your GitHub repository  
3. Configure:
   - Branch: main  
   - File: app.py  
4. Deploy and share your public link 🎉  

---

## 🛠 Tech Stack

- Python 3.9+  
- Streamlit  
- Plotly + Mapbox  
- GeoPandas  
- Shapely  
- Pandas / NumPy  
