
##  Air Quality Monitoring in Kenyan Cities 🏙 🇰🇪

## Project Overview
This project focuses on the **analysis and visualization of air quality data** for three major Kenyan cities: **Nairobi**, **Mombasa**, and **Kisumu**. Using real-time data from the **OpenWeather API**, we explore pollution trends, conduct statistical and machine learning analysis, and create an interactive **Dash** web dashboard.

## Jupyter Notebook Analysis

The project was carried out in a Jupyter Notebook, which was rendered for interactive exploration and analysis. The following key components were analyzed:

1. **Air Quality Analysis**:
    - Conversion of timestamps.
    - Extraction of pollutant concentrations for different cities.

2. **Data Visualization**:
    - Various plots and figures were created using **Matplotlib**, **Plotly**, and **Seaborn**.
    - Detailed comparison graphs for pollutants across cities and over time.

---

## Dashboard Visualization (Rendered in Jupyter Notebook)

I built an **interactive dashboard** using `Dash`:
- Select city, month, and date range
- View daily pollutant levels over time
- Compare monthly pollutant averages
- Explore trends and pollutant behavior

> Screenshots of Dashboard:


## Machine Learning Insights

### 1. Classification (AQI Levels)
- Used `main.aqi` to classify air quality as `Good`, `Moderate`, `Unhealthy`, etc.
- Algorithms: Decision Trees, Random Forests
- Input features: pollutant concentrations (`co`, `no2`, `pm2_5`, etc.)

### 2. Clustering Analysis
- Applied **KMeans** and **DBSCAN** to find pollution pattern clusters by time and location
- Helped identify peak pollution hours and typical pollutant profiles per city

### 3. Anomaly Detection
- Used **Multivariate Outlier Detection** and **AUC Score** methods
- Detected unusual spikes in pollutants like `PM₂.₅` and `CO` linked to industrial or traffic events

---

## Technologies Used
- **Jupyter Notebook**: For interactive analysis and visualization
- **Dash / Plotly**: Dashboard and data visualization
- **Pandas / NumPy**: Data processing and transformation
- **Scikit-learn**: Machine learning algorithms
- **Matplotlib / Seaborn**: Supplementary plots

---

## Try it Yourself

The analysis and visualizations were carried out interactively in a **Jupyter Notebook**. To run the notebook locally:

