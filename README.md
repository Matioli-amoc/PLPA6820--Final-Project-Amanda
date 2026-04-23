# PLPA6820--Final-Project-Amanda

## Descriptive Analysis of U.S. Milk Production Data

### Data and Source

This project will use publicly available U.S. milk production data, including quarterly and 
the annual records. Data are provided by the United States Department of Agriculture 
(USDA) and are freely available from the USDA Data Catalog.

These are the data files available for analysis, which can be found on the USDA website and also on GitHub:

[Dairy Data Access USDA](https://www.ers.usda.gov/data-products/dairy-data)

[Data quarterly-milk-factors.csv](https://github.com/Matioli-amoc/PLPA6820--Final-Project-Amanda/blob/main/quarterly-milk-factors.csv)

[Data milk-cows-and-prod.csv](https://github.com/Matioli-amoc/PLPA6820--Final-Project-Amanda/blob/main/milk-cows-and-prod.csv)

### Data Volume

The data consist of two CSV files containing U.S. milk production information at state and national levels across multiple years (2014–present). The datasets include variables such as number of milk cows, milk production per cow, total milk production, and regional/state identifiers.

Together, the files provide approximately five main variables per period, which allows for straightforward data organization and statistical analysis. The data are relatively small in size, which facilitates efficient handling, cleaning, and visualization in R. This structure also improves reproducibility and makes the workflow easy to execute on different systems.

## Research Question

How does U.S. milk production evolve over the years in terms of average output and 
variability?

## File Tree


```
├── Dairy.m.csv
├── figures
│   ├── Fig_boxplot.png
│   ├── Fig_map.png
│   ├── Fig_scatter.png
│   ├── Fig_trend.png
│   └── Fig_variability.png
├── Final Project.Rmd
├── milk-cows-and-prod.csv
├── PLPA6820- Amanda Final Project.Rproj
├── quarterly-milk-factors.csv
├── README.md
├── renv
│   ├── activate.R
│   ├── library
│   │   └── windows
│   ├── settings.json
│   └── staging
└── renv.lock

```

### How to run the project:

This project uses RStudio and the packages versions are managed using RENV.
Some packages examples:
```
tidyverse
dplyr
ggplot2
lme4
emmeans
maps, mapdata, mapproj
```

1. Fork and clone the repository in RStudio terminal using:

```
git clone **URL for the forked repository**
```

2. Open the .Rproj file in RStudio

3. Restore the environment:

   ```r
   renv::restore()
   ```

4. Run the R Markdown file "Final Project.Rmd" to reproduce the analysis and figures.
