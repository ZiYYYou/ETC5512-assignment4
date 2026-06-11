================================================================================
ETC5512 Assignment 4 - Blog Post
How fast can Victoria's emergency departments see you?
A five-year story of waiting times
================================================================================

Author: Chenghuiyu Fan
Student ID: 36427462

PROJECT STRUCTURE

ETC5512-assignment4/
- 36427462-Assignment4.Rproj
- Assignment4-36427462.Rmd
- Assignment4-36427462.html
- README.txt                   
- data_dictionary.csv          
- data/
  -- Emergency-department-care-2024-25.xlsx   
  -- 149331_01_1.csv                          
  -- RA_2021_AUST_GDA94/                      

HOW TO REPRODUCE

1. Open 36427462-Assignment4.Rproj in RStudio (this sets the project root
   so that here::here() resolves all paths; no absolute paths are used).
2. Install required packages if needed:
   install.packages(c("tidyverse", "readxl", "here", "sf"))
3. Knit Assignment4-36427462.Rmd to HTML.

All raw data files are included in the data/ folder, so no download is
required to reproduce the analysis. Full manual download steps for each
file are documented in the "Data Details" tab (Question 3) of the .Rmd.


DATA SOURCES

Data file 1: AIHW Emergency Department Care 2024-25 data tables (XLSX)
  - Source: Australian Institute of Health and Welfare
  - Released: 10 December 2025
  - URL: https://www.aihw.gov.au/hospitals/latest-updates-and-downloads/data
  - Sheets used: Table 5.1, Table 5.3, Table 6.3, Table S5.2
  - Licence: Creative Commons BY 4.0 (open government data)

Data file 2: National HealthDirect Health Facilities (CSV)
  - Source: Geoscience Australia
  - Updated: March 2025
  - URL: https://ecat.ga.gov.au/geonetwork/srv/eng/catalog.search#/metadata/149331
  - Used for: point locations (lat/long) of Victoria's 50 ED services
  - Licence: Creative Commons BY 4.0

Data file 3: Remoteness Area 2021 Shapefile (ASGS Edition 3)
  - Source: Australian Bureau of Statistics
  - Released: July 2021
  - URL: https://www.abs.gov.au/statistics/standards/australian-statistical-geography-standard-asgs-edition-3/jul2021-jun2026/access-and-downloads/digital-boundary-files
  - Used for: remoteness class polygon boundaries for the choropleth map
  - Licence: Creative Commons BY 4.0

IMPORTANT NOTES ON THE DATA

- Suppressed values: the AIHW tables use "n.p." (not published) and ". ."
  (not applicable / no data) instead of empty cells. These are converted
  to NA during cleaning before numeric conversion.
- All AIHW figures are pre-aggregated at the state / hospital peer group
  level. There are no patient-level records and no privacy concerns.
- Coordinate reference systems differ between spatial files: the
  Geoscience Australia CSV uses WGS84 (EPSG:4326) while the ABS shapefile
  uses GDA94 (EPSG:4283). ED points are reprojected with st_transform()
  before mapping.
- Victoria has very limited data for the "Very Remote" remoteness class
  in Table S5.2 (mostly suppressed), so this class appears grey on the
  choropleth map.
- See data_dictionary.csv for a full description of every variable used.