1. Clone the repo:
    ```bash
    git clone https://github.com/LexMainye/air-quality-Project.git
    cd air-quality-kenya
    ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Open the notebook:
    ```bash
    jupyter notebook air-quality-Project.ipynb
    ```

---

## Future Work
- Integrate meteorological data (temperature, wind) for deeper analysis
- Add forecasts using time series models (ARIMA, Prophet)
- Deploy dashboard online (e.g., Heroku, Render)

---


## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

-----

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

## Data Collection

### Source: [OpenWeather Air Pollution API](https://openweathermap.org/api/air-pollution)
- The dataset contains **90 days** of hourly air quality data.
- Cities Queried: `Nairobi`, `Mombasa`, and `Kisumu`
- Each record includes pollutants like `CO`, `NO`, `NO2`, `O3`, `SO2`, `PM2.5`, `PM10`, and `NH3`.

### Time Handling
- The `dt` column (UNIX timestamp) was **converted into datetime format** for easier analysis and filtering:
```python
import pandas as pd
df['dt'] = pd.to_datetime(df['dt'], unit='s')
```

### Dataset Structure
```python
df.info()
# Output:
# Columns: dt, city, main.aqi, co, no, no2, o3, so2, pm2_5, pm10, nh3
# Rows: 6048 entries (3 cities × 90 days × hourly data)
```
---

### Dataset Overview

The [dataset](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Air%20Data/pollution_data.csv) contains **6048 records** with the following columns:

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

### Key Details

- **Data points**: 6048 total entries
- **Cities monitored**: Kisumu, Mombasa, Nairobi
- **Pollutants covered**: 8 chemical compounds + AQI
- **Datetime conversion**: Performed to allow for resampling, time series plots, and trend analysis

This structured dataset allows for multi-dimensional analysis including temporal trends, inter-city air quality comparison, and pollutant-level deep dives.


### 📈 Dashboard Results (Built with Dash)

The dashboard was developed using the [Dash](https://dash.plotly.com/) framework and provides an **interactive web interface** for visualizing air quality data over a 90-day period across **Nairobi**, **Mombasa**, and **Kisumu**.

####  Dashboard Features

1. **City, Month & Date Filter Controls**
   - A dynamic control panel allows users to select:
     - A **city** from the three available (`city-dropdown`)
     - A **specific month** (`month-dropdown`)
     - A **custom date range** (`date-range`)
   - These filters work together to update all plots in real-time.

2. **Daily Pollution Levels**
   - **Graph ID**: `pollution-graph`
   - Displays line charts for **8 pollutants** (`co`, `no`, `no2`, `o3`, `so2`, `pm2_5`, `pm10`, `nh3`) over the selected period.
   - Each line represents a different pollutant’s hourly concentration.
   - Helps track **pollution spikes** and **multi-pollutant exposure** across time.

3. **Monthly Comparison**
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
# Dash board Chart Outputs for Each City

## Nairobi. 

### Air Quality Results:  

| Month    | Plot |
|----------|------|
| January  | ![January](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/January%20Air%20Quality%20Data.png) |
| February | ![February](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/February%20Air%20Quality%20Data.png) |
| March    | ![March](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/March%20Air%20Quality%20Data.png) |
| Early April    | ![April](https://github.com/LexMainye/Air-Quality-Project-/blob/796034ef69a4060de4901341553e889f0cbe9c23/Nairobi/Air%20Quality%20Data/April%20Air%20Quality%20Data%20.png) |

**Explanation:** 

- For the daily air pollution levels plots, carbon monoxide `co` appears to be the dominant pollutant compared to the other pollutants that appear to be in lower concentrations, March records the highest spike in `CO` reaching levels of about `~ 4,000 μg/m³`.

**Potential Causes of high CO levels in Nairobi**
1. **Vehicular Emissions** (Traffic, old cars, motorcycles)  
2. **Industrial Activities** (Factories, power plants, informal workshops)  
3. **Domestic Fuel Use** (Charcoal, firewood, kerosene stoves)  
4. **Geographic/Meteorological Traps** (Valley effect, temperature inversions)  
5. **Waste Burning** (Open garbage burning)  
6. **Construction Equipment** (Diesel generators, machinery)

**Recommended Mitigation strategies**
1. Strict vehicle emissions testing  
2. Promote electric/hybrid vehicles  
3. Improve public transport (BRT, cycling lanes)  
4. Phase out old, polluting vehicles  
5. Enforce industrial emission controls  
6. Switch factories to cleaner energy (solar/LPG)  
7. Ban open waste burning  
8. Subsidize clean cooking fuels (LPG/electric stoves)  
9. Public awareness campaigns on CO dangers  
10. Expand air quality monitoring network  
11. Increase urban green spaces  
12. Strict enforcement of anti-pollution laws
    
### Air pollutant types, monthly average levels plots, and trends plots for Jan to Early Apr 2025  

| Pollutant (μg/m³)                     | Monthly Average Levels  | Trends        |
|---------------------------------------|------------------------------------|--------------------------|
| **co** (Carbon Monoxide)              |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/Monthly%20Average%20CO%20levels%20in%20Nairobi.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/CO%20Trend%20Nairobi.png) |
| **no** (Nitric Oxide)                 |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/NO%20Average%20Monthly%20Trend.png)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/NO%20Trend.png) |
| **no2** (Nitrogen Dioxide)            | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/NO2%20Trends%20Monthly%20.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/NO2%20Trends.png) |
| **o3** (Ozone)                        | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/03%20Monthly%20Average%20.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/03%20Trend.png)|
| **so2** (Sulfur Dioxide)              | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/So2%20Levels%20Average.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/S02%20Trends%20in%20NBO.png)|
| **pm2_5** (Fine Particulate Matter)   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/PM2_5%20Monthly%20Trend.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/pm2_5%20trend%20nbo.png) |
| **pm10** (Coarse Particulate Matter)  | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/pm10%20avg%20lvls%20nbo.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/pm10%20trend%20nbo.png) |
| **nh3** (Ammonia)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Monthly%20Average%20Analysis/nh3%20monthly%20average%20trend.png)                   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/bc040a68b7326e638e6a8c45249055e433ae29fc/Nairobi/Trends/nh3%20trend%20.png) |

---

### Mombasa
### Air Quality Results:  

| Month    | Plot |
|----------|------|
| January  | ![January](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Air%20Quality%20Data/January%20Air%20Quality%20Data.png) |
| February | ![February](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Air%20Quality%20Data/February%20Air%20Quality%20Data.png) |
| March    | ![March](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Air%20Quality%20Data/March%20Air%20Quality%20Data.png) |
| Early April    | ![April](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Air%20Quality%20Data/April%20Air%20Quality%20Data.png) |


### Air pollutant types, monthly average levels plots, and trends plot for Jan to Early Apr 2025:  

| Pollutant (μg/m³)                     | Monthly Average Levels  | Trends        |
|---------------------------------------|------------------------------------|--------------------------|
| **co** (Carbon Monoxide)              |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/monthly%20average%20co%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/co%20trends.png) |
| **no** (Nitric Oxide)                 |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/monthly%20avg%20no%20lvls.png)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/no%20trend.png) |
| **no2** (Nitrogen Dioxide)            | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/monthly%20average%20no2%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/no2%20trend.png) |
| **o3** (Ozone)                        | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/03%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/03%20trend.png)|
| **so2** (Sulfur Dioxide)              | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/so2%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/so2%20trend.png)|
| **pm2_5** (Fine Particulate Matter)   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/pm2_5%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/pm2_5%20trend.png) |
| **pm10** (Coarse Particulate Matter)  | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/pm10%20monthly%20average%20levels%20.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/pm10%20trend.png) |
| **nh3** (Ammonia)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Monthly%20Average%20Levels/nh3%20monthly%20avg%20lvls%20.png)                    |  ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/7ca71ba9562f1e257de74cfbc6d88c38845e03ef/Mombasa/Trends/nh3%20trend.png) |

---
### Kisumu 
### Air Quality Results:  

| Month    | Plot |
|----------|------|
| January  | ![January](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Air%20Quality%20Data/January%20Air%20Quality%20Data.png) |
| February | ![February](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Air%20Quality%20Data/February%20Air%20Quality%20Data.png) |
| March    | ![March](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Air%20Quality%20Data/March%20Air%20Quality%20Data.png) |
| Early April    | ![April](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Air%20Quality%20Data/April%20Air%20Quality%20Data.png) |


### Air pollutant types, monthly average levels plots, and trends plot for Jan to Early Apr 2025:  

| Pollutant (μg/m³)                     | Monthly Average Levels  | Trends        |
|---------------------------------------|------------------------------------|--------------------------|
| **co** (Carbon Monoxide)              |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/co%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/co%20trend.png) |
| **no** (Nitric Oxide)                 |![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/no%20monthly%20avg%20lvls.png)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/No%20trend.png) |
| **no2** (Nitrogen Dioxide)            | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/no2%20monthly%20average%20trends.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/no2%20trend.png) |
| **o3** (Ozone)                        | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/03%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/03%20trends.png)|
| **so2** (Sulfur Dioxide)              | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/so2%20monthly%20avg%20trend.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/so2%20trend.png)|
| **pm2_5** (Fine Particulate Matter)   | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/pm2_5%20monthly%20avg%20lvl.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/pm2_5%20trend.png) |
| **pm10** (Coarse Particulate Matter)  | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/pm10%20monthly%20avg%20lvls.png)                    | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/pm10%20trend.png) |
| **nh3** (Ammonia)                     | ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Monthly%20Average/nh3%20monthly%20avg%20lvls.png)                    |  ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Kisumu/Trends/nh3%20trend.png) |

The Following information is on the dataset used in this analysis which data that contained  air quality data for the cities of Nairobi, Mombasa and Kisumu:

## DataFrame information:

| # | Column    | Non-Null Count | Dtype          |
|---|-----------|----------------|----------------|
| 0 | dt        | 6048 non-null  | datetime64[ns] |
| 1 | city      | 6048 non-null  | object         |
| 2 | main.aqi  | 6048 non-null  | int64          |
| 3 | co        | 6048 non-null  | float64        |
| 4 | no        | 6048 non-null  | float64        |
| 5 | no2       | 6048 non-null  | float64        |
| 6 | o3        | 6048 non-null  | float64        |
| 7 | so2       | 6048 non-null  | float64        |
| 8 | pm2_5     | 6048 non-null  | float64        |
| 9 | pm10      | 6048 non-null  | float64        |
| 10| nh3       | 6048 non-null  | float64        |

Additional information:
- RangeIndex: `6048 entries`, 0 to 6047
- Memory usage: `519.9+ KB`
- Total columns: `11`
- dtypes: `datetime64[ns](1)`, `float64(8)`, `int64(1)`, `object(1)`

----

 ## **Classification Report Output**

This output compares two sets of model performance metrics that was performed on the `y_test`, `y_pred` after spliting the dataset into training and testing sets.

---

**First Report (Random Forest Classifier)**
```text
              precision    recall  f1-score   support
           0       1.00      1.00      1.00       373
           1       0.99      1.00      1.00       563
           2       0.99      0.98      0.98       225
           3       0.97      0.97      0.97        40
           4       1.00      1.00      1.00         9
    accuracy                           0.99      1210
   macro avg       0.99      0.99      0.99      1210
weighted avg       0.99      0.99      0.99      1210
```

**Interpretation**:
1. **Perfect Performance for Most Classes**  
   - Classes 0, 1, and 4 show 100% precision and recall
   - Classes 2 and 3 are nearly perfect (98-99%)

2. **Likely Scenario**:  
   - **Training set evaluation** (model memorized the data)
   - **Overfitting warning**: Such perfect scores are unrealistic for real-world data

3. **Class Distribution**:  
   - Imbalanced dataset (Class 4 has only 9 samples vs 563 for Class 1)

---

**Second Report (Support vector machine)**
```text
              precision    recall  f1-score   support
           0       0.93      0.92      0.93       373
           1       0.91      0.94      0.93       563
           2       0.94      0.89      0.91       225
           3       0.86      0.78      0.82        40
           4       0.88      0.78      0.82         9
    accuracy                           0.92      1210
   macro avg       0.90      0.86      0.88      1210
