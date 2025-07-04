# Beyond-a-straight-line
This repository contains all the analysis scripts and visualizations associated with the manuscript submitted to *Nature Human Behaviour*. To ensure full reproducibility, this README provides detailed setup instructions.
This repository provides custom codes to replicate the results of our study. 

GENERAL INFORMATION ABOUT THE STUDY
Abstract:
As social media becomes increasingly embedded in daily life, understanding the relationship between its positive and problematic use has become a global priority. Using data from the 2023 Global Digital Wellbeing Survey (N = 30,994 across 35 countries), we investigated how symptoms of Social Media Disorder (SMD) relate to social media-related well-being (SMWB) measured across dimensions of PERMA model. Both constructs showed substantial cross-national variation, however, the different rates of SMD were not consistently associated with certain rates of poor SMWB suggesting that the relationship between the problematic and positive social media use is neither linear nor globally uniform. We applied latent profile analysis to identify distinct configurations defined by specific combinations of SMD symptoms and SMWB scores. These profiles were structurally consistent across regions, suggesting shared global patterns in how individuals experience social media. At the same time, their prevalence across regions varied significantly, reflecting sociocultural differences in how SMD and SMWB co-occur. The findings challenge severity-based models that treat problematic use as universally associated with diminished well-being on social media and highlight the need to study both problematic and positive use without assuming a straightforward negative relationship between them. Therefore, solutions for digital well-being and social media addiction should address this relationship, while also taking into account the cultural and regional context.

Research questions addressed in the present study:
Are all patterns of SMD symptoms equally detrimental to SMWB? How are distinct SMD symptom profiles associated with differences in SMWD? And to what extent do these psychological patterns differ across world regions, reflecting culturally embedded differences in digital life and well-being?

Hypotheses tested in the present study:
1.	There are distinct and replicable psychological profiles defined by patterns of social media disorder symptoms (SMD) and social media-related well-being (SMWB)
2.	These psychological profiles differ meaningfully in both the expression of SMD symptoms and levels of SMWB across the five PERMA domains.
3.	The latent profile structure, defined by patterns of SMD symptoms and SMWB domains remains consistent across world regions, indicating structural invariance.
4.	Despite structural consistency, the prevalence of SMD-SMWB profiles varies markedly across global regions, reflecting different prevalence rates of these profiles

HOW TO RUN THE ANALYSES
Install R and RStudio:
If you haven't already: Download and install **R**: https://cran.r-project.org/
Download and install **RStudio** (recommended): https://posit.co/download/rstudio-desktop/

