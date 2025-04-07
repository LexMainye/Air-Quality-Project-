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




