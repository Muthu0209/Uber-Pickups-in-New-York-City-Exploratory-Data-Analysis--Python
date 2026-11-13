# Uber-Pickups-in-New-York-City-Exploratory-Data-Analysis--Python
Exploratory data analysis of Uber pickups across New York City boroughs (January to June 2015), looking at how demand changes with time, location, weather and holidays.

## Business Context

Ridesharing demand is volatile. It shifts with time of day, location, weather and local events. The goal of this project is to find patterns in those fluctuations so supply can be matched to demand.

## Dataset

`Uber_Data.csv` has **29,101 rows and 13 columns**. Each row is the number of pickups in one borough in one hour, with the weather at that time.

| Column | Description |
|---|---|
| `pickup_dt` | Date and time of pickup (hourly) |
| `borough` | NYC borough of the pickup (Bronx, Brooklyn, EWR, Manhattan, Queens, Staten Island) |
| `pickups` | Number of pickups in that borough in that hour |
| `spd` | Wind speed (mph) |
| `vsb` | Visibility (miles) |
| `temp` | Temperature (°F) |
| `dewp` | Dew point (°F) |
| `slp` | Sea level pressure |
| `pcp01` / `pcp06` / `pcp24` | Liquid precipitation over 1, 6 and 24 hours |
| `sd` | Snow depth |
| `hday` | Holiday flag (Y/N) |

**Period covered:** 2015-01-01 to 2015-06-30

## Approach

1. **Data overview**: shape, data types and statistical summary.
2. **Data cleaning**
   - Converted `pickup_dt` to datetime.
   - Extracted year, month, day, hour and weekday, then dropped the original column.
   - `borough` had 3,043 missing values, which were labelled `Unknown`.
   - `temp` had 359 missing values, all from Brooklyn in the first 15 days of January. They were imputed with Brooklyn's mean temperature.
3. **Univariate analysis**: histograms and boxplots for every numeric variable, and count plots for `borough` and `hday`.
4. **Bivariate analysis**: correlation heatmap, pair plots, and line charts of pickups by month, day of month and hour of day.

## Key Findings

- **Pickups are heavily right-skewed**, with a few hours reaching about 8,000 pickups.
- **Demand grows steadily through the period.** June pickups are about 2.8x January's.
- **Hourly demand peaks in the evening**, around the 19th and 20th hour of the day.
- **Weather shows no strong linear relationship with pickups.** Temperature and dew point are strongly correlated, and visibility is negatively correlated with precipitation, as expected.
- **Manhattan accounts for most pickups by volume.** Every borough has the same number of rows, but Manhattan has far more pickups than the rest.
- **Holidays have fewer pickups** than non-holidays, though only about 4% of observations are holidays.

## Tech Stack

- Python
- pandas, NumPy
- Matplotlib, Seaborn
- Jupyter / Google Colab

## Repository Structure

```
.
├── Data_Analytics_Engineering_EDA.ipynb   # Full analysis notebook
├── Uber_Data.csv                          # Dataset
└── README.md
```

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```
2. Install dependencies:
   ```bash
   pip install numpy==2.0.2 pandas==2.2.2 matplotlib==3.10.0 seaborn==0.13.2 jupyter
   ```
3. In the notebook, replace the Google Drive loading cells with a local path:
   ```python
   data = pd.read_csv('Uber_Data.csv')
   ```
4. Launch Jupyter and run all cells:
   ```bash
   jupyter notebook
   ```

## Author

**Muthulakshmi Viswanathan**
Data Analyst, Toronto, Canada
[LinkedIn](https://www.linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username)
