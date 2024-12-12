# Processing Restaurant and Weather Data

## Project Summary
The objective of this project was to integrate restaurant and weather datasets to generate a comprehensive dataset enriched with weather information based on geographical locations. The processed data was stored in Parquet format and partitioned by country to facilitate efficient access and analysis.

---

## Workflow and Key Steps

### Step 1: Restaurant Data Integration
- Consolidated multiple CSV files containing restaurant data into a unified DataFrame.
- Verified the accuracy of `latitude` and `longitude` fields, confirming the absence of missing or invalid values.
- Introduced a new column, `custom_geohash`, generated with `precision=4` based on the geographical coordinates of each restaurant.

- <img width="967" alt="image" src="https://github.com/user-attachments/assets/9e8a9575-3518-4313-8086-8f3c9205377d" />


---

### Step 2: GeoHash Generation
- Computed GeoHash values for both datasets (restaurants and weather) using `latitude` and `longitude` as inputs.
- Ensured data quality by excluding weather data rows lacking geographical coordinates during GeoHash creation.

- <img width="907" alt="image" src="https://github.com/user-attachments/assets/d3a0c26c-93c5-416b-8a91-5e6506e5c995" />


---

### Step 3: Data Integration via GeoHash
- Combined the restaurant and weather datasets using a `left-join` operation on the GeoHash column.
- Identified unmatched rows in the resulting dataset, where weather data was absent. These gaps arose due to:
  - Limited regional coverage within the weather dataset.
  - Granularity differences between restaurant and weather data sources.
- **Note:** The task did not impose stringent validation requirements for the GeoHash-based merging process.

- <img width="418" alt="image" src="https://github.com/user-attachments/assets/c0bba245-e16e-49d7-b993-67725f2999ea" />


---

### Step 4: Storing the Enriched Dataset
- Saved the resulting enriched dataset in Parquet format for optimal storage and processing efficiency.
- Partitioned the data by the `country` column to enable streamlined access and analysis for different regions.

- <img width="665" alt="image" src="https://github.com/user-attachments/assets/6dce94df-5246-4866-90ff-831eb7996798" />
