# 📊 Clean Dataset — SEA Globalisation & Inequality Research

This folder contains the fully cleaned, verified, and merged datasets used in the research project:
**"Globalisation and Income Inequality in Southeast Asia (2000–2023)"**

---

## 📁 Files in This Folder

| File | Description |
|------|-------------|
| `SEA_Master_Data_FINAL.xlsx` | Master dataset — KOFGI + Gini (144 rows, 5 columns) |
| `SEA_Master_Data_FINAL_v2.xlsx` | Upgraded master dataset — KOFGI + Gini + GDP Growth (144 rows, 6 columns) |
| `SEA_GDP_Growth_Raw.xlsx` | Raw GDP Growth data extracted from World Bank before merging |

---

## 🌍 Countries Covered

| Country | Code | Development Level |
|---------|------|-------------------|
| Indonesia | IDN | Lower-middle income |
| Malaysia | MYS | Upper-middle income |
| Philippines | PHL | Lower-middle income |
| Singapore | SGP | High income |
| Thailand | THA | Upper-middle income |
| Vietnam | VNM | Lower-middle income |

**Time Period:** 2000 to 2023 (24 years)
**Total Observations:** 144 rows (6 countries × 24 years)
**Missing Values:** Zero — all variables complete

---

## 📋 Dataset Features (Columns)

### SEA_Master_Data_FINAL_v2.xlsx — Full Dataset

| Column | Description | Source | Scale |
|--------|-------------|--------|-------|
| `Code` | 3-letter ISO country code (e.g. SGP, IDN) | KOF | Text |
| `Country` | Full country name | KOF | Text |
| `Year` | Year of observation | All sources | 2000–2023 |
| `KOFGI` | KOF Overall Globalisation Index Score | KOF ETH Zurich | 0–100 |
| `Gini` | Gini Coefficient — income inequality | World Bank / SingStat / DOSM | 0–100 |
| `GDP_Growth` | Annual GDP Growth Rate | World Bank WDI | Percentage (%) |

**KOFGI:** Higher score = more globalised. Composite of economic, social, and political globalisation dimensions.

**Gini:** Higher score = more unequal. 0 = perfect equality, 100 = maximum inequality. Values above 40 indicate high inequality.

**GDP_Growth:** Annual percentage change in real GDP. Negative values indicate economic contraction.

---

## 🔗 Original Data Sources

| Variable | Source | Direct Link |
|----------|--------|-------------|
| Gini Index | World Bank — World Development Indicators | [data.worldbank.org/indicator/SI.POV.GINI](https://data.worldbank.org/indicator/SI.POV.GINI) |
| Singapore Gini | Singapore Department of Statistics (SingStat) | [tablebuilder.singstat.gov.sg/table/CT/17892](https://tablebuilder.singstat.gov.sg/table/CT/17892) |
| Malaysia Gini (supplementary) | Department of Statistics Malaysia (DOSM) | [data.gov.my/data-catalogue/hh_inequality](https://data.gov.my/data-catalogue/hh_inequality) |
| KOFGI Score | KOF Swiss Economic Institute — ETH Zurich | [kof.ethz.ch/...kof-globalisation-index.html](https://kof.ethz.ch/en/forecasts-and-indicators/indicators/kof-globalisation-index.html) |
| GDP Growth | World Bank — World Development Indicators | [data.worldbank.org/indicator/NY.GDP.MKTP.KD.ZG](https://data.worldbank.org/indicator/NY.GDP.MKTP.KD.ZG) |

---

## 🛠️ Data Preparation Notes

### Missing Gini Data — How It Was Handled
Several countries do not conduct annual household income surveys. Missing years were filled using **linear interpolation** between known survey data points.

| Country | Survey Frequency | Real Data Points | Interpolated Points |
|---------|-----------------|-----------------|---------------------|
| Indonesia | Annual | 24/24 (100%) | 0 |
| Malaysia | Every 2–3 years | 15/24 (63%) | 9 |
| Philippines | Every 3 years | 9/24 (38%) | 15 |
| Singapore | Annual (SingStat) | 24/24 (100%) | 0 |
| Thailand | Mostly annual | 21/24 (88%) | 3 |
| Vietnam | Every 2 years | 12/24 (50%) | 12 |

**Interpolation formula:**
Value(Y) = Value(A) + [(Y − A) / (B − A)] × (Value(B) − Value(A))

### Singapore Special Case
The World Bank does not publish Singapore's Gini coefficient. Data was sourced directly from SingStat using the **"Household Employment Income Per Household Member (Including Employer CPF Contributions) — Before Government Transfers and Taxes"** series, converted from 0–1 scale to 0–100 scale for comparability with World Bank data.

### Scale Harmonisation
SingStat reports Gini on a 0–1 scale. All other World Bank data uses a 0–100 scale. Singapore values were multiplied by 100 before merging.

### Verification
All anchor data points were cross-verified against:
- CEIC Data (Thailand, Vietnam)
- TheGlobalEconomy.com (Philippines)
- Direct SingStat website screenshots (Singapore 2022, 2023)

---

## ✅ Data Quality Checks

| Check | Expected | Result |
|-------|----------|--------|
| Total rows | 144 | 144 ✅ |
| Rows per country | 24 | 24 each ✅ |
| Year range | 2000–2023 | 2000–2023 ✅ |
| Missing KOFGI values | 0 | 0 ✅ |
| Missing Gini values | 0 | 0 ✅ |
| Missing GDP values | 0 | 0 ✅ |
| KOFGI range | 30–100 | 45.2 to 82.7 ✅ |
| Gini range | 25–55 | 29.3 to 48.2 ✅ |

---

## 📜 Citation

If you use this dataset, please cite:
Jaiswal, Ansuman. (2025). SEA Globalisation & Inequality Research Dataset (2000–2023).
GitHub: https://github.com/iam-ansuman/SEA-Globalisation-Inequality-Research
Data sources: World Bank WDI, KOF ETH Zurich, SingStat, DOSM.

*An independent research project combining data science and critical development theory — Ansuman Jaiswal, 2026*
