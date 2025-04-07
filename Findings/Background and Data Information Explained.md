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


