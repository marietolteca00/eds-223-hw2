## Exploring Patterns of Environmental Justice- EDS-223
- Author: Marie Tolteca, Student at Bren School of Environmental Science and Management, Masters in Environmental Data Science
- Date 10/18/2025
## Data
Data Source:Historical redlining grades (HOLC), current demographic/environmental data (EJScreen), and recent bird observations (birds) — to explore the legacy of redlining in both social‑environmental conditions and biodiversity outcomes. All three datasets can be found the link `Dataset` below:

Dataset: <https://drive.google.com/file/d/14CauXFZkVh_6z2Euq0m1Sq1kHQ31fiMk/view?usp=sharing>

Dataset Citation:

-   United States Environmental Protection Agency. 2015. EJSCREEN. Retrieved:\
    www.epa.gov/ejscreen

-  Global Biodiversity Information Facility. Retrieved:https://eds-223-geospatial.github.io/assignments/gbif.org

-  Mapping Inequality Redlining in New Deal America. Retrieved: https://dsl.richmond.edu/panorama/redlining/data
    
**Objectives:**

-   Build effective, responsible, accessible and aesthetically-pleasing
    maps

-   Practice manipulating vector and raster data to build multi-layer
    maps

-   Practice making maps in R, specifically using tmap

**Reprository Structure**
My reprository structure: 
/Users/marietolteca/Documents/MEDS/EDS-223L/eds-223-hw2/
├── data
│   ├── ejscreen
│       └── EJSCREEN_2023_BG_StatePct_with_AS_CNMI_GU_VI.gdb
│   ├── gbif-birds-LA
│       └── gbif-birds-LA.shp
│   └── mapping-inequality
│       └── mapping-inequality-los-angeles.json
├── figs
│   ├── avg_env_holc.png
│   ├── bird_plot.png
│   └── LA_historical_reds.jpeg
├── eds-223-hw2.Rproj
├── EDS223-HW2.qmd
└── README.md
------------------------------------------------------------------------

## Workflow

**Before Starting: Make sure to add the data folder to your `.gitignore`. Add this line `data/` and click save.**

# 1.  Required packages and setup:
Install and load spatial/data‑manipulation libraries (e.g., tidyverse, sf, tmap, here). Set up the project root so file paths work consistently throughout.
# 2. Read in datasets:
    - Block‑group level EJScreen dataset (`EJSCREEN_2023_BG_StatePct_with_AS_CNMI_GU_VI.gdb`)
    - HOLC redlining polygon layer (`mapping-inequality-los-angeles.json`)
    - Bird observation shapefile (`gbif-birds-LA.shp`)
# 3. Filter region of interest:
    - Subset the EJScreen dataset to Los Angeles (LA) County. This will run the script faster, without running all data not within LA county.
# 4. Coordinate Reference System (CRS) transition:
    - Check each dataset’s CRS. If they differ, transform one or more layers so that all are in the same projection.
    - Using warning messages verify that the CRS alignment is successful before spatial operations.
# 5. Spatial join and Percentage of block groups that fall within each HOLC grade:
    - Spatially join block groups with HOLC grade to assign each block group a HOLC grade.
    - Drop geometry when performing tabular summaries.
    - *Creating a map of historical redlining neighborhoods* Explore historical redlining in Los Angeles and its legacy on present-day environmental justice.
    - *Create Summary Table*: percentage of block groups in each HOLC grade and percentage with no HOLC grade.
# 6. Visualization (*ggplot*) Summarizing current conditions from EJ screen within HOLC grade :
    - Calculate mean values of low‑income percentile, PM2.5 percentile, and life‑expectancy percentile grouped by HOLC grade.
    - Create column plot showing variation across HOLC grades in the percentile variables.
    - Interpreted findings from `avg_env_holc.png`
# 7. Legacy of redlining in biodiversity observations:
    - Perform a spatial join between bird observation points and HOLC grade polygons.
    - Summarise and compute counts/percentages of bird observations by HOLC grade.
    - Using `ggplot` visualize bird observations per HOLC grade.
    - Interpreted results from `bird_plot.png`
    
------------------------------------------------------------------------
## Outputs
##### Saved in `figs` folder for Map and Plots.

-   `LA_historical_reds.jpeg`: Map of Los Angeles historical redlining neighborhoods
-   `avg_env_holc.png`: Column plot of Percentile of low income, particulate matter 2.5, and low life expectancy within HOLC grades
-   `bird_plot.png`: Column plot of percentage of bird oberservations within each HOLC grade in Los Angeles

------------------------------------------------------------------------

## Reproducibility

All analysis was conducted in **R studio** using the packages above for visualization. Code is contained in the `eds223-hw2.qmd` file, and outputs are saved in the `figs` directory.