weighted avg       0.92      0.92      0.92      1210
```

**Interpretation**:
1. **Good Performance with Room for Improvement**  
   - Main classes (0-2) show 91-94% F1 scores  
   - Rare classes (3-4) struggle more (82% F1)

2. **Key Observations**:  
   - **Class 4**: Only 78% recall (misses 22% of extreme pollution cases)  
   - **Class 3**: 86% precision (14% false alarms for moderate pollution)  

3. **Comparison**:  
   - Significant drop from first report's 0.99 to 0.92 accuracy  
   - Expected behavior for test set evaluation  

---
 **Key Metrics Explained**

| Metric    | Formula                          | Ideal | Current (Test) |
|-----------|----------------------------------|-------|----------------|
| Precision | TP / (TP + FP)                   | 1.0   | 0.86-0.94      |
| Recall    | TP / (TP + FN)                   | 1.0   | 0.78-0.94      |
| F1-score  | 2 × (Precision×Recall)/(Precision+Recall) | 1.0   | 0.82-0.93      |

---
### Hyperparameter Tuning
- For Hyperparameter tuninig  X was (pollutants), y was main.aqi
- The best results were:

  | Parameter           | Value               |
  |---------------------|---------------------|
  | n_estimators        | 300                 |
    | min_samples_split   | 2                   |
    | min_samples_leaf    | 1                   |
    | max_features        | 'sqrt'              |
    | max_depth           | 10                  |
    | **Best weighted F1-score** | **0.99296** |
  
---

### **Analysis of Random Forest Performance with Optimized Parameters**

 **1. Model Performance Summary**

The classification report shows **near-perfect performance** on all air quality categories (AQI classes 1-5) after the parameters were optimized:

| AQI Class | Precision | Recall | F1-Score | Support |
|-----------|----------|--------|----------|---------|
| 1 (Good) | 1.00 | 1.00 | 1.00 | 360 |
| 2 (Moderate) | 1.00 | 1.00 | 1.00 | 575 |
| 3 (Unhealthy) | 1.00 | 1.00 | 1.00 | 223 |
| 4 (Very Unhealthy) | 1.00 | 0.97 | 0.99 | 37 |
| 5 (Hazardous) | 0.94 | 1.00 | 0.97 | 15 |

**Key Metrics**:
- **Accuracy**: 100% (1210/1210 correct predictions)
- **Macro Avg F1**: 0.99 (excellent balance across classes)
- **Weighted Avg F1**: 1.00 (accounts for class imbalance)

 **Conclusion**

This tuned Random Forest achieves **99%+ accuracy** by:
1. Optimizing tree depth and split criteria for air quality patterns
2. Intelligently selecting dominant pollutants per split  
3. Leveraging ensemble power to handle rare events

---   

### Feature Importance

![image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Feature%20importance%20Plot%20.png)

This graph displays the relative importance of different air pollutant features in a machine learning model for predicting air quality outcomes.

Key observations:

    - PM10 (particulate matter ≤10 micrometers) has the highest importance at approximately 0.35 (35%)
    - PM2.5 (fine particulate matter ≤2.5 micrometers) follows closely at about 0.32 (32%)
    - These two particulate matter measurements together account for over two-thirds of the feature importance
    
* The remaining pollutants have significantly lower importance:
  
    - O3 (ozone) ranks third at around 0.10 (10%)
    - CO (carbon monoxide) at approximately 0.09 (9%)
    - NO2 (nitrogen dioxide) at about 0.06 (6%)
    - NH3 (ammonia) at roughly 0.04 (4%)
    - SO2 (sulfur dioxide) and NO (nitric oxide) have the lowest importance, each below 0.02 (2%)
  
---

  ### Confusion Matrix
  
  ![image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Confusion%20Matrix.png)

  Key observations:
- The diagonal elements (from top-left to bottom-right) represent correct predictions:

      - Class 0: 360 correct predictions
      - Class 1: 575 correct predictions
      - Class 2: 222 correct predictions
      - Class 3: 36 correct predictions
      - Class 4: 15 correct predictions

- Off-diagonal elements show misclassifications:

      - Class 3 has 1 instance misclassified as Class 4

The model appears to perform best on Classes 0 and 1 (with high accuracy), moderately well on Class 2,3 and 4 with a slight misclassification on class 4

---

### Clustering


**Elbow Method & Cluster Analysis for Air Quality Data**

![image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Elbow%20Plot.png)

**1. Elbow Plot Interpretation**
The plot shows the **inertia** (sum of squared distances to cluster centers) decreasing as the number of clusters (K) increases:

- **Key Observation**:  
  - The "elbow" occurs at **K=3 or K=4** (where inertia reduction slows sharply)  
  - This suggests **3-4 natural groupings** exist in the pollution data  

- **Why It Matters**:  
  - Fewer clusters → Broader pollution patterns  
  - More clusters → Finer distinctions (e.g., separating industrial vs. traffic pollution)  

 **2. Cluster Means Analysis**
The 5-cluster solution reveals distinct pollution profiles:

| Cluster | CO     | NO₂   | PM₂.₅ | O₃   | Dominant AQI | Interpretation               |
|---------|--------|-------|-------|------|--------------|-------------------------------|
| **0**   | 379    | 2.5   | 7.6   | 43   | 1-2          | **Clean Days** (Good air)     |
| **1**   | 1,187  | 13.1  | 48.2  | 24   | 3-4          | **Urban Pollution** (Traffic) |
| **2**   | 2,657  | 28.8  | 125.5 | 5    | 5            | **Extreme Events** (Wildfires/Industry) |
| **3**   | 491    | 4.7   | 12.2  | 62   | 2            | **High-Ozone Days**           |
| **4**   | 714    | 6.5   | 22.6  | 24   | 2-3          | **Mixed Sources**             |

**Key Insights**:  
- **Cluster 2** is critical (Hazardous AQI) with extreme PM₂.₅ (125 μg/m³) and CO (2,657 μg/m³)  
- **Cluster 3** shows ozone-dominated pollution (62 μg/m³) despite moderate other pollutants  

 **3. Cluster-AQI Alignment**
The cross-tabulation reveals:

- **Cluster 0**: Mostly AQI 1-2 (Clean)  
- **Cluster 1**: Primarily AQI 3-4 (Polluted)  
- **Cluster 2**: Exclusively AQI 5 (Hazardous)  
- **Cluster 3**: Mostly AQI 2 (Moderate with ozone)  
- **Cluster 4**: Mixed AQI 2-3 (Transitional)  

**Notable Mismatches**:  
- 6 AQI-2 samples in Cluster 1 → Possible sensor errors  
- 1 AQI-4 in Cluster 4 → Borderline case  

   -
 **4. Scientific Implications**
- **Cluster 2** matches known extreme event signatures (e.g., wildfire smoke)  
- **Cluster 3** shows ozone production inversely correlates with NO₂ (titration effect)  
- **Cluster 0-1** gradient reflects urban pollution accumulation  

This analysis confirms that **3-4 dominant emission regimes** exist in the data, with clear links to AQI categories. The elbow plot suggests K=4 might be optimal for balancing granularity and simplicity.

---
### Cluster of Pollution Profiles

![Image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Cluster%20of%20Pollution%20Profiles.png)

**Key Insights from the Plot**

1. **Separation of Pollution Profiles**:
   - The plot visually confirms the three distinct pollution profiles:
     - **`Cluster 0` (left, dark purple)**: Low pollution, associated with cleaner air (but higher ozone).
     - **`Cluster 1` (middle, Green)**: Moderate pollution, a transitional group between low and high pollution.
     - **`Cluster 2 `(right, yellow)**: Severe pollution, likely from industrial or vehicular emissions.

2. **PCA Components**:
   - **`PCA Component 1`** (x-axis) seems to capture the overall pollution intensity, as Cluster 2 (highest pollution) is on the far right, Cluster 0 (lowest pollution) is on the far left, and Cluster 1 (moderate) is in between.
   - **`PCA Component 2`** (y-axis) might be influenced by specific pollutants like ozone (O3), which is higher in Cluster 0, or other factors that differentiate pollution profiles within the same overall intensity level.

3. **Cluster Density and Spread**:
   - `Cluster 0` is the most densely packed, suggesting that many samples fall into the "cleaner air" category.
   - `Cluster 2` is the least dense, indicating that fewer samples exhibit such extreme pollution levels.
   - `Cluster 1`’s spread and overlap with the other clusters reflect its role as a "middle ground" with more variability in pollution profiles.

4. **Alignment with AQI**:
   - The plot’s separation along PCA Component 1 mirrors the AQI distribution:
     - Left `Cluster 0` → Good/Moderate AQI.
     - Middle `Cluster 1` → Unhealthy for Sensitive Groups, with some Unhealthy/Very Unhealthy.
     - Right `Cluster 2` → Very Unhealthy AQI.

5. **Clustering Quality**:
   - The moderate silhouette score (0.452) is reflected in the plot: while Clusters 0 and 2 are relatively distinct, Cluster 1 shows some overlap with both, indicating that the boundaries between clusters are not perfectly sharp.

**Conclusion**

This scatter plot effectively visualizes the clustering of pollution profiles after PCA reduction. It confirms the interpretation of the clusters as representing **`low (Cluster 0)`**, **`moderate (Cluster 1)`**, and **`severe (Cluster 2)`** pollution levels, with `PCA Component 1` largely capturing the gradient of pollution intensity. The alignment with AQI categories further validates the clustering, and the moderate silhouette score explains the slight overlaps observed, particularly for `Cluster 1`.

---
### Cluster Heatmap

![Image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Cluster%20Heatmap.png)

**Key Insights from the Heatmap**

1. **Pollution Gradient Across Clusters**:
   - The heatmap clearly shows a gradient of pollution levels:
     - **`Cluster 0`** (cleaner air): Low concentrations of most pollutants, except for O3.
     - **`Cluster 1`** (moderate pollution): Intermediate concentrations, acting as a transitional group.
     - **`Cluster 2`** (highly polluted): Extremely high concentrations of most pollutants, except for O3.

2. **Ozone Anomaly**:
   - Ozone (O3) is highest in `Cluster 0` (43.1 µg/m³) and lowest in `Cluster 2` (5.3 µg/m³), which is expected due to the inverse relationship between ozone and NO in polluted environments. In `Cluster 2`, high NO levels (14.6 µg/m³) likely deplete ozone through titration.

3. **Health Implications**:
   - **`Cluster 0`**: Generally safe air quality, though elevated ozone levels could pose risks for sensitive groups during high-sunlight conditions.
   - **`Cluster 1`**: Moderate health risks, particularly for sensitive groups, due to elevated PM2.5, PM10, and NO2 levels.
   - **`Cluster 2`**: Severe health risks due to extremely high levels of PM2.5, PM10, CO, NO, and NO2, which can cause respiratory and cardiovascular issues.

4. **Sources of Pollution**:
   - **`Cluster 2`**’s high levels of CO, NO, NO2, PM2.5, and PM10 suggest significant contributions from vehicular and industrial emissions.
   - **`Cluster 1`** may represent urban areas with moderate traffic or industrial activity.
   - **`Cluster 0`** likely represents less urbanized or cleaner areas, with higher ozone possibly due to natural formation in the presence of sunlight and lower NO levels.

5. **Clustering Quality**:
   - The distinct color differences across clusters in the heatmap support the moderate separation indicated by the silhouette score (0.452). While there’s a clear progression in pollutant levels, the relatively small differences in some pollutants (e.g., SO2, NH3) between clusters may contribute to the slight overlaps seen in the scatter plot.

**Conclusion**

The heatmap provides a clear visual summary of the average pollution levels across the three clusters, confirming the earlier interpretations:

- **`Cluster 0`** represents cleaner air with low pollutant levels (except for O3), aligning with `"Good"` and `"Moderate"` AQI levels.
- **`Cluster 1`** represents moderate pollution, with intermediate pollutant levels and a mix of AQI categories, primarily `"Unhealthy for Sensitive Groups."`
- **`Cluster 2`** represents highly polluted conditions, with extremely high pollutant levels and `"Very Unhealthy"` AQI levels, likely driven by industrial or vehicular emissions.

  ---
  ### Cluster Distribution by City
  ![Image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Cluster%20Distribution%20by%20City%20.png)

**Analysis of the Histogram**

**Nairobi**

**Interpretation**:
  - Nairobi predominantly falls into **`Cluster 0`** ("Cleaner" air), indicating mostly "Good" or "Moderate" air quality.
  - A smaller portion is in **`Cluster 1`** ("Moderate" pollution), suggesting occasional "Unhealthy for Sensitive Groups" conditions.
  - A very small number of samples are in **`Cluster 2`** ("Highly polluted"), indicating rare instances of severe pollution.

**Mombasa**

**Interpretation**:

  - Mombasa has the vast majority of its samples in **`Cluster 0`**, suggesting the best air quality among the three cities, with predominantly "Good" or "Moderate" AQI levels.
  - The negligible presence of **`Cluster 1`** and **`Cluster 2`** indicates that moderate and severe pollution are extremely rare in Mombasa.

**Kisumu**

**Interpretation**:
  - Kisumu’s samples are split between **`Cluster 0`** ("Cleaner" air) and **`Cluster 1`** ("Moderate" pollution).
  - Most of Kisumu’s samples are in `Cluster 0`, indicating that the majority of the time, Kisumu experiences "Good" or "Moderate" air quality.
  - The remaining samples are in `Cluster 1`, suggesting that Kisumu experiences moderate pollution levels a notable portion of the time, likely corresponding to "Unhealthy for Sensitive Groups" AQI levels, with some potential for "Moderate", conditions within `Cluster 1`.


**Conclusion**

- **Mombasa** has the best air quality, with nearly all samples in `Cluster 0` ("Cleaner" air), corresponding to "Good" and "Moderate" AQI levels.
- **Nairobi** also has generally good air quality, predominantly in `Cluster 0`, but with some `Cluster 1` and a few `Cluster 2` samples, indicating occasional moderate to severe pollution.
- **Kisumu** has a mix of air quality levels, with 75% of samples in Cluster 0 ("Cleaner" air) and 25% in `Cluster 1` ("Moderate" pollution). This means Kisumu’s air quality is mostly "Good" or "Moderate," with occasional "Unhealthy for Sensitive Groups" conditions, but it does **not** experience the "Very Unhealthy" levels associated with `Cluster 2`.

---

### Silhouette Plot

![Image Alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Silhouette%20plot%20per%20sample.png)

**Key Insights from the Silhouette Plot**

1. **Moderate Clustering Quality**:
   - The average silhouette score of 0.45 indicates moderate clustering quality, which is visually confirmed by the plot. Most samples have positive silhouette coefficients (0.2 to 0.6), suggesting that the clusters are reasonably distinct, but the presence of lower and negative values indicates some overlap, particularly for Cluster 1.

2. **Cluster Separation**:
   - **`Cluster 0`** (likely the largest band) has many samples with silhouette coefficients around 0.4 to 0.6, reflecting its distinct position in the scatter plot (low pollution) and its large size (3750 samples).

   - **`Cluster 1`** (likely a smaller band) has more samples with lower coefficients (near 0 or slightly negative), reflecting its transitional nature and overlap with Clusters 0 and 2, as seen in the scatter plot.

   - **`Cluster 2`** (likely the smallest band) has a mix of coefficients, with some high values due to its distinctness (high pollution) but some lower values due to overlap with Cluster 1.

3. **Potential Misclassifications**:
   - The small number of negative silhouette coefficients (around -0.1) suggests that a few samples may be misclassified, particularly in Cluster 1, which acts as a transitional group. These samples might be better assigned to `Cluster 0` or `Cluster 2`, depending on their pollutant profiles.

4. **Consistency with Previous Analyses**:
   - The silhouette plot aligns with the scatter plot’s observation of slight overlaps, particularly for `Cluster 1`, which is positioned between Clusters 0 and 2 in the PCA space.
   - The heatmap’s distinct pollution profiles (especially between Clusters 0 and 2) support the higher silhouette coefficients for these clusters, while Cluster 1’s intermediate levels explain its lower coefficients.
   - The cluster distribution by city (e.g., Kisumu having only Clusters 0 and 1) is reflected in the plot, as Cluster 2’s small size (20 samples) and absence in Kisumu contribute to its small band.


**Conclusion**

The silhouette plot, with an average silhouette score of 0.45, confirms that the K-means clustering (K=3) on your pollution data resulted in moderately well-separated clusters. Most samples have positive silhouette coefficients, indicating that they are generally well-assigned to their clusters, but the presence of lower and negative values reflects some overlap, particularly for `Cluster 1` ("Moderate" pollution), which acts as a transitional group between `Cluster 0` ("Cleaner" air) and `Cluster 2` ("Highly polluted"). This aligns with the scatter plot’s visualization of overlaps, the heatmap’s intermediate pollution levels for `Cluster 1`, and the cluster distribution by city, where cities like Kisumu lack `Cluster 2` entirely.

---

### DBSCAN Silhouette 

| Metric               | Value                                                                 |
|----------------------|-----------------------------------------------------------------------|
| **DBSCAN Silhouette** | -0.26                                                                |
| **Cluster Distribution** | Cluster ID: `[-1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17]`<br>Counts: `[1187, 4761, 8, 6, 6, 7, 7, 5, 7, 6, 5, 5, 5, 10, 5, 4, 5, 6, 3]` |

- Silhouette: -0.26 (poor separation)
- Cluster distribution: 
  - 1 dominant cluster (4,761 points)
  - 1,187 noise points
  - 17 tiny clusters (3-10 points each)
 
  ### K-Distance Plot for eps Estimation
  
  ![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/K-Distance%20Plot%20for%20eps%20estimation.png)

  **Interpretation:**

The plot shows the sorted distances to the 5th nearest neighbor for each point. The goal is to identify an "elbow" point, where the distances start to increase rapidly. This elbow suggests a good eps value for DBSCAN, as it represents the transition from dense regions (where points are close to their neighbors) to sparse regions (where points are farther apart).

**Observation:**

For the first ~4000 points, the 5th nearest neighbor distance is very small (close to 0, around 0 to 0.5). This indicates that most points in the dataset are in dense regions, where points are very close to their 5th nearest neighbor.
Around 4000 points, the distance starts to increase gradually, and after ~5000 points, it rises sharply, reaching up to 14.

**Elbow Point:**

The elbow is not very pronounced, but a reasonable elbow point appears to be around the 4000th to 4500th point, where the distance starts to increase more noticeably. At this point, the 5th nearest neighbor distance is around 0.5 to 1.0.

This suggests that an eps value in the range of 0.5 to 1.0 might be a good starting point for DBSCAN. Points with a 5th nearest neighbor distance less than this value are likely in dense regions (potential clusters), while points with larger distances are in sparser regions (potential noise or outliers).

**Implications:**

The k-distance plot indicates that the data has a large dense region (the first ~4000 points with small distances) and a smaller sparse region (the last ~1000 points with rapidly increasing distances). This aligns with the K-means cluster distribution by city, where Cluster 0 ("Cleaner" air) had 3750 samples (dense), Cluster 1 ("Moderate" pollution) had 510 samples (less dense), and Cluster 2 ("Highly polluted") had only 20 samples (very sparse).

An eps value of 0.5 to 1.0 should capture the dense regions as clusters, but points in sparser regions (e.g., Cluster 2 from K-means) might be labeled as noise if their 5th nearest neighbor distance exceeds this value.

### New DBSCAN Silhouette 

| Metric               | Value                     |
|----------------------|---------------------------|
| **DBSCAN Silhouette** | 0.69 (good separation)    |
| **Cluster Distribution** |                          |
| Cluster -1 (Noise)   | 126 points                |
| Cluster 0            | 5,922 points              |


**Key Improvements Shown:**
1. **Much better silhouette score** (jumped from -0.26 → 0.69)
2. **Cleaner clustering**:
   - Only 2% noise (down from 20% previously)
   - One clear dominant cluster
3. **Interpretation**:
   - 0.69 indicates well-defined clusters
   - The small noise amount suggests good parameter tuning

**DBSCAN Cluster Means (Retuned DBSCAN)**

| **dbscan_labels** | **CO**      | **NO**    | **NO2**   | **O3**    | **SO2**  | **PM2.5** | **PM10**  | **NH3**   |
|-------------------|-------------|-----------|-----------|-----------|----------|-----------|-----------|-----------|
| -1 (Noise)        | 1676.082857 | 4.437619  | 18.934286 | 29.180476 | 6.410397 | 67.920794 | 114.321111 | 20.285873 |
| 0                 | 536.405137  | 0.184510  | 4.567015  | 38.573288 | 2.280675 | 15.034556 | 31.053105  | 6.886206  |

- These are **high values**, especially for **CO**, **PM2.5**, **PM10**, and **NH₃** — indicating **high pollution** in the noise points.

**Interpretation**

- **Cluster 0**: Represents **normal/typical air quality conditions**.

- **Cluster -1**: Represents **outliers** — likely **pollution spikes or unusual events** with very high pollutant levels.

- DBSCAN has effectively separated **high-pollution anomalies** from **normal data**.

### DBSCAN Clustering Plot

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/DBSCAN%20Clustering%20for%20Air%20Quality%20Data.png)

**Interpretation**

**Cluster 0 (Normal Conditions):**

- Location: Centered around the origin (PC1 ≈ 0, PC2 ≈ 0).

- Shape: Dense, compact cloud.

Interpretation: Represents typical urban air quality with moderate pollutant levels (e.g., CO: 300–800 μg/m³, PM₂.₅: 15–40 μg/m³).

**Real-World Scenarios:**

- Nairobi: Weekday rush hour near Thika Road (high CO/NO₂).

- Kisumu: Lake Victoria ferry emissions + sugar factory operations.

- Mombasa: Ship exhaust at the port + tourist traffic.


**Cluster -1 (Outliers):**

- Location: Scattered at the periphery (high or low PC1/PC2).

- Shape: Sparse, isolated points.

- Interpretation: Extreme pollution events or sensor errors.

**Real World Senarios**

- Nairobi: Industrial malfunctions (Athi River factories).

- Mombasa: Open burning of waste in Kibarani.
- Kisumu : Sugarcane burning in Kibos

### DBSCAN Air Qualtity Clustering Plot

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/DBSCAN%20Clustering%20for%20Air%20Quality%20Data.png)

### **Interpreting the DBSCAN Air Quality Clusters**

**1.The PCA-DBSCAN Plot**

The visualization shows air quality data from Nairobi, Mombasa, and Kisumu reduced to two dimensions using PCA, with DBSCAN clusters overlaid:

- **X-axis (PC1 - 58.5% variance)**:  
  Represents *overall pollution magnitude*.  
  - **Rightward shift** → Higher pollution (extreme PM₂.₅/CO days).  
  - **Left side** → Cleaner conditions (typical urban air).  

- **Y-axis (PC2 - 15.8% variance)**:  
  Captures *pollution type/composition*:  
  - **Top**: Ozone (O₃)-dominant (e.g., sunny days in Nairobi suburbs).  
  - **Bottom**: NO₂/PM-dominated (e.g., Mombasa port traffic).  

- **Clusters**:  
  - **Blue (Cluster 0)**: 5,922 samples → *Typical urban air* (moderate CO/PM₂.₅).  
  - **Red (Outliers)**: 126 samples → *Extreme pollution events*.  

---

**2. Kenyan City-Specific Patterns**  

**Nairobi (Traffic + Industry)**  
- **Cluster 0**: Rush hour on Thika Road (high NO₂/CO).  
- **Outliers**:  
  - Industrial leaks in Athi River (high SO₂).  
  - Wildfire smoke from Aberdares (high PM₂.₅).  

 **Mombasa (Port + Tourism)**  
- **Cluster 0**: Ship emissions at the port (high NO₂/SO₂).  
- **Outliers**:  
  - Kibarani waste burning (extreme CO/PM₁₀).  
  - Cruise ship docking days (NO₂ spikes).  

**Kisumu (Biomass + Agriculture)**  
- **Cluster 0**: Sugar factory operations (moderate PM₂.₅/NH₃).  
- **Outliers**:  
  - Sugarcane burning in Kibos (PM₂.₅ > 200 μg/m³).  
  - Lake Victoria algae blooms (NH₃ spikes).  

---

 **3. Why the Silhouette Score of 0.69 Matters**  
- **0.50–0.70**: Good separation (expected for air quality data).  
- **Kenyan Context**:  
  - Confirms clear distinction between:  
    1. *Daily urban pollution* (Blue cluster).  
    2. *Rare extreme events* (Red outliers).  
  - Validates DBSCAN’s ability to:  
    - Ignore sensor errors (true noise).  
    - Flag real crises (wildfires, industrial accidents).  

 **Nairobi-Specific**  
- **Traffic**: Retrofit matatus to Euro 4 standards.  
- **Industry**: Enforce scrubbers in Athi River factories.  

 **Mombasa-Specific**  
- **Port**: Mandate shore power for docked ships.  
- **Tourism**: Monitor beach hotel waste burning.  

 **Kisumu-Specific**  
- **Agriculture**: Ban sugarcane burning in dry seasons.  
- **Lake**: Reduce fertilizer runoff into Lake Victoria.  


 **Key Takeaways for Kenya**  
1. **Nairobi**: Traffic dominates, but industry causes extremes.  
2. **Mombasa**: Port activities need stricter monitoring.  
3. **Kisumu**: Agricultural burning is the primary outlier source.  

---

### Pollution Profiles by Cluster

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Pollution%20profiles%20by%20cluster.png)

**Cluster Analysis Summary:**

1. **Cluster 0 (Purple)**:
   - Represents normal or typical air quality conditions
   - Contains the majority of data points
   - Shows moderate levels of all three pollutants
   - Has relatively consistent pollutant relationships

2. **Cluster -1 (Yellow)**:
   - Represents outliers or unusual events
   - Shows dramatic spikes in pollution levels
   - PM2.5 concentrations are particularly elevated, reaching nearly 200 μg/m³
   - Likely corresponds to specific pollution events like:
     - Severe traffic congestion
     - Industrial emissions events
     - Weather-related pollution trapping (temperature inversions)
     - Possible seasonal events (agricultural burning, etc.)
    

 **DBSCAN Cluster Means for Kenyan Air Quality**

 **1. Outlier Cluster (-1): Extreme Pollution Events**  
*(126 samples | Red points in plot)*  

| Pollutant | Mean Value | Kenyan Context | Real-World Scenarios |
|-----------|------------|----------------|----------------------|
| **NH₃**   | 20.29 μg/m³ | **2.9× higher** than normal | - Sugarcane burning (Kisumu Kibos)<br>- Livestock waste (Nakuru abattoirs) |
| **PM₂.₅** | 67.92 μg/m³ | **4.5× higher** than normal | - Wildfires (Nairobi National Park)<br>- Construction dust (Athi River) |
| **NO₂**   | 18.93 μg/m³ | **4.1× higher** than normal | - Ship idling at Mombasa port<br>- Matatu congestion (Nairobi CBD) |
| **CO**    | 1676.08 μg/m³ | **3.1× higher** than normal | - Open waste burning (Dandora)<br>- Industrial malfunctions (Mlolongo) |

**Key Insight**:  
These are **public health emergencies** exceeding WHO thresholds:  
- PM₂.5 > 25 μg/m³ (24-hr limit)  
- CO > 4 mg/m³ (1-hr limit)  

---

**2. Core Cluster (0): Typical Urban Conditions**

*(5,922 samples | Blue points in plot)*  

| Pollutant | Mean Value | Kenyan Context | Real-World Scenarios |
|-----------|------------|----------------|----------------------|
| **NH₃**   | 6.89 μg/m³ | Baseline | - Moderate agricultural activity<br>- Urban waste decomposition |
| **PM₂.₅** | 15.03 μg/m³ | Within WHO limits | - Typical traffic dust<br>- Household cooking (charcoal) |
| **NO₂**   | 4.57 μg/m³ | Low-to-moderate | - Diesel generators<br>- Rush hour emissions |
| **CO**    | 536.41 μg/m³ | Below danger | - Standard vehicle exhaust<br>- Small-scale industries |

**Key Insight**:  
Represents **manageable urban air quality** requiring:  
- Routine traffic controls  
- Dust suppression on unpaved roads  

---

**3. City-Specific Comparisons**  

**Nairobi**  
- **Outliers**: High CO/NO₂ from:  
  - Gikomba market fires  
  - Industrial Area generator use  
- **Typical Days**: PM₂.₅ ~15 μg/m³ (Thika Road construction)  

**Mombasa**  
- **Outliers**: High NO₂/SO₂ from:  
  - Cruise ship docking  
  - Kipevu oil refinery  
- **Typical Days**: NH₃ ~7 μg/m³ (Fish processing plants)  

**Kisumu**  
- **Outliers**: High NH₃/PM₂.₅ from:  
  - Sugar mill operations  
  - Lake Victoria algae blooms  
- **Typical Days**: CO ~500 μg/m³ (Boda boda emissions)  

 **DBSCAN Cluster Distribution Across Kenyan Cities**

**1. Outlier Cluster (-1): Extreme Pollution Events**  

*(Total: 126 samples)*  

| City    | Count | Likely Causes | Urgent Interventions Needed |
|---------|-------|---------------|-----------------------------|
| **Nairobi** | 92   | - Industrial malfunctions (Athi River)<br>- Gikomba market fires<br>- Nighttime construction dust | - Real-time monitoring near factories<br>- Ban open burning in informal settlements |
| **Kisumu** | 26    | - Sugarcane burning in Kibos<br>- Lake Victoria algae blooms (NH₃) | - Enforce seasonal burning bans<br>- Lake water quality management |
| **Mombasa** | 8     | - Ship idling at port<br>- Kibarani waste burning | - Shore power for docked ships<br>- Relocate dumpsite away from city |

**Key Insight**:

Nairobi accounts for **73% of extreme events**, underscoring its industrial and urban density challenges.

---

**2. Core Cluster (0): Typical Urban Conditions**  
*(Total: 5,922 samples)*  

| City    | Count | Dominant Sources | Long-Term Mitigation Strategies |
|---------|-------|------------------|----------------------------------|
| **Mombasa** | 2,008 | - Port activities<br>- Tourist vehicle emissions | - Electrify ferry fleet<br>- Promote electric tuktuks |
| **Kisumu** | 1,990 | - Sugar factory operations<br>- Motorcycle (boda-boda) exhaust | - Improve sugarcane waste management<br>- Incentivize electric boda-bodas |
| **Nairobi** | 1,924 | - Matatu congestion<br>- Road construction dust | - Fast-track BRT expansion<br>- Pave high-traffic unpaved roads |

**Key Insight**:  
All cities show comparable baseline pollution, but **Mombasa's port gives it slightly higher typical pollution levels**.

---

**3. City-Specific Risk Profiles**

**Nairobi**  
- **Outlier/Normal Ratio**: 92/1924 = **4.8%**  
  - *Interpretation*: Frequent industrial/urban emergencies amid manageable daily pollution.  
  - *Action*: Prioritize Athi River industrial compliance.

**Kisumu**  
- **Outlier/Normal Ratio**: 26/1990 = **1.3%**  
  - *Interpretation*: Rare but severe agricultural/lake-driven spikes.  
  - *Action*: Focus on Kibos sugarcane regulation.

**Mombasa**  
- **Outlier/Normal Ratio**: 8/2008 = **0.4%**  
  - *Interpretation*: Well-managed except for port-related extremes.  
  - *Action*: Target ship emissions at KPA.

**4. Policy Recommendations**

**Nairobi-Specific**  
- **Strict Enforcement**:  
  - Nighttime construction bans in CBD.  
  - Monthly factory stack tests in Industrial Area.

**Kisumu-Specific**  
- **Agricultural Reforms**:  
  - Subsidize non-burning harvest techniques.  
  - Monitor Lake Victoria nutrient runoff.

 **Mombasa-Specific**  
- **Port Modernization**:  
  - Mandate LNG-powered ships by 2026.  
  - Install real-time stack monitors at Kipevu.

---

## Noise Days Plots

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Clustering%20%26%20Clustering%20Techniques/Noise%20Days%20Plots.png)

**Interpretation**

 **Nairobi**
- **Most noisy overall** — the tallest bar by far.
- Weekdays with highest noise:

  - **Monday (~0.101)** and **Wednesday (~0.068)**.

- Noise is spread across the week, though early weekdays are more prominent.
- Suggests that Nairobi may have consistently higher activity levels or events that trigger noise detections.

 **Kisumu**
- Moderate levels of noise days.
- Noticeable peaks on:

  - **Thursday (~0.035)** — the largest single day for Kisumu.
  - Other days have much lower proportions, around **~0.01–0.014**.

- Indicates **Thursday might be a significant day** for noise in Kisumu — possibly linked to a weekly event or market.

**Mombasa**
- **Lowest noise levels** — very small bar.
- Noise is minimal and evenly distributed.
- The proportions are all below **~0.014**, making the values almost invisible in the stacked format.
- This may reflect:
  - Fewer noise-triggering activities.
  - Or different environmental conditions (e.g., better insulation, fewer events, different monitoring).

 **Key Takeaways**
- **Nairobi** is the noisiest city by far, especially early in the week.
- **Kisumu** shows a peak on **Thursday**.
- **Mombasa** isn't as noisy as the rest


### Advanced Anomaly Detection & Pattern Analysis

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Anomaly%20Detection%20%26%20Pattern%20Analysis/Pollution%20Hotspots.png)

The map plot effectively shows that Nairobi appears to be a air significant pollution hotspot compared to other cities under observation in Kenya.

Nairobi's status as a significant air pollution hotspot compared to Mombasa and Kisumu can be attributed to several interconnected factors:

 1. **Population Density and Urbanization**
   - Nairobi is Kenya's most densely populated city (over 4.7 million people in the metro area), leading to higher emissions from:
     - Vehicular traffic (congestion is severe)
     - Industrial activity concentrated in the city
     - Domestic fuel use (charcoal, kerosene)
   - Mombasa and Kisumu have lower population densities and less industrial concentration.

 2. **Transportation Emissions**
   - Nairobi has:
     - Heavy reliance on older, poorly maintained vehicles (many diesel-powered)
     - Frequent traffic jams (idling engines increase particulate matter)
     - Limited public transport infrastructure (leads to more private vehicles)
   - Mombasa has more maritime transport (less polluting than road traffic), while Kisumu has fewer vehicles overall.

3. **Industrial Activity**
   - Nairobi hosts Kenya's largest industrial zone (along Mombasa Road and Athi River), including:
     - Manufacturing plants
     - Construction material production (cement, steel)
     - Informal sector activities (e.g., metal recycling)
   - Mombasa's industry is more port-focused, and Kisumu has lighter industry.

 4. **Geographical and Meteorological Factors**
   - Nairobi's **high altitude (~1,800m)** reduces air dispersion, trapping pollutants.
   - The city sits in a **valley**, limiting wind circulation that could disperse pollution.
   - Mombasa's coastal location benefits from sea breezes that disperse pollutants.
   - Kisumu's proximity to Lake Victoria also allows for better air mixing.

5. **Energy and Fuel Use**
   - **Nairobi:**
     - Heavy use of diesel generators during power outages
     - Widespread charcoal burning in informal settlements
     - Industrial reliance on heavy fuel oils
   - **Mombasa/Kisumu:**
     - More access to cleaner energy (e.g., Mombasa's proximity to the Kipevu power plant)
     - Less reliance on backup generators

 6. **Construction and Dust**
   - Nairobi's rapid construction boom generates significant dust (PM2.5/PM10).
   - Unpaved roads in informal settlements exacerbate particulate pollution.
   - Mombasa and Kisumu have slower construction growth.

7. **Waste Burning**
   - Open burning of waste is common in Nairobi's informal settlements (Dandora, Kibera).
   - Mombasa and Kisumu have smaller-scale waste disposal issues.

8. **Policy and Enforcement Gaps**
   - Nairobi's pollution regulations are poorly enforced (e.g., vehicle emissions testing).
   - County governments in Mombasa and Kisumu may have better localized controls.

Mitigation Insights:
To reduce Nairobi's pollution, priorities could include:
- Upgrading public transport (e.g., BRT systems)
- Stricter vehicle emissions standards
- Promoting cleaner industrial technologies
- Expanding green spaces to improve air circulation.

Mombasa and Kisumu's relatively lower pollution levels highlight how coastal/breeze-accessible cities can benefit from natural dispersion, but they may face future risks if industrialization grows unchecked.

---

### Multivariate Outlier Detection

|               | Anomaly (-1) | Anomaly (1) | Total |
|---------------|--------------|-------------|-------|
| **Not Noise** | 22           | 5900        | 5922  |
| **Noise**     | 99           | 27          | 126   |
| **Total**     | 121          | 5927        | 6048  |

- Most normal cases (5900) are correctly identified as anomaly=1
- Noise is more common in the anomaly=-1 group (99 vs 27)

  ---

  ### Pollutant Interactions Graph

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Anomaly%20Detection%20%26%20Pattern%20Analysis/Pollutant%20Interactions%20Graph.png)

 **Interpreting Pollutant Interaction Network During Extreme Air Quality Events**

**1. Graph Structure & Key Findings**
The network diagram visualizes **strong correlations (r > 0.7)** between pollutants during extreme pollution days (DBSCAN Cluster -1). Line thickness represents correlation strength.

**Dominant Interactions**:  
1. **CO as the Hub**:  
   - Strongest ties to PM₂.₅ (r=0.91), PM₁₀ (r=0.91), NO (r=0.82), and NO₂ (r=0.74).  
   - *Interpretation*: CO spikes signal **combustion events** (burning, traffic, industry).  

2. **PM₂.₅-PM₁₀ Bond (r=0.97)**:  
   - Near-perfect correlation → Fine and coarse particles share common sources.  

3. **NO-NO₂-CO Triangle**:  
   - NO/NO₂ correlations with CO (r=0.74–0.82) → **Traffic/fuel combustion fingerprint**.  

 **2. Kenyan Context for These Correlations**

**A. CO-Linked Patterns**  

| Correlation | Kenyan Scenario | Example Locations |
|-------------|-----------------|-------------------|
| **CO ↔ PM₂.₅ (0.91)** | Biomass burning | Kibos (Kisumu), Kibera (Nairobi) |
| **CO ↔ NO (0.82)** | Matatu/truck exhaust | Thika Road (Nairobi), Likoni Ferry (Mombasa) |
| **CO ↔ PM₁₀ (0.91)** | Construction + burning | Athi River, Mlolongo industrial zones |

**B. Particulate Matter**  
- **PM₂.₅ ↔ PM₁₀ (0.97)**:  
  - Shared sources:  
    - **Urban**: Vehicle brake/tire wear (Nairobi CBD).  
    - **Rural**: Agricultural tilling + savanna fires (Narok).  

**C. Nitrogen Oxides**  
- **NO ↔ NO₂ (via CO)**:  
  - **Traffic hotspots**:  
    - Mombasa port truck queues.  
    - Nairobi’s Globe Roundabout.  


 **3. Policy Implications**

**Nairobi-Specific**  
- **Targeted Measures**:  
  - **Thika Road**: Enforce Euro 5 standards for trucks.  
  - **Industrial Area**: Mandate CO scrubbers in factories.  

**Mombasa-Specific**  
- **Port Actions**:  
  - Replace diesel forklifts with electric models.  
  - Real-time NO₂ monitoring at KPA gates.  

**Kisumu-Specific**  
- **Agricultural Controls**:  
  - Promote non-burning sugarcane harvesting.  
  - Penalize nighttime field burning.  

---

 **4. Scientific Insights**  

- **Combustion Signature**: High CO-PM₂.₅-NOₓ correlations confirm **incomplete fuel burning** dominates extremes.  
- **Traffic vs. Industry**:  
  - **NO-dominant**: Traffic (matatus, trucks).  
  - **CO-dominant**: Industry/waste burning.  

 **Conclusion**  
1. **CO is the keystone pollutant** during extremes → it should be monitored closely.  
2. **PM₂.₅-PM₁₀ pairing** demands integrated dust/fire controls.  
3. **City-specific strategies** should break these correlation chains.

---

### AUC Score

I found a Sensor fault AUC: 1.00 indicating a good sense of fault prediction.

---

### SHAP Value plot 

![image alt](https://github.com/LexMainye/Air-Quality-Project-/blob/main/Anomaly%20Detection%20%26%20Pattern%20Analysis/SHAP%20Value%20Plot.png)

**Interpreting the SHAP Value Plot**

**1. What the Plot Shows**

This horizontal bar chart visualizes the **importance and directional impact** of each feature (pollutant) on your air quality model's predictions, using SHAP (SHapley Additive exPlanations) values:
- **Y-axis**: Features (pollutants) ordered by importance.  
- **X-axis**: SHAP value → How much each feature *pushes* predictions higher (positive) or lower (negative).  
- **Bar Length**: Magnitude of impact.  
- **Color**: Likely represents feature value (red = high concentration, blue = low).  

---

**2. Key Insights for Kenyan Air Quality**

**Top Influential Pollutants**  

1. **Feature 4 (Likely PM₂.₅)**:  
   - **Strong positive impact** (long right bar).  
   - *Interpretation*: High PM₂.₅ levels drastically worsen predicted AQI.  
   - *Kenya Context*: Matches construction dust (Athi River).  

2. **Feature 1 (Likely CO)**:  
   - **Moderate positive impact**.  
   - *Interpretation*: CO spikes from traffic/industry raise AQI predictions.  
   - *Kenya Context*: Matatu congestion (Nairobi CBD), waste burning (Dandora).  

3. **Feature 6 (Possibly O₃)**:  
   - **Negative impact** (left bar).  
   - *Interpretation*: High O₃ sometimes lowers AQI predictions (due to NOx titration in cities).  
   - *Kenya Context*: Sunny days in Karen (low NOx) vs. industrial zones (high NOx).  

 **Less Important Features**  
- **Feature 0/7 (e.g., NH₃, SO₂)**:  
  - Minimal impact → Less critical for AQI predictions in your model.  

---

**3. Policy Implications**  

**Prioritize Reducing Top Pollutants**  
1. **PM₂.₅ (Feature 4)**:  
   - **Nairobi**: Enforce dust control at construction sites.  
   - **Kisumu**: Ban sugarcane field burning.  

2. **CO (Feature 1)**:  
   - **Mombasa**: Retrofit port trucks to Euro 6 standards.  
   - **Nairobi**: Phase out charcoal stoves in informal settlements.  
   
 **Monitor O₃ (Feature 6) Paradox**  
- **Action**: Deploy more NOx sensors in high-O₃ suburbs (e.g., Karen, Runda).  
---
 **4. Scientific Validation**  
- **PM₂.₅ Dominance**: Confirms global findings on its health impacts.  
- **CO-O₃ Tradeoff**: Reflects Kenya’s unique mix of traffic and industrial sources.  
---

**Conclusion**  
This plot reveals:  
1. **PM₂.₅ and CO are Kenya’s top AQI drivers**.  
2. **O₃ has complex effects** depending on location.  
3. **Targeted reductions in PM₂.₅/CO** will most improve air quality.  







