# Global Energy & CO2 Emissions Analysis
### Analyzing the Relationship Between Energy Consumption, CO2 Emissions and Temperature Change (1980-2019)

---

## 📌 Project Overview
This project investigates whether rising global energy consumption 
and CO2 emissions are linked to increasing temperatures across 
about 200 countries over 40 years (1980-2019).

The analysis focuses specifically on the United States and Canada 
as two of the world's largest energy consumers and CO2 emitters, 
while providing a global overview for context.

---

## 🛠️ Tools Used
| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data cleaning and merging |
| Jupyter Notebook | Analysis environment |
| Tableau Public | Interactive dashboards |
| GitHub | Version control and sharing |

---

## 📂 Project Structure
```
Energy/
│
├── ENERGY.IPYNB                 # 1. Energy data cleaning
├── TEMPERATURE.IPYNB            # 2. Temperature data cleaning
├── MERGED_DATASET.ipynb         # 3. Merge, checks and summary figures
│
├── energy.csv                   # Raw energy dataset
├── combined_temperature.csv     # Raw temperature dataset
├── energy_cleaned.csv           # Output of ENERGY.IPYNB
├── cleaned_temperature.csv      # Output of TEMPERATURE.IPYNB
├── energy_breakdown_final.csv   # Output of MERGED_DATASET.ipynb (all energy types)
└── merged_final.csv             # Output of MERGED_DATASET.ipynb (energy + temperature)
```

---

## 📊 Datasets
**1. Global Energy Dataset**
- Source: U.S. Energy Information Administration (EIA), via Kaggle
- Rows: 55,440 (raw) → 41,920 (cleaned)
- Countries: 230 (raw, plus a World aggregate) → 202 in the final merged dataset
- Years: 1980 - 2019
- Features: Energy consumption, production, GDP, 
  Population, CO2 emissions, Energy intensity

**2. Global Temperature Dataset**
- Source: World Bank, via Kaggle
- Rows: 20,740
- Countries: 170
- Years: 1901 - 2022
- Features: Annual mean temperature, 5-year smoothed average

**Final merged dataset (`merged_final.csv`)**
- 8,080 rows: 202 countries × 40 years (all energy types combined)
- 163 of the 202 countries have temperature data

---

## 🧹 Data Cleaning Steps

### Energy Dataset
- Removed redundant index column (`Unnamed: 0`)
- Removed World aggregate rows to avoid double counting
- Replaced negative values with NaN (physically impossible)
- Removed countries with no GDP data in any year
- Forward/backward filled GDP and Population within 
  each country using neighboring years (a global median 
  is used only as a last resort, for 5 rows)
- Recomputed Energy Intensity columns from cleaned 
  source data
- Dropped rows where consumption/production could 
  not be filled
- Standardized column names

### Temperature Dataset
- Standardized column names
- Verified no missing values across all columns

### Merging
- Resolved 15+ country name mismatches between datasets
- Removed a duplicate copy of Gambia in the temperature data
- Removed historical countries (Former U.S.S.R., Former Yugoslavia, 
  etc.) and non-country territories that Tableau can't map
- Used left join to preserve all energy countries
- Overlapping period: 1980-2019 (40 years)

---

## 🔍 Key Findings
- CO2 data is only near-complete from 1993 onward (in 1980 only 
  the United States reports CO2, and the Former U.S.S.R. is removed 
  for mapping), so trends are measured over 1993-2019
- Global CO2 emissions rose from about 21,500 to about 35,500 
  million tonnes between 1993 and 2019 (roughly +65%), growing 
  fastest in the 2000s
- Over 1980-2019 as a whole, the United States emitted the most 
  CO2 in the dataset, with China close behind; China has been 
  the largest emitter every year since 2006
- Average temperature across the 163 countries with temperature 
  data rose by about 0.27°C per decade, and global CO2 and average 
  temperature are strongly correlated over 1993-2019 (r ≈ 0.8)
- High emission countries tend to be large 
  industrialized nations in temperate climates

---

## ⚠️ Limitations
- China, India and about 35 other countries and territories 
  (e.g. Ireland, Morocco, Czech Republic) have no temperature 
  data in the source dataset, so they are excluded from the 
  temperature analysis
- Before 1993, CO2 coverage is incomplete, so global CO2 totals 
  for the 1980s understate real emissions
- Temperature dataset ends in 2022, energy dataset 
  ends in 2019
- Correlation shown between CO2 and temperature but 
  causation requires deeper statistical analysis
- Historical countries (Former USSR, Yugoslavia etc.) 
  excluded from modern map visualizations

---

## 🚀 How to Run

**1. Clone the repository**
```bash
git clone https://github.com/Gerno05/Energy.git
cd Energy
```

**2. Install required libraries**
```bash
pip install pandas numpy jupyter
```

**3. Run the notebooks in order**
```bash
jupyter notebook
```
Open and run:
1. `ENERGY.IPYNB`
2. `TEMPERATURE.IPYNB`
3. `MERGED_DATASET.ipynb`

Each notebook only writes its own output files, so they can be 
re-run any number of times and give the same result.

## 📋 Requirements
python >= 3.8
pandas >= 1.3.0
numpy >= 1.21.0
jupyter >= 1.0.0

---

## 👤 Author
George Alaneme
- GitHub: github.com/Gerno05
- Tableau: public.tableau.com/George Alaneme
- LinkedIn: linkedin.com/in/George Alaneme

---

## 📄 Data Sources
- Countries CO2 Emission and more...
  https://www.kaggle.com/datasets/lobosi/c02-emission-by-countrys-grouth-and-population
- Mean temperature for countries by year 1901-2022
 https://www.kaggle.com/datasets/palinatx/mean-temperature-for-countries-by-year-2014-2022

---

*This project was completed as part of a data analysis 
portfolio to demonstrate skills in Python, data cleaning 
and Tableau visualization.*
