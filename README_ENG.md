# FALL 2025 Doubled-Up Homelessness: Spatial Data Analysis and Visualization

This repository contains a comprehensive data cleaning and spatial integration pipeline to analyze doubled-up homelessness patterns across demographic groups and geographic regions in the United States. The project enables intersectional analysis of race, ethnicity, and economic status across geographic boundaries at both sub-state (PUMA) and state levels.

**Final Tableau visualization can be found here: https://public.tableau.com/app/profile/yijun.kim3606/viz/FA25Doubled-UpHomelessness/StateOverviewDashboard**

## Getting Started

The primary deliverable is the cleaned spatial datasets optimized for Tableau visualization. The `data/FA25_DataCleaning.ipynb` notebook contains the complete data processing pipeline. The cleaned datasets are located in the `data/clean data/FA25_Cleaned data/` folder:
- `puma_data_integrated_spatial_2023/` - PUMA-level spatial data (shapefile)
- `state_data_2023_cleaned_with_spatial.csv` - State-level data with WKT geometry

Dashboard previews are available in `visualizations/FA25_dashboard preview/`.

## Overview

Doubled-up homelessness refers to households where people are living with others due to economic hardship or loss of housing. Understanding patterns of doubled-up homelessness across different demographic groups and geographic regions is crucial for policymakers, researchers, and advocates working to address housing insecurity.

The challenge is that demographic and housing data from the American Community Survey (ACS) requires extensive cleaning, standardization, and spatial integration to enable meaningful geographic visualization and intersectional analysis. Raw data lacks proper geographic identifiers, contains inconsistent formatting, and requires merging with spatial boundaries to create visualization-ready datasets.

This project transforms raw ACS data into analysis-ready datasets that enable:
- Geographic mapping of doubled-up homelessness rates at PUMA and state levels
- Demographic breakdowns by race/ethnicity
- Economic status intersections (poverty analysis)
- Dynamic filtering and intersectional analysis in Tableau

## Project Description

The goal is to provide accessible, accurate data visualizations to better understand patterns of doubled-up homelessness across different demographic groups and geographic regions. To accomplish this goal, cleaned data was created for spatial visualization in Tableau, enabling intersectional analysis of race, ethnicity, and economic status across geographic boundaries at both sub-state (PUMA) and state levels.

The main challenge is to develop comprehensive **data cleaning and spatial integration pipelines to transform raw ACS data into visualization-ready datasets**. The secondary tasks involve **standardizing geographic identifiers, creating filtering flags, and optimizing data structure for Tableau performance**. The tertiary goals involve **integrating spatial geometries with demographic and economic indicators to enable geographic analysis**. The successful completion of these objectives will showcase the importance of data accessibility in promoting evidence-based policy decisions for housing insecurity.

## Project Checklist

1. ✅ Develop comprehensive data cleaning pipeline for PUMA and state-level datasets
2. ✅ Create standardized geographic identifiers and metadata
3. ✅ Build filtering flag system for demographic and economic characteristics
4. ✅ Integrate spatial geometries with cleaned tabular data
5. ✅ Optimize datasets for Tableau visualization performance
6. ✅ Generate visualization-ready outputs in multiple formats (shapefile, CSV with WKT)

## Proposed Solution

1. For the main challenge, a researcher would examine raw ACS data files with inconsistent formatting, missing geographic identifiers, and complex column structures. They would need to standardize GEOIDs, merge state mapping data, create filtering variables, and integrate spatial boundaries. This is a task that can be automated through Python data processing pipelines using pandas and geopandas.

2. The secondary task involves standardizing column names, creating binary flags for demographic categories, and optimizing data structure for visualization tools. This requires systematic data transformation rules and naming conventions that can be codified in a cleaning script.

3. The tertiary task would involve merging tabular data with spatial shapefiles, handling unmatched records, and converting geometries to appropriate formats for different visualization platforms. This is a common GIS data integration problem that can be solved through spatial joins and format conversion.