Install Required R Packages (use the following code prior any analyses:
```r
# Install core CRAN packages
install.packages(c(
  "readr",       # For reading CSV files
  "readxl",      # For reading Excel files
  "openxlsx",    # For writing Excel files
  "stringr",     # For string operations
  "dplyr",       # For data manipulation
  "tidyr",       # For reshaping data
  "ggplot2",     # For visualizations
  "viridis",     # For color scales
  "forcats",     # For factor manipulation
  "tidyLPA",     # For latent profile analysis
  "mice",        # For multiple imputation
  "psych",       # For exploratory factor analysis
  "lavaan",      # For confirmatory factor analysis
  "Rtsne",       # For t-SNE visualization
  "patchwork"    # For combining ggplot2 plots
))

DETAILED INFORMATION ABOUT ALL R-PACKAGES USED IN THE PRESENT STUDY:
R version 4.5.0 (2025-04-11)
Platform: aarch64-apple-darwin20
Running under: macOS Sonoma 14.7.6

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
LAPACK: /Library/Frameworks/R.framework/Versions/4.5-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

time zone: Europe/London
tzcode source: internal

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] scales_1.4.0         multcomp_1.4-28      TH.data_1.1-3        MASS_7.3-65          survival_3.8-3      
 [6] mvtnorm_1.3-3        emmeans_1.11.1       car_3.1-3            carData_3.0-5        caret_7.0-1         
[11] lattice_0.22-6       randomForest_4.7-1.2 nnet_7.3-20          purrr_1.0.4          broom_1.0.8         
[16] mclust_6.1.1         psych_2.5.3          lavaan_0.6-19        Rtsne_0.17           viridis_0.6.5       
[21] viridisLite_0.4.2    tidyr_1.3.1          tidyLPA_1.1.0        readr_2.1.5          mice_3.17.0         
[26] stringr_1.5.1        openxlsx_4.2.8       patchwork_1.3.0      ggplot2_3.5.2        forcats_1.0.0       
[31] dplyr_1.1.4          readxl_1.4.5        

loaded via a namespace (and not attached):
  [1] RColorBrewer_1.1-3    rstudioapi_0.17.1     jsonlite_2.0.0        shape_1.4.6.1        
  [5] magrittr_2.0.3        estimability_1.5.1    jomo_2.7-6            farver_2.1.2         
  [9] nloptr_2.2.1          rmarkdown_2.29        ragg_1.4.0            vctrs_0.6.5          
 [13] minqa_1.2.8           htmltools_0.5.8.1     cellranger_1.1.0      Formula_1.2-5        
 [17] pROC_1.18.5           mitml_0.4-5           sass_0.4.10           parallelly_1.44.0    
 [21] bslib_0.9.0           sandwich_3.1-1        gsubfn_0.7            plyr_1.8.9           
 [25] zoo_1.8-14            lubridate_1.9.4       cachem_1.1.0          lifecycle_1.0.4      
 [29] iterators_1.0.14      pkgconfig_2.0.3       Matrix_1.7-3          R6_2.6.1             
 [33] fastmap_1.2.0         rbibutils_2.3         future_1.49.0         digest_0.6.37        
 [37] textshaping_1.0.1     labeling_0.4.3        timechange_0.3.0      abind_1.4-8          
 [41] httr_1.4.7            compiler_4.5.0        proxy_0.4-27          bit64_4.6.0-1        
 [45] withr_3.0.2           pander_0.6.6          backports_1.5.0       fastDummies_1.7.5    
 [49] pan_1.9               lava_1.8.1            GPArotation_2025.3-1  ModelMetrics_1.2.2.2 
 [53] tools_4.5.0           pbivnorm_0.6.0        MplusAutomation_1.1.1 zip_2.3.2            
 [57] future.apply_1.11.3   glue_1.8.0            quadprog_1.5-8        nlme_3.1-168         
 [61] grid_4.5.0            checkmate_2.3.2       reshape2_1.4.4        generics_0.1.4       
 [65] recipes_1.3.1         gtable_0.3.6          tzdb_0.5.0            class_7.3-23         
 [69] data.table_1.17.2     hms_1.1.3             foreach_1.5.2         pillar_1.10.2        
 [73] vroom_1.6.5           splines_4.5.0         bit_4.6.0             tidyselect_1.2.1     
 [77] knitr_1.50            reformulas_0.4.1      gridExtra_2.3         stats4_4.5.0         
 [81] xfun_0.52             texreg_1.39.4         hardhat_1.4.1         timeDate_4041.110    
 [85] proto_1.0.0           stringi_1.8.7         yaml_2.3.10           boot_1.3-31          
 [89] evaluate_1.0.3        codetools_0.2-20      tibble_3.3.0          cli_3.6.5            
 [93] rpart_4.1.24          xtable_1.8-4          systemfonts_1.2.3     Rdpack_2.6.4         
 [97] jquerylib_0.1.4       Rcpp_1.0.14           globals_0.18.0        coda_0.19-4.1        
[101] parallel_4.5.0        gower_1.0.2           lme4_1.1-37           listenv_0.9.1        
[105] glmnet_4.1-9          ipred_0.9-15          prodlim_2025.04.28    e1071_1.7-16         
[109] crayon_1.5.3          rlang_1.1.6           mnormt_2.1.1         

Once packages are installed, open any .Rmd or .R file in RStudio and press Ctrl+Shift+Enter (or Cmd+Shift+Enter on Mac) to run the code. Each script is self-contained and commented to guide you through what it does.

EXAMPLE: For Demographic plots:
Open RStudio
Load and run R Markdown "demographic_plots.Rmd"

Please, note,LPA analysis is uploaded as a zipped file. To run it, unzipp it first. To complete the LPA.Rmd file, allow for 5 hours (due to bootsrapping procedures)

