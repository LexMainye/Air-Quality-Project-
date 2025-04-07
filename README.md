Here is the updated `README.md` without emojis:

```markdown
# Air Quality Analysis and Dashboard for Nairobi, Mombasa, and Kisumu

## Project Overview
This project focuses on the **analysis and visualization of air quality data** for three major Kenyan cities: **Nairobi**, **Mombasa**, and **Kisumu**. Using real-time data from the **OpenWeather API**, we explore pollution trends, conduct statistical and machine learning analysis, and create an interactive **Dash** web dashboard.

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

## Jupyter Notebook Analysis

The project was carried out in a Jupyter Notebook, which was rendered for interactive exploration and analysis. The following key components were analyzed:

1. **Air Quality Analysis**:
    - Conversion of timestamps.
    - Extraction of pollutant concentrations for different cities.
    - Filtering and cleaning data.

2. **Data Visualization**:
    - Various plots and figures were created using **Matplotlib**, **Plotly**, and **Seaborn**.
    - Detailed comparison graphs for pollutants across cities and over time.

---

## Dashboard Visualization (Rendered in Jupyter Notebook)

I built an **interactive dashboard** using `Dash` (rendered in Jupyter using `dash_jupyter` or `JupyterDash`):
- Select city, month, and date range
- View daily pollutant levels over time
- Compare monthly pollutant averages
- Explore trends and pollutant behavior

> Screenshot of Dashboard:


## Machine Learning Insights

### 1. Classification (AQI Levels)
- Used `main.aqi` to classify air quality as `Good`, `Moderate`, `Unhealthy`, etc.
- Algorithms: Decision Trees, Random Forests
- Input features: pollutant concentrations (`co`, `no2`, `pm2_5`, etc.)

### 2. Clustering Analysis
- Applied **KMeans** and **DBSCAN** to find pollution pattern clusters by time and location
- Helped identify peak pollution hours and typical pollutant profiles per city

### 3. Anomaly Detection
- Used **Isolation Forest** and **Z-score** methods
- Detected unusual spikes in pollutants like `pm10` and `o3` linked to industrial or traffic events

### 4. Pattern Recognition
- Time series decomposition to separate trend, seasonality, and noise
- Revealed:
  - PM2.5 levels spike in Nairobi on weekdays
  - Coastal cities (Mombasa) have lower NO2 concentrations overall

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
    git clone https://github.com/yourusername/air-quality-kenya.git
    cd air-quality-kenya
    ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Open the notebook:
    ```bash
    jupyter notebook air_quality_analysis.ipynb
    ```

---

## Future Work
- Integrate meteorological data (temperature, wind) for deeper analysis
- Add forecasts using time series models (ARIMA, Prophet)
- Deploy dashboard online (e.g., Heroku, Render)

---

## Author
Made with love by LexMainye

> Feel free to fork, star, or contribute!

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
```

This updated version excludes emojis and maintains the necessary explanations of the project steps, analysis, and insights. Let me know if you need any further adjustments!
