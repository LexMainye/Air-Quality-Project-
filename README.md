##  Air Quality Monitoring in Kenyan Cities 🏙 🇰🇪

This project focuses on monitoring and analyzing air quality data across three major cities in Kenya: **Kisumu**, **Mombasa**, and **Nairobi**. The data is sourced using the **OpenWeather API**, providing detailed environmental pollutant concentrations and the Air Quality Index (AQI) over time.

---

### 📡 Data Collection

The air quality data was retrieved via the OpenWeather API's Air Pollution endpoints. API requests were made for each of the three cities — **Kisumu**, **Mombasa**, and **Nairobi** — — over a span of 90 consecutive days.

Each response from the API includes the air quality data structured with various pollutant concentrations and the computed AQI. The collected data was stored in a pandas DataFrame for further analysis.

---

### 📊 Dataset Overview

The dataset contains **6048 records** with the following columns:

| Column     | Description |
|------------|-------------|
| `dt`       | Timestamp of the data collection (converted from UNIX timestamp to `datetime64[ns]` format) |
| `city`     | Name of the city (`Kisumu`, `Mombasa`, `Nairobi`) |
| `main.aqi` | Overall Air Quality Index (1 = Good, 5 = Very Poor) |
| `co`       | Carbon Monoxide concentration (μg/m³) |
| `no`       | Nitric Oxide concentration (μg/m³) |
| `no2`      | Nitrogen Dioxide concentration (μg/m³) |
| `o3`       | Ozone concentration (μg/m³) |
| `so2`      | Sulfur Dioxide concentration (μg/m³) |
| `pm2_5`    | Fine Particulate Matter (PM2.5) concentration (μg/m³) |
| `pm10`     | Coarse Particulate Matter (PM10) concentration (μg/m³) |
| `nh3`      | Ammonia concentration (μg/m³) |

The **`dt`** column is initially provided in UNIX timestamp format and was converted into Python's `datetime64[ns]` format using `pd.to_datetime()` for time-based analysis.

---

### 🧠 Key Details

- **Data points**: 6048 total entries
- **Cities monitored**: Kisumu, Mombasa, Nairobi
- **Pollutants covered**: 8 chemical compounds + AQI
- **Datetime conversion**: Performed to allow for resampling, time series plots, and trend analysis

This structured dataset allows for multi-dimensional analysis including temporal trends, inter-city air quality comparison, and pollutant-level deep dives.

---


---

### 📈 Dashboard Results (Built with Dash)

The dashboard was developed using the [Dash](https://dash.plotly.com/) framework and provides an **interactive web interface** for visualizing air quality data over a 90-day period across **Nairobi**, **Mombasa**, and **Kisumu**.

#### 🔧 Dashboard Features

1. **City, Month & Date Filter Controls**
   - A dynamic control panel allows users to select:
     - A **city** from the three available (`city-dropdown`)
     - A **specific month** (`month-dropdown`)
     - A **custom date range** (`date-range`)
   - These filters work together to update all plots in real-time.

2. **📊 Daily Pollution Levels**
   - **Graph ID**: `pollution-graph`
   - Displays line charts for **8 pollutants** (`co`, `no`, `no2`, `o3`, `so2`, `pm2_5`, `pm10`, `nh3`) over the selected period.
   - Each line represents a different pollutant’s hourly concentration.
   - Helps track **pollution spikes** and **multi-pollutant exposure** across time.

3. **📅 Monthly Comparison**
   - **Graph ID**: `monthly-comparison`
   - Shows **monthly average concentration** of a selected pollutant (via `pollutant-dropdown`) for the chosen city.
   - Useful for identifying pollution patterns, seasonal trends, or policy impacts.
   - Bars represent different months, making it easy to spot changes.

4. **📈 Pollutant Trend (Mean, Min, Max)**
   - **Graph ID**: `pollutant-trend`
   - Plots daily **average**, **minimum**, and **maximum** pollutant levels using a line+fill chart.
   - Provides a detailed view of pollutant fluctuation and outliers over time.
   - Helps determine how volatile or stable air quality is in a specific city.

---

### 🔍 Behind the Scenes (Code Overview)

- The dashboard uses `dcc.Dropdown`, `dcc.DatePickerRange`, and `dcc.Graph` from Dash Core Components.
- Three Dash `@callback`s are used to update the visuals based on user input:
  1. `update_graph()` → updates multi-line time series chart of pollutants
  2. `update_monthly_comparison()` → updates the monthly bar chart per pollutant
  3. `update_pollutant_trend()` → shows trend analysis with daily mean, min, max

```python
@app.callback(
    Output('pollution-graph', 'figure'),
    [Input('city-dropdown', 'value'),
     Input('month-dropdown', 'value'),
     Input('date-range', 'start_date'),
     Input('date-range', 'end_date')]
)
# ... Updates daily view with multiple pollutants
```

All charts are rendered using **Plotly**, and the dataset is filtered live using **Pandas**, enabling fast and smooth updates based on UI selections.

---

Would you like me to generate a sample screenshot (mock-up) to show what the dashboard might look like in the README as an image? Or write deployment instructions (`run.py` or `app.py`) + `requirements.txt` next?
