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
├── Final-Project.html
├── Final-Project.md
├── Final-Project_files
│   └── figure-markdown_strict
│       ├── unnamed-chunk-10-1.png
│       ├── unnamed-chunk-6-1.png
│       ├── unnamed-chunk-7-1.png
│       ├── unnamed-chunk-8-1.png
│       └── unnamed-chunk-9-1.png
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

---

### Outputs:

This project generates:

* Scatter plot showing the relationship between number of milk cows and total milk production

![Figure1](
https://github.com/Matioli-amoc/PLPA6820--Final-Project-Amanda/blob/main/figures/Fig_scatter.png)

* Boxplot illustrating milk productivity per cow across U.S. regions

![Figure2](
figures/Fig_boxplot.png)

* Map of average state-level milk production in the United States

![Figure3](
figures/Fig_map.png)

* Time series plot showing milk production trends over time by region

![Figure4](
figures/Fig_trend.png)

* Variability plot showing the standard deviation of milk production across years

![Figure5](
figures/Fig_variability.png)

**All figures are saved in the `figures/` folder.**

---

### Methods Summary

Data were filtered for the last 10 years (2014–present). Analyses include:

* Data cleaning and transformation using `dplyr`, for example:

```r
Dairy.annual <- Dairy.data.US %>%
  filter(Period == "ANNUAL", Year >= 2014) %>% # Subset
  select(Year, Data_item, Value) %>% # Select 
  pivot_wider(names_from = Data_item, values_from = Value)  #Transform from long to wider format
```

* Linear regression models to evaluate relationships between variables:

```r
lm1 <- lm(Milk_production_region ~ Milk_cows_region, data = Dairy.r)
summary(lm1)
```

* Correlation analysis:

```r
cor.test(Dairy.r$Milk_cows_region, Dairy.r$Milk_per_cow_region)
```

* Visualization using `ggplot2`, including scatter plots, boxplots, and maps:

```r
ggplot(Dairy.m, aes(x = Milk_cows_state, y = Milk_production_state, color = Region)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE)
```

All analyses were performed in R using a reproducible workflow supported by R Markdown and `renv`.

---

### Results

Milk production showed an overall increasing trend from 2014 to recent years, although patterns varied across regions. Some regions, such as the Lake States and Mountain Region, displayed consistent growth in milk production over time, while others remained relatively stable or showed slight fluctuations.

The variability analysis indicated that the standard deviation of milk production increased over time, suggesting greater differences among regions in recent years. This may reflect regional specialization or differences in production systems.

Productivity per cow differed across regions, as illustrated in the boxplot. Regions such as the West Coast and Northern Plains showed higher median productivity, while regions like Delta States and Other States had lower values. Additionally, the spread within regions indicates variability in efficiency, likely influenced by management practices and environmental conditions.

Overall, U.S. milk production increased in average output over time, with a moderate increase in variability across regions.

---
### Reproducibility

This project is fully reproducible using:

* R Markdown
* Version control (Git/GitHub)
* renv for package management
* Readme file
---

### Author

Amanda Matioli de Oliveira Chaves

Auburn University




