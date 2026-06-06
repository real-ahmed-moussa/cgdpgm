# Dataset — China's GDP (1960–2014)

| Property | Value |
|---|---|
| Source | [World Bank World Development Indicators](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD) |
| Indicator | NY.GDP.MKTP.CD (GDP, current USD) |
| Instances | 55 annual observations |
| Features | Year (1960–2014), GDP (USD) |
| Missing Data | None |
| Size | < 1 KB |

## Files

- **`gdpChina.csv`** — raw GDP values in current USD (two columns: `Year`, `gdp`)
- **`gdpChina2.csv`** — analysis-ready version with three columns: `Year`, `gdp_orig` (raw USD), `gdp` (scaled to 10¹⁰ USD for numerical stability in spline fitting)

The analysis uses `gdpChina2.csv` with the `gdp` column (units: ×10¹⁰ USD). GDP ranges from 4.67 (1962) to 1,035.48 (2014) in these units.
