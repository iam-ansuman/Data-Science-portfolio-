# Do Left-Handers Really Die Young?

**A Bayesian analysis of the famous "9-year gap" between left- and right-handers**

A MedTourEasy Traineeship project | Python, pandas, NumPy, Matplotlib | Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/iam-ansuman/Data-Science-portfolio-/blob/main/handedness-death-age-analysis/handedness_death_age_analysis.ipynb)

---

## The question

In 1991, Halpern and Coren reported that left-handed people died about **9 years younger** than right-handed people (66 vs 75). They surveyed families of people who died in 1989 in two southern California counties.

But left-handedness was once actively discouraged, so older generations rarely reported it. This project asks:

> **Can the changing rate of left-handedness alone reproduce the gap, with no real difference in lifespan?**

## Key results

| Measure | Result |
|---|---|
| Mean age at death, left-handers (study year 1990) | **67.25** |
| Mean age at death, right-handers (study year 1990) | **72.79** |
| Apparent gap | **5.5 years** |
| Share of the original 9-year gap reproduced | **about 60%** |
| Gap if the study were run in 2018 (what-if) | **2.3 years** |

**Conclusion:** with no lifespan difference built into the model at all, changes in how left-handedness was reported produce a 5.5-year gap. The gap shrinks as generations even out, which is the signature of a statistical artefact, not a biological effect.

## Data

| Dataset | Year | Coverage | Gives us |
|---|---|---|---|
| National Geographic survey (Gilbert & Wysocki, 1992) | 1986 | 1,177,507 Americans aged 10 to 86, so birth years 1900 to 1976 | P(LH \| A): left-handed rate by age and sex |
| CDC/NCHS US deaths by single year of age | 1999 | All US deaths that year (2,391,399), ages 0 to about 120 | P(A): probability of dying at each age |

These are **two separate snapshots**, not a continuous time series. The handedness questions were part of the National Geographic Smell Survey, run with the Monell Chemical Senses Center.

## Method

Bayes' theorem flips a known probability into the one we want:

```
P(A | LH) = P(LH | A) × P(A) / P(LH)
```

- **P(LH | A):** chance someone who died at age A was left-handed, looked up from the survey by their birth year (study year minus age). Ages outside the survey range use the mean of the 10 youngest or 10 oldest data points.
- **P(A):** chance of dying at age A, from the 1999 death counts.
- **P(LH):** overall share of left-handers among the dead, a death-weighted average.

Right-handers use the same formula with P(RH) = 1 − P(LH). Mean ages come from summing age × probability across ages 6 to 114.

## Findings from each chart

**1. Older people report far less left-handedness.** Men are more left-handed than women at every age (about 14 to 15.5% vs 11 to 12% under 40). Rates drop about 40% between ages 45 and 65, which in 1986 means people born roughly 1921 to 1941.

**2. It depends on birth year, not age.** Reported left-handedness more than doubles, from about 6% for people born before 1920 to a plateau near 13% for those born after about 1942. The rise is gradual over two decades, consistent with social pressure slowly easing. The plateau is close to the modern worldwide estimate of 10.6% (Papadatou-Pastou et al., 2020).

**3. Most deaths come from low left-handedness generations.** US deaths peak around age 84 (about 73,000 at a single year of age). In a 1990 study year, most deaths belong to people born around 1895 to 1925, when left-handedness was rarely reported. The peak reflects counts, not risk: many people still alive multiplied by a high yearly chance of dying.

**4. Left-handers skew younger among the dead.** The left-handed age-at-death curve sits above the right-handed one until about age 70, then falls below it. This happens even though the model assumes identical lifespans.

**5. The gap fades over time.** Moving the study to 2018 cuts the gap by 58%, from 5.5 to 2.3 years, because people dying in 2018 were born later, when reporting was more even across generations.

## How this compares with published research

A 2023 study by Microsoft's AI for Good Lab and Harvard (Ferres et al., *Archives of Public Health*) modelled all 2,019,512 US deaths from 1989 by birth year, gender and handedness. With no lifespan difference assumed, it reproduced a **9.3-year** gap. When the rate of left-handedness was held constant, the gap dropped to **0.02 years**.

This project's simplified model gets about 60% of the way there. The remaining difference is explained by the limitations below.

## Limitations

- **Year mismatch:** 1999 death data is used for a 1990 study year, a 9-year shift in assigned birth years.
- **Place mismatch:** the whole US, not the two California counties in the original study.
- **Sexes combined:** men are more left-handed and die younger on average, which the combined rate hides.
- **Extrapolated edges:** ages below 14 and above 90 use flat averages of the noisiest survey points. The step visible near age 90 in the probability chart comes from this switch, not from real deaths.
- **2018 is a what-if:** it reuses the 1999 death distribution, so 2.3 years is an estimate, not a measurement.

## Possible extensions

- Run the analysis separately for men and women.
- Sweep every study year from 1986 to 2040 to see when the gap disappears.
- Hold the left-handed rate constant to test whether the gap goes to zero.
- Use 1989 death data from CDC WONDER to match the original study year.

## Repository contents

| File | Description |
|---|---|
| `handedness_death_age_analysis.ipynb` | Completed notebook with all 10 tasks, charts and outputs |
| `handedness_project_report.pptx` | Project report presentation |
| `README.md` | This file |

## How to run

1. Click the **Open in Colab** badge above, or upload the notebook to [Google Colab](https://colab.research.google.com).
2. Choose **Runtime > Run all**. Both datasets load directly from public URLs, so no downloads are needed.

Requirements if running locally: `pandas`, `numpy`, `matplotlib`.

## References

- Halpern, D. F. & Coren, S. (1991). Handedness and life span. *New England Journal of Medicine*.
- Gilbert, A. N. & Wysocki, C. J. (1992). Hand preference and age in the United States. *Neuropsychologia*, 30(7), 601 to 608.
- CDC / NCHS (2001). Deaths: Final Data for 1999. *National Vital Statistics Reports*, 49(8).
- Ferres, J. L. et al. (2023). Modeling to explore and challenge inherent assumptions when cultural norms have changed: a case study on left-handedness and life expectancy. *Archives of Public Health*, 81:137.
- Papadatou-Pastou, M. et al. (2020). Human handedness: a meta-analysis. *Psychological Bulletin*, 146(6).

---

*Developed as part of the MedTourEasy Traineeship Program by [Ansuman](https://github.com/iam-ansuman).*