## Technology Stack

1. **Python** (Pandas, NumPy, GeoPandas)
2. **Jupyter Notebooks** for data cleaning and documentation
3. **Tableau** for spatial visualization and dashboard creation

## Project Structure

```
.
├── data/
│   ├── clean data/
│   │   └── FA25_Cleaned data/
│   │       ├── README.md
│   │       ├── puma_data_integrated_spatial_2023/ (shapefile directory)
│   │       └── state_data_2023_cleaned_with_spatial.csv
│   ├── raw data/
│   │   └── FA25_Raw Data/
│   │       ├── US_2023_5y_state_RACE_poor.csv
│   │       ├── ipums_puma_2020_ipums_puma_2020.shp.csv
│   │       ├── puma_data_2023.csv
│   │       ├── state_2023_5y_all_row E label fix.csv
│   │       └── us-state-ansi-fips.csv
│   ├── spatial file/
│   │   └── FA25_spatial file/
│   │       ├──  PUMA/
│   │       │   └── ipums_puma_2020.zip
│   │       ├──  State/
│   │       │   └── HexStatesPadded.zip
│   │       └── README.md   
│   └── FA25_DataCleaning.ipynb
├── dataset-documentation/
│   └── DATASETDOC-fa25.md
├── miscellaneous/
│   ├── FA25_Client Slides/
│   ├── FA25_DEMODay Poster.pdf
│   └── FA25_In-Class Presentation Doubled-up Homelessness.pdf
├── visualizations/
│   └── FA25_dashboard preview/
│       ├── PUMA Detail Dashboard.png
│       └── State Overview Dashboard.png
└── workbooks
    └── FA25_DS594 Tableau.twb
```

### Folder Descriptions

#### `./data/`
Main data directory containing all input and output datasets.

**`./data/clean data/FA25_Cleaned data/`**
- Contains the final cleaned and integrated datasets ready for visualization
- `puma_data_integrated_spatial_2023/` - Integrated PUMA spatial data (shapefile format, 2,461 records)
- `state_data_2023_cleaned_with_spatial.csv` - Integrated state data with WKT geometry (51 records)
- `README.md` - Documentation for cleaned data files

**`./data/raw data/FA25_Raw Data/`**
- Contains all original source files before processing
- `puma_data_2023.csv` - Original PUMA-level demographic and doubled-up homelessness data (2,462 records)
- `state_2023_5y_all_row E label fix.csv` - Original state-level data (51 records)
- `US_2023_5y_state_RACE_poor.csv` - State-level race and poverty intersection data
- `us-state-ansi-fips.csv` - State FIPS code mapping file (51 records)
- `ipums_puma_2020_ipums_puma_2020.shp.csv` - PUMA geographic metadata (2,486 records)
- `US_2022_5y_puma_2-25-25.csv` - Additional PUMA data from 2022

**`./data/FA25_DataCleaning.ipynb`**
- Main Jupyter notebook containing the complete data cleaning and spatial integration pipeline
- Processes both PUMA and state-level datasets
- Generates all cleaned output files

**`./dataset-documentation/DATASETDOC-fa25.md`**
- Complete dataset documentation including schema, field descriptions, and usage guidelines

#### `./miscellaneous/`
Contains project deliverables and presentation materials.

**`./miscellaneous/FA25_Client Slides/`**
- Client presentation slides

**`./miscellaneous/FA25_DEMODay Poster.pdf`**
- Demo day poster presentation

**`./miscellaneous/FA25_In-Class Presentation Doubled-up Homelessness/`**
- In-class presentation materials

#### `./visualizations/`
Contains visualization outputs and dashboard previews.

**`./visualizations/FA25_dashboard preview/`**
- `PUMA Detail Dashboard.png` - Preview of PUMA-level dashboard
- `State Overview Dashboard.png` - Preview of state-level dashboard

**`./workbooks/`**
Contains tableau workbook files for visualization

