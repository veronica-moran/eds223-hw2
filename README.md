# Examining Environmental Justice Concerns in Los Angeles Historically HOLC Graded Neighborhoods



## Purpose

This repository contains an exploratory spatial analysis of historical Home Owners' Loan Corporation (HOLC) neighborhood grades in Los Angeles, California. Historical HOLC classifications were compared with recent low-income population percentages, particulate matter 2.5 (PM2.5) and low life expectancy percentiles, and bicycle and pedestrian crashes. The analysis maps historical HOLC neighborhoods and summarizes how these indicators and recorded crashes vary across grades A through D.

## Data

**Data Access**

Historical HOLC data was originally downloaded from University of Richmond's [Mapping Inequality project](https://dsl.richmond.edu/panorama/redlining/data). 

Bike and pedestrian crash data came from the [Statewide Integrated Traffic Records System (SWITRS) database](https://tims.berkeley.edu/). 

The original EJSCREEN data set was obtained from the EPA website and was accessed from a [Google Drive folder](https://drive.google.com/file/d/1nG6Nj1bXfzQFOVMO8Km3eNy4SWu1YcIQ/view). 

**Data Organization**
  
    eds223-hw2/
    ├── README.md
    ├── eds223-hw2.qmd
    ├── eds223-hw2.pdf
    ├── .gitignore
    └── data/                     # local only (not on GitHub)
        ├── ejscreen/
        │   ├── EJSCREEN_2023_BG_Columns.xlsx
        │   ├── EJSCREEN_2023_BG_StatePct_with_AS_CNMI_GU_VI.gdb/
        │   └── ejscreen-tech-doc-version-2-2.pdf
        ├── mapping-inequality/
        │   └── mapping-inequality-los-angeles.json
        └── SWITRS_LA/
            └── Crashes.csv

**Libraries:**

```r
library(tidyverse)
library(sf)
library(here)
library(tmap)
library(gt)
```

Project Variables

- Historical HOLC neighborhood grade (grade: A, B, C, D)

- Low-income population proportion (`LOWINCPCT`)

- PM2.5 percentile (`P_PM25`)

- Low life expectancy percentile (`P_LIFEEXPPCT`)

- Bicycle and pedestrian crash indicators (`BICYCLE_ACCIDENT`, `PEDESTRIAN_ACCIDENT`)

**Data Cleaning**

The HOLC and crash datasets were transformed to match the EJSCREEN coordinate reference system (CRS). Los Angeles County census block groups were converted to centroids and spatially joined with historical HOLC grades. Bicycle and pedestrian crash records were also spatially joined with HOLC grades after removing records with missing coordinates. Records without an assigned HOLC grade were excluded from the income and environmental indicator analyses.

## Author
Veronica Moran

Master of Environmental Data Science (MEDS), UC Santa Barbara

# References

[1] Nelson, R. K., Winling, L., et al. (2023). *Mapping inequality: Redlining in New Deal America*. Digital Scholarship Lab, University of Richmond. (https://dsl.richmond.edu/panorama/redlining/howandwhy)[Accessed October 22, 2026]

[2] Mitchell, B., & Franco, J. (2018, March 20). *HOLC “redlining” maps: The persistent structure of segregation and economic inequality*. National Community Reinvestment Coalition. (https://ncrc.org/holc/) [Accessed October 22, 2026]

[3] Schmidt, K. (2023, October 19). *Structural racism and pedestrian safety*. Public Health Post, Boston University School of Public Health. (https://publichealthpost.org/health-equity/structural-racism-and-pedestrian-safety/) [Accessed October 22, 2026]

[4] Braveman, P. A., Arkin, E., Proctor, D., Kauh, T., & Holm, N. (2022). Systemic and structural racism: Definitions, examples, health damages, and approaches to dismantling. *Health Affairs, 41*(2), 171–178. (https://doi.org/10.1377/hlthaff.2021.01394) 

[5] University of Richmond, Digital Scholarship Lab. (n.d.). Mapping inequality: Redlining in New Deal America [Data set](https://dsl.richmond.edu/panorama/redlining/data)

[6] University of California, Berkeley, Safe Transportation Research and Education Center (SafeTREC). (n.d.). Transportation Injury Mapping System (TIMS): Statewide Integrated Traffic Records System (SWITRS) crash data [Data set](https://tims.berkeley.edu/)

[7] U.S. Environmental Protection Agency. (2023). EJSCREEN 2023: Environmental Justice Screening and Mapping Tool [Data set](https://drive.google.com/file/d/1nG6Nj1bXfzQFOVMO8Km3eNy4SWu1YcIQ/view)