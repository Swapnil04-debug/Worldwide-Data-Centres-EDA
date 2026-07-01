# Worldwide Data Centers – Exploratory Data Analysis (EDA)

## Project Overview
This project performs an end-to-end Exploratory Data Analysis (EDA) on a global data center dataset to understand operational characteristics, resource consumption patterns, and sustainability metrics across facilities worldwide. The rapid growth of cloud computing, AI, and digital services has driven massive expansion in data center infrastructure — and with it, significant electricity and water consumption. This analysis explores those trends to surface actionable insights for more sustainable and efficient operations.

- **Project Type:** EDA
- **Contribution:** Individual

## Problem Statement
Data centers are essential to modern digital services but consume significant electricity and water, making operational efficiency and sustainability critical concerns. This project cleans and analyzes a global data center dataset to identify patterns in energy consumption, water usage, cooling efficiency, and facility performance, enabling data-driven insights for more sustainable and efficient data center operations.

## Business Objective
Analyze the operational efficiency and sustainability of global data centers by examining energy consumption, water usage, cooling technologies, and infrastructure characteristics. Specific objectives include:
- Analyzing electricity and water consumption patterns across data centers.
- Comparing operational performance across countries and owner companies.
- Evaluating the efficiency of various cooling system technologies.
- Identifying trends over time (2019–2025) in capacity, efficiency, and resource usage.

## Dataset
- **File:** `data_center_hybrid.csv`
- **Size (raw):** ~122,514 records across 13–14 columns
- **Time range:** 2019–2025

**Key columns:**
| Column | Description |
|---|---|
| Year | Year of recorded operational data |
| Facility_ID | Unique facility identifier |
| Facility_Name | Name of the data center |
| Owner_Company | Company that owns/operates the facility |
| City / Country | Facility location |
| Facility_Type | Classification (Enterprise, Colocation, Hyperscale, etc.) |
| Estimated_Capacity_MW | Estimated power capacity |
| Daily_Electricity_Usage_MWh | Daily electricity consumption |
| Daily_Water_Usage_Gallons | Daily water consumption |
| PUE | Power Usage Effectiveness |
| WUE_L_per_kWh | Water Usage Effectiveness |
| Cooling_System_Type | Type of cooling system used |
| Surrounding_Water_Stress_Tier | Regional water stress classification |

## Tools & Libraries
- Python 3
- pandas, numpy — data manipulation
- matplotlib, seaborn — visualization
- pycountry — country name validation/standardization
- Google Colab (with Google Drive mount) as the development environment

## Project Workflow
1. **Know Your Data** – Loaded the dataset, inspected shape, dtypes, duplicates, and missing values (with a missing-values heatmap).
2. **Understanding Variables** – Reviewed column definitions, summary statistics, and unique value counts.
3. **Data Wrangling** –
   - Replaced `"Unknown"` placeholders with `NaN` for City/Country.
   - Resolved rows with missing City/Country combinations (dropped fully-missing pairs).
   - Cleaned invalid city names (numeric-only, single-character, symbol-laden, or email-like values).
   - Standardized country names (aliases, translated names, regex-based corrections) and validated them against `pycountry`'s official country list.
   - Removed duplicate records after cleaning.
   - Detected outliers via boxplots on key numeric metrics.
   - Engineered categorical bins: **Capacity_Category** (Small/Medium/Large/Hyperscale), **PUE_Category** (Excellent/Good/Average/Poor), and quantile-based **WUE**/**Electricity_Usage** categories.
   - Standardized duplicate/aliased owner company names (e.g., Amazon/Amazon AWS, Facebook/Meta, Microsoft/Microsoft Azure).
4. **Data Visualization & Storytelling** – 15 charts exploring:
   - Distribution of data centers by capacity category, facility type, and geography.
   - Electricity and water consumption by country and city.
   - Top cities/countries by capacity and hyperscale concentration.
   - Yearly trends in electricity usage, water usage, and PUE (efficiency).
   - Most energy-efficient countries by average PUE.
   - Correlation heatmap and pair plot across numeric metrics.
   Each chart includes rationale for the chart type chosen, key insights, and business impact discussion.
5. **Solution to Business Objective** – Actionable recommendations derived from the analysis (see below).

## Key Insights
- Data centers are concentrated in a handful of hub cities (e.g., Ashburn, Sterling, Manassas) and countries, with the **United States** dominating electricity consumption.
- **Electricity usage, water usage, and installed capacity** are all strongly and positively correlated — larger facilities consume proportionally more of both resources.
- **PUE has steadily improved (declined) from 2019 to 2025**, indicating industry-wide gains in energy efficiency even as total consumption has grown.
- **Hyperscale** and **Medium** capacity facilities make up the bulk of the market, while **Large** facilities are the least represented category.
- A few companies (Amazon AWS, Equinix, Digital Realty) operate a disproportionately large share of global data center facilities.

## Recommendations
- Prioritize infrastructure investment in high-demand hubs while exploring emerging locations to reduce concentration risk.
- Adopt advanced cooling technologies and monitor PUE/WUE to improve energy and water efficiency.
- Increase renewable energy adoption to offset rising electricity demand and carbon impact.
- Use predictive analytics for capacity planning based on historical growth trends.

## How to Run
1. Open the notebook `Swapnil_Dixit_s_Data_Centre_EDA_Submission_project.ipynb` in Google Colab (or Jupyter).
2. Mount Google Drive (if using Colab) and update the dataset path if needed:
   ```python
   df = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/DATA SET/data_center_hybrid.csv')
   ```
3. Install any missing dependency:
   ```bash
   pip install pycountry
   ```
4. Run all cells sequentially from top to bottom.

## Project Structure
```
├── Swapnil_Dixit_s_Data_Centre_EDA_Submission_project.ipynb   # Main analysis notebook
├── data_center_hybrid.csv                                     # Raw dataset (not included; add locally)
└── README.md                                                  # Project documentation
```

## Author
**Swapnil Dixit**
- GitHub: [Swapnil04-debug](https://github.com/Swapnil04-debug)
- Project repo: [Worldwide-Data-Centres-EDA](https://github.com/Swapnil04-debug/Worldwide-Data-Centres-EDA)

## Conclusion
This EDA capstone project offers a comprehensive view of the global data center landscape — covering infrastructure capacity, resource consumption, geographic distribution, and operational efficiency. The findings highlight both the sustainability challenges and efficiency gains within the industry, providing a foundation for data-driven decisions around capacity planning, energy management, and sustainable growth.
