# Honest vs. Misleading Visualizations

**Objective:** Quantify how chart design choices distort economic data, and build tools to detect and correct that distortion.

## Methodology
- Recreated Anscombe's Quartet to show that four datasets with identical means, variances, and correlation (r = 0.816) have completely different shapes
- Computed Tufte's Lie Factor for a truncated-axis revenue chart and redesigned it with an honest baseline
- Deflated FRED average hourly earnings (AHETPI) to 2020 dollars using CPI-U and plotted the same series four ways: full range, truncated y-axis, cherry-picked window, and log scale
- Ran a four-step EDA checklist (structure, distributions, relationships, anomalies) on World Bank GDP data covering 262 economies over 64 years (1960–2023)
- Built an interactive ipywidgets chart that toggles nominal vs. real wages, the y-axis floor, the time window, and linear vs. log scale, with a live Lie Factor readout

## Key Findings
- Summary statistics alone can hide nonlinearity, outliers, and single-point leverage, so data should be plotted before it is modeled
- A truncated y-axis turned a 4.1% revenue increase into what looks like a 200% jump, a Lie Factor of 49
- Real hourly earnings rose only about 20% in 60 years, with a long decline from the early 1970s to the mid-1990s. A 2015-onward window hides that decline entirely, and the 2020 spike reflects a composition effect (low-wage job losses), not wage gains
- Raw GDP is extremely right-skewed; a log10 transform makes the distribution readable
- The World Bank file stores missing data as absent rows rather than NaNs, so gaps only appear after pivoting to a country × year panel (74 of 1,280 country-years in the sampled heatmap). The gaps cluster at the start and end of the period, which rules out MCAR
- The dataset mixes regional aggregates with countries, so cross-country averages must filter them out to avoid double-counting