**`./workbooks/FA25_DS594 Tableau.twb/`** - the FA25 team's workbook file for tableau visualization.

## Data Sources

### Primary Data Sources

| Source | Type | Description | Link |
|---|---|------------------------------------------------------------------|---|
| American Community Survey (ACS) 2023 5-Year Estimates | CSV | Original source data files containing demographic and doubled-up homelessness metrics at both PUMA and state levels, provided by the client | https://drive.google.com/drive/folders/14gJlaHZU1O_ew-ffJjUAQFKGAGYEuOxW?dmr=1&ec=wgc-drive-hero-goto
| IPUMS USA | Shapefile | Geographic boundary shapefiles for Public Use Microdata Areas (PUMAs) from the 2020 census, used for spatial integration of PUMA-level data | https://usa.ipums.org/usa/volii/pumas20.shtml
| U.S. Census Bureau | CSV | State FIPS code mapping and geographic definitions | https://gist.github.com/dantonnoriega/bf1acd2290e15b91e6710b6fd3be0a53#file-us-state-ansi-fips-csv
| HexStatesPadded | Shapefile | Hexagon-based state map shapefile with padding for improved visualization, used for state-level spatial integration | https://stanke.co/hexstatespadded/

### Data Sets

* **Primary Dataset**: 2,461 PUMA records and 51 state records with demographic and economic metrics
* **Geographic Coverage**: All U.S. states and 2,461 Public Use Microdata Areas (PUMAs)
* **Data Period**: 2023 (5-year estimates representing 2019-2023)
* **Demographic Categories**: White, Black, AIAN, Asian, NHOPI, Hispanic, Other, Multi
* **Economic Metrics**: Doubled-up homelessness rates, poverty status, race × poverty intersections

## 📂 Data Processing & Cleaning

This project uses a comprehensive Jupyter notebook (`DataCleaning.ipynb`) to prepare ACS datasets for spatial visualization in Tableau.

---

### Step 1: PUMA Data Cleaning and Spatial Integration

The **PUMA cleaning process** transforms raw PUMA-level data into a visualization-ready spatial dataset.

**Purpose**

* Load and standardize PUMA demographic and economic data
* Merge geographic identifiers and metadata
* Create filtering flags for demographic and economic characteristics
* Integrate spatial geometries from shapefiles
* Optimize column names and structure for Tableau

**How it Works**

1. **Inputs**
   * `puma_data_2023.csv` - Main PUMA data (2,462 records)
   * `us-state-ansi-fips.csv` - State mapping file
   * `ipums_puma_2020_ipums_puma_2020.shp.csv` - PUMA geographic metadata
   * `ipums_puma_2020.shp` - PUMA spatial shapefile

2. **Process**
   * Standardize GEOIDs to 7-digit zero-padded strings
   * Extract state FIPS codes from GEOIDs
   * Merge state names and abbreviations
   * Merge PUMA names and codes
   * Create binary flags for demographic categories (White, Black, AIAN, Asian, NHOPI, Hispanic, Other, Multi)
   * Create economic flags (Poor_Flag) and intersection flags (Race_Poor_Flag)
   * Drop unnecessary columns (renter-related, standard errors)
   * Rename columns to abbreviated format for Tableau compatibility
   * Merge with spatial shapefile using GEOID matching

3. **Output**
   * `puma_data_2023_integrated_spatial/` - Shapefile directory with 2,461 matched records
   * 129 columns (122 data columns + 7 spatial metadata columns)

---

### Step 2: State Data Cleaning and Spatial Integration

The **state cleaning process** transforms raw state-level data into a visualization-ready dataset with WKT geometry.

**Purpose**

* Load and standardize state demographic and economic data
* Merge race × poverty intersection data
* Create filtering flags matching PUMA structure
* Integrate hexagon shapefile geometries
* Convert to WKT format for CSV export

**How it Works**

