# Metro → ZIP Sale Price & Affordability Explorer

An interactive Streamlit application for exploring U.S. housing affordability across metropolitan areas and ZIP codes.
The tool supports metro-level comparison, ZIP-level detail analysis, interactive maps, affordability metrics, basemap choices, and historical trend visualization.

## What This App Visualizes

- Median Sale Price
- Price-to-Income Ratio (PTI)
- Multi-Metro Affordability Comparison dashboard
- Metro → ZIP drill-down navigation
- ZIP-level historical line charts with metro-average overlay
- Hover tooltips, selection events, ZIP rankings, percentiles
- Selectable basemap styles (Carto-Positron, OpenStreetMap)

## Live Deployment

To deploy on Streamlit Cloud:
1. Visit: https://share.streamlit.io
2. Connect your GitHub repo
3. Set:
   Repository: haiguo123/data511
   Branch: main
   Main file: app.py

## Project Structure

data511/
│
├── app.py                # Main Streamlit application (full UI, map, sidebar)
├── charts.py             # Plotly chart builders (metro trends, ZIP trends)
├── events.py             # Map click-event extraction functions
├── geo_utils.py          # Shapefile loading, CBSA/ZCTA polygon mapping
├── config_data.py        # Shared configs, PTI computation, colors, constants
├── requirements.txt      # Python dependencies
│
├── data/
│   ├── house_ts_agg.csv  # Cleaned sale-price + income dataset
│   ├── cbsa_shapes.zip   # CBSA shapefile bundle for metro map
│   └── zcta_shapes.zip   # ZCTA ZIP shapefile bundle for ZIP-level map
│
└── .streamlit/
    └── config.toml       # Optional Streamlit theme overrides

## Data Sources

1. House Price & Income (local CSV)
   File: data/house_ts_agg.csv
   Includes:
   - city, city_full, city_clean
   - zip_code_str
   - year
   - median_sale_price
   - per_capita_income
   - lat, lon

2. CBSA Metro Shapefiles
   File: data/cbsa_shapes.zip
   Contains .shp/.dbf/.shx/.prj shapefile components.

3. ZCTA ZIP Shapefiles
   File: data/zcta_shapes.zip
   Used to render ZIP boundaries inside a metro.

## Features

### Metro-Level View
- National metro choropleth
- Hover tooltips with PTI or median sale price
- Metro ranking, percentile, YoY comparisons
- Click a metro → enter ZIP-level view
- Sidebar “Quick Metro Search”
- Selectable basemap style

### ZIP-Level View
- ZIP-level choropleth with hover details
- Rich metrics: rank, percentile, YoY, metro deviation
- ZIP trend chart:
  - With metro avg line shown on top of the chart
  - Dynamic annotation placement
- Data download button for selected metro's ZIP dataset

### Multi-Metro Dashboard (City Mode Only)
- Compare PTI trends across selected metros
- Color-coded affordability shades
- Clean legend toggle
- COVID (2020–2021) percent-change bar chart

## Metric Definitions

Price-to-Income Ratio (PTI):
PTI = median_sale_price / per_capita_income

The app also assigns affordability labels:
- 0–2.9: Affordable
- 3.0–3.9: Moderately Unaffordable
- 4.0–4.9: Seriously Unaffordable
- 5.0–8.9: Severely Unaffordable
- 9.0+: Impossibly Unaffordable

## Running Locally

pip install -r requirements.txt
streamlit run app.py

## Deploying on Streamlit Cloud

1. Visit https://share.streamlit.io
2. Link your GitHub repo
3. Configure:
   - Branch: main
   - File: app.py
4. Deploy and share the public URL.

## Tech Stack

- Python 3.9+
- Streamlit
- Plotly (Mapbox)
- GeoPandas
- Shapely
- Pandas, NumPy
