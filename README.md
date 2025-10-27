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

##Merged Data & Analysis

- Data Merged: The two primary files (relevant_strawberries_wide.csv and quarterly_vols_strawberries.csv) have been successfully merged.
- Aggregation Step: To make the merge possible, the quarterly shipment data (quarterly_vols_strawberries.csv) was aggregated into annual totals (total_tonnage) grouped by Year and Origin (state).
- Unit Conversion: Production data (production_cwt) was converted from CWT to TONS (production_tons) to match the shipment data's units.
- Final Combined Data: The resulting dataset (combined_data) contains one row per state per year, with columns for production_tons, total_tonnage, acres_harvested, and price_per_cwt, allowing for direct comparison.