1. **Inputs**
   * `state_2023_5y_all_row E label fix.csv` - Main state data (51 records)
   * `us-state-ansi-fips.csv` - State mapping file
   * `US_2023_5y_state_RACE_poor.csv` - Race × poverty intersection data
   * `HexStatesPadded.shp` - State hexagon shapefile

2. **Process**
   * Standardize state FIPS codes to 2-digit zero-padded strings
   * Merge state names and abbreviations
   * Merge race × poverty intersection metrics
   * Create binary flags for demographic and economic characteristics
   * Drop standard error columns (keeping only MOE columns)
   * Round percentage columns to 2 decimal places
   * Merge with hexagon shapefile using state abbreviations
   * Convert geometry to WKT format for CSV compatibility

3. **Output**
   * `state_data_2023_cleaned_with_spatial.csv` - CSV file with WKT geometry (51 records)
   * 123 columns (122 data columns + 1 WKT geometry column)

---

**Final Outputs**

* PUMA Spatial Dataset: `data/clean data/FA25_Cleaned data/puma_data_integrated_spatial_2023/` (shapefile)
* State Spatial Dataset: `data/clean data/FA25_Cleaned data/state_data_2023_cleaned_with_spatial.csv` (CSV with WKT)

---

**Pipeline Summary:**

* `data/FA25_DataCleaning.ipynb` → Complete data cleaning and spatial integration pipeline
* PUMA Processing → 2,461 records with 129 columns in shapefile format
* State Processing → 51 records with 123 columns in CSV with WKT format
* Both datasets optimized for Tableau visualization with filtering flags
* Output location: `data/clean data/FA25_Cleaned data/`

---

## Team & Contact Information

| Name | Role | Email Address |
| ----------- | ----------- | ----------- |
| Yijun Kim | Project Member - Student | yijunkim@bu.edu |
| Deniz Ozcakir | Project Member - Student | dozcakir@bu.edu |
| Alex Noor | Project Member - Student | alexnoor@bu.edu |
| Amira Zuniga | Project Member - Student | azuniga@bu.edu |
| Hoayang Peng | Project Manager | hpeng824@bu.edu |
| Catalina Sanhueza Schuller | Technical Project Manager | csanhuez@bu.edu |

### Client Contacts
- Molly Richard - molly.richard@uri.edu

### Course Information
- **Class**: DS594 Data Visualization
- **Program**: Boston University Spark!
- **Semester**: Fall 2025
- **Client**: Molly Richard

## Key Research Findings

### Data Quality Improvements
- **Standardization**: All GEOIDs and FIPS codes consistently formatted as zero-padded strings
- **Column Optimization**: Reduced from 166 to 122 columns for PUMA data, 139 to 123 for state data
- **Naming Convention**: Abbreviated column names optimized for Tableau (10-character limit for shapefiles)
- **Flag System**: 17 binary flags created for flexible filtering (8 demographic + 1 economic + 8 intersection flags)

### Analysis Capabilities Enabled
- **Demographic Analysis**: Filter by race/ethnicity using flags or categories
- **Economic Analysis**: Filter by poverty status using Poor_Flag
- **Intersectional Analysis**: Combined demographic × economic flags (e.g., White_Poor_Flag)
- **Spatial Visualization**: Full geographic boundaries for mapping at PUMA and state levels
- **Statistical Analysis**: Includes frequencies, percentages, MOE, and CV for all metrics

## Future Research Directions

### Dashboard Enhancements
Future semesters could strengthen the dashboard by:
1. **Robust State Comparison Mode**: Fully implement comprehensive state-to-state comparison functionality with side-by-side analysis
2. **Enhanced Filtering Capabilities**: Add more flexible and granular filtering options for demographic and economic characteristics
3. **Lightweight PUMA-Level Comparisons**: Support efficient PUMA-to-PUMA comparisons without performance degradation
4. **Platform Migration**: Migrate the dashboard away from Tableau entirely, as Tableau-style apps are inherently slow. This migration would enable:
   - Improved performance and faster load times
   - Greater customization flexibility
   - Different interactive options that are easier to implement
   - More responsive user experience

