# Processing Restaurant and Weather Data

## Project Summary
The objective of this project was to integrate restaurant and weather datasets to generate a comprehensive dataset enriched with weather information based on geographical locations. The processed data was stored in Parquet format and partitioned by country to facilitate efficient access and analysis.

---

## Workflow and Key Steps

### Step 1: Restaurant Data Integration
- Consolidated multiple CSV files containing restaurant data into a unified DataFrame.
- Verified the accuracy of `latitude` and `longitude` fields, confirming the absence of missing or invalid values.
- Introduced a new column, `custom_geohash`, generated with `precision=4` based on the geographical coordinates of each restaurant.

---

### Step 2: GeoHash Generation
- Computed GeoHash values for both datasets (restaurants and weather) using `latitude` and `longitude` as inputs.
- Ensured data quality by excluding weather data rows lacking geographical coordinates during GeoHash creation.

---

### Step 3: Data Integration via GeoHash
- Combined the restaurant and weather datasets using a `left-join` operation on the GeoHash column.
- Identified unmatched rows in the resulting dataset, where weather data was absent. These gaps arose due to:
  - Limited regional coverage within the weather dataset.
  - Granularity differences between restaurant and weather data sources.
- **Note:** The task did not impose stringent validation requirements for the GeoHash-based merging process.

---

### Step 4: Storing the Enriched Dataset
- Saved the resulting enriched dataset in Parquet format for optimal storage and processing efficiency.
- Partitioned the data by the `country` column to enable streamlined access and analysis for different regions.