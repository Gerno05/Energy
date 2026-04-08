# Global Energy & CO2 Emissions Analysis
### Analyzing the Relationship Between Energy Consumption, CO2 Emissions and Temperature Change (1980-2019)

---

## 📌 Project Overview
This project investigates whether rising global energy consumption 
and CO2 emissions are linked to increasing temperatures across 
170 countries over 40 years (1980-2019).

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
| SQLite | Data querying |
| GitHub | Version control and sharing |

---

## 📂 Project Structure
energy-analysis/
│
├── data/
│   ├── energy.csv                  # Raw energy dataset
│   ├── combined_temperature.csv    # Raw temperature dataset
│   ├── energy_cleaned.csv          # Cleaned energy data
│   ├── temperature_cleaned.csv     # Cleaned temperature data
│   └── merged_final.csv            # Merged dataset for analysis
│
├── notebooks/
│   ├── energy_cleaning.ipynb       # Energy data cleaning
│   ├── temperature_cleaning.ipynb  # Temperature data cleaning
│   └── analysis.ipynb              # Exploratory data analysis
│
├── dashboard/
│   └── screenshots/
│       ├── dashboard1.png          # Global Energy Overview
│       └── dashboard2.png          # CO2 vs Temperature
│
└── README.md

---

## 📊 Datasets
**1. Global Energy Dataset**
- Source: U.S. Energy Information Administration (EIA)
- Rows: 55,440 (raw) → 47,640 (cleaned)
- Countries: 170
- Years: 1980 - 2019
- Features: Energy consumption, production, GDP, 
  Population, CO2 emissions, Energy intensity

**2. Global Temperature Dataset**
- Source: World Bank
- Rows: 20,740
- Countries: 170
- Years: 1901 - 2022
- Features: Annual mean temperature, 5-year smoothed average

---

## 🧹 Data Cleaning Steps

### Energy Dataset
- Removed redundant index column (`Unnamed: 0`)
- Removed World aggregate rows to avoid double counting
- Replaced negative values with NaN (physically impossible)
- Forward/backward filled GDP and Population within 
  each country using neighboring years
- Recomputed Energy Intensity columns from cleaned 
  source data
- Dropped rows where consumption/production could 
  not be filled
- Standardized column names

### Temperature Dataset
- Renamed columns to remove spaces and special characters
- Converted Year to integer format
- Verified no missing values across all columns

### Merging
- Resolved 20+ country name mismatches between datasets
- Used left join to preserve all energy countries
- Overlapping period: 1980-2019 (40 years)

---

## 📈 Dashboards

### Dashboard 1 — Global Energy & Emissions Overview
- World map showing CO2 emissions by country
- Global CO2 trend line (1980-2019)
- Top 10 highest CO2 emitting countries
- Interactive year filter

### Dashboard 2 — CO2 vs Temperature Analysis
- Dual axis line chart: CO2 and temperature over time
- Scatter plot: CO2 emissions vs average temperature
- Temperature map by country (Blue = cold, Red = hot)
- Interactive year filter

🔗 **View Live Dashboard:** [Tableau Public Link]

---

## 🔍 Key Findings
- Global CO2 emissions rose from ~5,000 to ~35,000 
  million tonnes between 1980 and 2019
- The United States is the largest CO2 emitter 
  in the dataset
- Global average temperatures rose alongside 
  increasing CO2 emissions
- High emission countries tend to be large 
  industrialized nations in temperate climates
- CO2 emissions accelerated significantly after 1992

---

## ⚠️ Limitations
- China and India excluded from temperature analysis 
  due to missing temperature data in source dataset
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
git clone https://github.com/yourname/energy-analysis.git
cd energy-analysis
```

**2. Install required libraries**
```bash
pip install pandas numpy matplotlib jupyter
```

**3. Run the notebooks in order**
```bash
jupyter notebook
```
Open and run:
1. `notebooks/energy_cleaning.ipynb`
2. `notebooks/temperature_cleaning.ipynb`
3. `notebooks/analysis.ipynb`

**4. View dashboards**
Open Tableau Public link above or load 
`merged_final.csv` into Tableau directly

---

## 📋 Requirements
python >= 3.8
pandas >= 1.3.0
numpy >= 1.21.0
jupyter >= 1.0.0

---

## 👤 Author
**Your Name**
- GitHub: github.com/yourname
- Tableau: public.tableau.com/yourname
- LinkedIn: linkedin.com/in/yourname

---

## 📄 Data Sources
- Energy Data: U.S. Energy Information Administration
  https://www.eia.gov
- Temperature Data: World Bank Climate Portal
  https://climateknowledgeportal.worldbank.org

---

*This project was completed as part of a data analysis 
portfolio to demonstrate skills in Python, data cleaning, 
SQL and Tableau visualization.*