### Immediate Extensions
1. **Additional Demographics**: Include age, gender, and household composition variables
2. **Service Provider Mapping**: Integrate housing service provider locations for resource mapping

## Resources

### Documentation

* **Dataset Documentation**: [./dataset-documentation/DATASETDOC-fa25.md](./dataset-documentation/DATASETDOC-fa25.md) - Comprehensive dataset documentation following BU Spark standards, including schema, field descriptions, and usage guidelines.
* **Cleaned Data README**: [./data/clean data/FA25_Cleaned data/README.md](./data/clean%20data/FA25_Cleaned%20data/README.md) - Documentation file in the cleaned data folder explaining how to use the processed datasets for visualization on Tableau.
* **Spatial file README**: [./data/spatial file/FA25_spatial file/README.md](./data/spatial%20file/FA25_spatial%20file/README.md) - Documentation file in the spatial file folder explaining how to use spatial files when cleaning the data with `FA25_DataCleaning.ipynb`.

### Technical Implementation Resources

1. **Jupyter Notebooks**: https://jupyter.org/ - Analysis environment documentation
2. **Python Data Science Stack**: Pandas, NumPy, GeoPandas libraries
3. **GeoPandas Documentation**: https://geopandas.org/ - Spatial data manipulation
4. **Tableau Documentation**: https://www.tableau.com/learn - Geographic visualization guides
5. **ESRI Shapefile Format**: Standard for spatial data storage and exchange
6. **WKT Format**: Well-Known Text for CSV-based spatial data

## License and Attribution

### Academic Citation
```
Doubled-Up Homelessness: Spatial Data Analysis and Visualization. (2025). 
BU Spark DS594 Team: Yijun Kim, Deniz Ozcakir, Alex Noor, Amira Zuniga. 
In collaboration with  Molly Richard. 
https://github.com/BU-Spark/data-viz-ciss-doubled-up
```

### Data Source Attribution
- **IPUMS USA**: Integrated Public Use Microdata Series - https://usa.ipums.org/usa/
- **Geographic Boundaries**: U.S. Census Bureau and IPUMS USA

### Usage Rights
- **Code and Analysis**: Open source for research and educational use
- **Dataset**: Public domain (ACS data) - No restrictions for public use
- **Visualizations and Reports**: Open source with attribution - Suitable for educational and research use
- **Cleaned Datasets**: Available for research, policy analysis, and educational purposes

### Contact for Permissions
For questions about usage rights, data access, or collaboration:
- **Technical Questions**: yijunkim@bu.edu
- **Data Usage Rights**: U.S. Census Bureau and IPUMS USA (public domain)
- **Academic Collaboration**: Contact project team members for research partnerships

---

*This project was completed as part of DS594 Data Visualization course in the Boston University Spark! Program, Fall 2025.*


---


# Spring 2025 DS594 Doubled-up Homelessness Project

## Summary and Final Deliverable

Doubling up—or sharing the housing of others due to economic hardship—is a 
measure of housing insecurity and hidden homelessness. These dashboards show 
estimates of doubled-up homelessness across the United States using a measure 
derived from person-level American Community Survey (ACS) data. 

