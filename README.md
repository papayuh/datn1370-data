# datn1370-data

Public datasets for DATN 1370, Introduction to Data Visualization & Analytics
(Lone Star College–University Park). Read any file straight into pandas with its
raw GitHub URL:

```python
import pandas as pd
url = "https://raw.githubusercontent.com/papayuh/datn1370-data/main/weeks/wk07-trends/data/houston_power_monthly.csv"
df = pd.read_csv(url)
```

## Files

### `weeks/wk07-trends/data/houston_power_monthly.csv`

Houston-area monthly electricity use and temperature, January 2018 to September
2026 (105 rows, no blanks). Derived from `houston_power_clean.csv`: each value is
the mean of that month's available days. Used by the Module 4 assignment.

| Column | Meaning |
|---|---|
| `month` | text, `YYYY-MM` |
| `avg_high_f` | average daily high at Houston Intercontinental Airport (GHCN station USW00012960), °F, one decimal |
| `avg_load_mw` | average ERCOT Coast weather zone native load, megawatts, whole number |

### `weeks/wk07-trends/data/houston_power_raw.csv`

Houston-area daily electricity use and Houston temperature, 2018-01-01 to
2026-09-30. **Deliberately left messy for a cleaning exercise**: date as text,
temperature in NOAA's tenths of a degree Celsius, a few repeated rows, a few
blanks, a few `-9999` "no reading" codes, and a few missing days. Do not use it
as a reference dataset.

| Column | Meaning |
|---|---|
| `Date` | day, text, `MM/DD/YYYY` |
| `Coast Load (MW)` | ERCOT Coast weather zone native load, average of that day's hourly values, megawatts |
| `TMAX`, `TMIN` | daily high and low at Houston Intercontinental Airport (GHCN station USW00012960), tenths of °C |

### `weeks/wk07-trends/data/houston_power_clean.csv`

The same data after the course's cleaning steps: repeated rows removed, `-9999`
treated as missing, rows without a load or a temperature dropped, plus
`temp_f` = average of high and low, in °F. Columns `date`, `load_mw`, `tmax`,
`tmin`, `temp_f`.

### `weeks/wk07-trends/data/houston_gas_weekly.csv`

Houston weekly retail gasoline price with inflation adjustment, June 2000 to
October 2026, used in the Week 7 lecture. `price` is dollars per gallon,
`price_today` and `crude_today` are restated at the latest CPI in the file,
`us` is the U.S. average price, `crude` is the crude oil price per barrel.

## Sources and licenses

| Data | Source | License / terms |
|---|---|---|
| Hourly native load by weather zone, 2018–2026 (`Native_Load_YYYY.zip`) | ERCOT, Hourly Load Data Archives: https://www.ercot.com/gridinfo/load/load_hist | ERCOT Terms of Use §5 (https://www.ercot.com/help/terms): raw data on public portions of the site may be used, reproduced, and redistributed in compilations, charts, and analyses. ERCOT does not guarantee the accuracy of such compilations. This file is a compilation (hourly to daily averages) with deliberate cleaning-exercise errors added; it is not ERCOT's data as published. |
| Daily TMAX/TMIN, Houston Intercontinental Airport | NOAA NCEI, Global Historical Climatology Network – Daily: https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily · station file https://www.ncei.noaa.gov/data/global-historical-climatology-network-daily/access/USW00012960.csv | U.S. government work, public domain. Cite: Menne, M.J., et al. (2012), Global Historical Climatology Network – Daily (GHCN-Daily), Version 3, NOAA National Climatic Data Center, doi:10.7289/V5D21VHZ. |
| Weekly retail gasoline prices (Houston and U.S.) and crude oil prices | U.S. Energy Information Administration: https://www.eia.gov/petroleum/gasdiesel/ | U.S. government work, public domain (EIA copyright and reuse policy: https://www.eia.gov/about/copyrights_reuse.php). |
| Consumer Price Index for All Urban Consumers (CPI-U) | U.S. Bureau of Labor Statistics: https://www.bls.gov/cpi/ | U.S. government work, public domain. |

Data retrieved 2026-10-16 (power and temperature).
