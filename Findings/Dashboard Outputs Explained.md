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

January 2025 

Air Quality Results:  

| Month    | Plot |
|----------|------|
| January  | ![January](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/January%20Air%20Quality%20Data.png) |
| February | ![February](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/February%20Air%20Quality%20Data.png) |
| March    | ![March](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/March%20Air%20Quality%20Data.png) |
| Early April    | ![April](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/April%20Air%20Quality%20Data%20.png) |

Air pollutant types, monthly average levels plots, and trends plots for the month of January 2025:  

| Pollutant (μg/m³)                     | Monthly Average Levels (January 2025) | Trends (January 2025)       |
|---------------------------------------|------------------------------------|--------------------------|
| **co** (Carbon Monoxide)              |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/Monthly%20Average%20CO%20levels%20in%20Nairobi.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/CO%20Trend%20Nairobi.png) |
| **no** (Nitric Oxide)                 |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/NO%20Average%20Monthly%20Trend.png)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/NO%20Trend.png) |
| **no2** (Nitrogen Dioxide)            | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/NO2%20Trends%20Monthly%20.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/NO2%20Trends.png) |
| **o3** (Ozone)                        | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/03%20Monthly%20Average%20.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/03%20Trend.png)|
| **so2** (Sulfur Dioxide)              | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/So2%20Levels%20Average.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/S02%20Trends%20in%20NBO.png)|
| **pm2_5** (Fine Particulate Matter)   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/PM2_5%20Monthly%20Trend.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/pm2_5%20trend%20nbo.png) |
| **pm10** (Coarse Particulate Matter)  | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/pm10%20avg%20lvls%20nbo.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/pm10%20trend%20nbo.png) |
| **nh3** (Ammonia)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/nh3%20monthly%20average%20trend.png)                   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/nh3%20trend%20.png) |