Click on a state or local area (Census Bureau Public Use Microdata Area, or PUMA) to view 
community-level estimates. Using the drop-down options, identify and compare 
estimates for specific subgroups. You can also explore how your community ranks 
among others through the dynamic bar chart on the right.  This measure of 
doubled-up homelessness was developed by a team of researchers and advocates 
([Richard, Dworkin, Rule, Farooqui, Glendening, & Carlson, 2024](https://www.tandfonline.com/doi/abs/10.1080/10511482.2021.1981976); [Chicago Coalition 
to End Homelessness](https://chicagohomeless.org/).  Estimates in this dashboard were generated and visualized 
by researchers and students at Boston University from a 2018-2022 5-Year ACS 
sample downloaded from [IPUMS USA](https://www.ipums.org/projects/ipums-usa/d010.V15.0) version 15.0.

Note: **Public Use Microdata Areas (PUMAs)** are non-overlapping, statistical geographic areas that partition each state or equivalent entity into geographic areas containing no fewer than 100,000 people each. They cover the entirety of the United States, Puerto Rico, and Guam ([census.gov](https://www.census.gov/programs-surveys/geography/guidance/geo-areas/pumas.html)). 

The FINAL public Tableau dashboard can be accessed here: https://public.tableau.com/app/profile/peiyang.liu/viz/CISS/MainDashboard

Our Github repository is broken down as follows:

* **Data** folder contains raw data (csv) provided by our client, cleaned data (csv) used to make our Tableau dashboard, shape file and a python notebook showing our data cleaning process
* **Visualizations** folder contains screenshots of our completed dashboard (which can also be accessed using the Tableau Public link below)
* **Miscellaneous** folder contains our cient presentation decks, DEMO Day poster, and data dictionary Excel file
* **Workbook** folder contains .twb file and extracted workbook file
* **Dataset documentation** folder contains a more detailed description about the data we used for this project

### Future Semester's Work

Future semesters can explore several directions for advancing this project. One potential improvement involves refining how units are displayed—specifically, adjusting the format when the doubled-up homelessness population falls below 100,000. This could include implementing conditional statements to switch the unit from millions (M) to thousands (k) for clearer representation.

Additional data may be needed to represent poor/near poor population. This demographic only contains percentage information but no weighted total information.

Another stylistic improvement could involve finding a more elegant way to incorporate hyperlinks to the raw datasets and the research that inspired this analysis.

A more comprehensive direction for future semesters could involve developing a meaningful way to integrate all dashboards created in previous semesters (e.g. dashboards by State, MSA, and PUMA) into a unified, interactive interface that enhances the overall user experience.


## Project Overview

Client: Molly Richard, PhD Postdoctorial Associate at Boston University, Center For Innovation In Social Science (richard4@bu.edu)

### Overall Project Objective: To create a dashboard that allows users to visualize and download data on doubled-up homelessness. 

### A. Team

1. Aiganysh Ulanova - Student - aulanova@bu.edu
2. Bader Alhodithi - Student - badera@bu.edu
3. Carol (Qingyuan) Kong - Student - qykong@bu.eu
4. Penny Lin - Student - pennylin@bu.edu

5. William Li - Project Manager - liw25@bu.edu
6. Peiyang Liu - Technical Project Manager - nickpliu@bu.edu

### B. User Stories

- As policy analysts, we want to examine the factors and policies that contribute to households doubling up per state, so that we can develop and analyze targeted policies that address housing instability before it leads to literal homelessness.

- As researchers, we are interested in analyzing the rates of doubled-up homelessness for different demographic groups faced homelessness and whether the rates differ between urban/rural regions, such that we can better understand how policies could be made to address doubled-up homelessness.

- As local government officials, we would like to understand the demographics of people experiencing doubled-up homelessness so that we can allocate housing resources effectively.

### C. Proposed Solutions

We are going to build off of previous semester's progress, updating the geographical detailness, more specifically transitioning from MSA to PUMA.

### D. Tools

1. Tableau
2. Python
3. Google Drive

### E. Data Sources

1. https://drive.google.com/drive/folders/1TNbRB03RlVIT0EhUYfAUw7cYLODN7yaQ
2. https://console.cloud.google.com/bigquery?project=cds-ds-594&ws=!1m0

### F. Data Preparation

With Python or SQL we will explore the data and determine what features we will be suing. 

### G. Color Palette

1. #ADD7F6 - Uranian Blue
2. #87BFFF - Jordy Blue
3. #3F8EFC - Chefchaouen Blue
4. #266755 - Neon Blue
5. #3B28CC - Chrylser blue

