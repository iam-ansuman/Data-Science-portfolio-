# 📂 Unclean Dataset — Raw Original Data

This folder contains the **original raw datasets** downloaded directly from their official sources — before any cleaning, filtering, merging, or interpolation was applied.

These files are preserved here for full transparency and reproducibility. Anyone can download these exact files and follow the cleaning process documented in `/docs/` to reproduce the final master dataset from scratch.

---

## 📁 Files in This Folder

| File | Original Source | What It Contains |
|------|----------------|-----------------|
| `API_SI.POV.GINI_DS2_en_excel_v2_285016.xls` | World Bank WDI | Gini Index for all countries, 1960–2024, wide format |
| `API_NY.GDP.MKTP.KD.ZG_DS2_en_excel_v2_279307.xls` | World Bank WDI | GDP Growth (annual %) for all countries, wide format |
| `KOFGI_2025_public.xlsx` | KOF ETH Zurich | KOF Globalisation Index for all countries, 1970–2023 |

---

## ⚠️ Why These Files Are "Unclean"

These raw files have not been processed in any way. They contain:

- **All countries in the world** — not just the 6 SEA countries used in this study
- **All years** — from as far back as 1960, not just 2000–2023
- **Wide format** — years spread across columns instead of rows
- **Missing values** — structural gaps where countries did not report data
- **Extra columns** — Indicator Name, Indicator Code, metadata columns not needed for analysis
- **Mixed scales** — World Bank uses 0–100 for Gini; SingStat uses 0–1

---

## 🔗 Official Download Links

| Dataset | Direct Download Link |
|---------|---------------------|
| World Bank Gini Index | [data.worldbank.org/indicator/SI.POV.GINI](https://data.worldbank.org/indicator/SI.POV.GINI) |
| World Bank GDP Growth | [data.worldbank.org/indicator/NY.GDP.MKTP.KD.ZG](https://data.worldbank.org/indicator/NY.GDP.MKTP.KD.ZG) |
| KOF Globalisation Index | [kof.ethz.ch/en/forecasts-and-indicators/indicators/kof-globalisation-index.html](https://kof.ethz.ch/en/forecasts-and-indicators/indicators/kof-globalisation-index.html) |

---

## 🛠️ How These Were Cleaned

The full step-by-step cleaning process is documented in:
`/docs/SEA_Project_Process_Documentation_v4_Final.docx`

**Summary of cleaning steps applied:**
- Filtered to 6 countries: Indonesia, Malaysia, Philippines, Singapore, Thailand, Vietnam
- Filtered to years 2000–2023
- Converted from wide format to long format using Excel Power Query
- Filled missing Gini values using linear interpolation
- Added Singapore Gini from SingStat (not available in World Bank)
- Supplemented Malaysia Gini with DOSM data
- Harmonised scales (SingStat 0–1 → 0–100)
- Merged all three datasets on country code + year key using Python

**The clean, ready-to-use version is in:**
`/Data/Clean-DataSet/SEA_Master_Data_FINAL_v2.xlsx`

---
Jaiswal, Asuman. (2025). Globalisation and Income Inequality in Southeast Asia (2000–2023): 
A Mixed-Methods Analysis. Independent Research Project. 
GitHub: https://github.com/iam-ansuman/SEA-Globalisation-Inequality-Research

*An independent research project by Anshuman Jaiswal | 2026*
