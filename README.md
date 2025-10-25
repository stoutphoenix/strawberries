# Strawberry Production and Transportation Data

## Overview
This project combines USDA strawberry production data with transportation shipment data to analyze farm-to-market patterns.

## Key Files

### Data Files (CSV)

**Primary Analysis Files:**
- **`relevant_strawberries_wide.csv`** - *START HERE*
  - Cleaned USDA NASS production data in wide format
  - Contains: year, state, price per CWT, acres harvested, production in CWT
  - One row per state per year
  - Ready for analysis and merging

- **`quarterly_vols_strawberries.csv`** - *START HERE*
  - Filtered transportation data for strawberries only
  - Contains: year, quarter, origin state, commodity, tonnage shipped
  - Source: USDA AMS refrigerated truck shipment data

**Intermediate/Raw Files:**
- `quarterly_vols_all.csv` - Original unfiltered transportation data (all commodities)
- `relevant_strawberries.csv` - Raw USDA production data in long format (before cleaning)

### Code Files
- **`clean_data.Rmd`** - R Markdown script containing all data cleaning and transformation steps

## Data Sources

**Production Data:** USDA NASS QuickStats (Survey program)
- Categories: Production, Acres Harvested, Yield, Price Received
- Geographic Level: State
- Period: Annual (2000-2024)

**Transportation Data:** USDA AMS Agricultural Refrigerated Truck Quarterly
- Quarterly shipment volumes by origin and commodity
- Measured in tons
- Source: https://www.ams.usda.gov/services/transportation-analysis/agricultural-refrigerated-truck-quarterly-datasets

## Notes

- Production data is in **CWT** (hundredweight = 100 lbs)
- Shipment data is in **TONS** (1 ton = 20 CWT)
- Convert as needed: `tons = cwt / 20` or `cwt = tons * 20`
