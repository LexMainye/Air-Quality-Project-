##  Air Quality Monitoring in Kenyan Cities 🏙 🇰🇪

This project focuses on monitoring and analyzing air quality data across three major cities in Kenya: **Kisumu**, **Mombasa**, and **Nairobi**. The data is sourced using the **OpenWeather API**, providing detailed environmental pollutant concentrations and the Air Quality Index (AQI) over time.

---
### Background Information to Each city

**Nairobi**

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Nairobi.jpg)

Nairobi is the capital and largest city of Kenya. The city lies in the south central part of Kenya, at an elevation of 1,795 metres (5,889 ft). The name is derived from the Maasai phrase Enkare Nairobi, which translates to 'place of cool waters', a reference to the Nairobi River which flows through the city. The city proper had a population of 4,397,073 in the 2019 census.

---

**Mombasa**

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Mombasa/Mombasa.jpg)

Mombasa ( *mom-BASS-ə; also US:  -⁠BAH-sə*) is a coastal city in southeastern Kenya along the Indian Ocean. It was the first capital of British East Africa, before Nairobi was elevated to capital status in 1907. It now serves as the capital of Mombasa County. The town is known as "the white and blue city" in Kenya. It is the country's oldest (c. 900 A.D.) and second-largest city after Nairobi, with a population of about 1,208,333 people according to the 2019 census.
Mombasa's location on the Indian Ocean made it a historical trading centre, and it has been controlled by many countries because of its strategic location.

---

**Kisumu**

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Kisumu/Kisumu.jpg)

Kisumu ( kee-SOO-moo) is the third-largest city in Kenya located in the Lake Victoria area in the former Nyanza Province. It is the second-largest city after Kampala in the Lake Victoria Basin. The city has a population of slightly over 600,000. The metro region, including Maseno and Ahero, has a population of  1,155,574 people according to the 20189 census. Apart from being an important political city, it is one of the premier industrial and commercial centres in Kenya. It is also an intellectual city with many PhDs.Culturally, Kisumu serves as the centre of the Luo people of East Africa. It was the most prominent urban centre in the pre-colonial and post-colonial period. It remains prominent in the modern era for natives of the Kavirondo region. It was briefly renamed Port Florence, before its name was reverted back.
The city serves as the capital of Kisumu County. 

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

# Dash board Chart Outputs for Each City


## Nairobi.

Air Quality Results:  

| Month    | Plot |
|----------|------|
| January  | ![January](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/January%20Air%20Quality%20Data.png) |
| February | ![February](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/February%20Air%20Quality%20Data.png) |
| March    | ![March](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/March%20Air%20Quality%20Data.png) |
| Early April    | ![April](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/April%20Air%20Quality%20Data%20.png) |

