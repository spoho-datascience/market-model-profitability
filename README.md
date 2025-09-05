**Replication package for the paper:**

**"Does the consideration of market prices in model selection increase model profitability? Evidence from theory, artificial data and real-world data." by Wunderlich, F., Garnica-Caparros, M., and Memmert, D. (2025)**

## Overview & Folder Structure

The code in this replication material generates the 4 figures (Fig 1 - Fig 4) present in the paper and can be used to obtain all information contained in the 4 relevant tables (Table 3 - Table 6) included in the paper.

The main contents of the repository are the following:

-   `data/`: folder including ananonymised version of the real-world dataset

-   `figures/`: folder including R code to replicate Figures 1 - 4

-   `experiments/`: folder including code to rerun experiments on real-world and artificial data in Jupyter Notebook

-   `results/`: folder where results of experimental runs are stored

**Data**

This folder includes data_real_anonymised.csv, a dataset anonymised for team names and match dates, that is used as data source to generate Figure 3 and results with regard to real-world data (Table 5 and Table 6).

**Figures**

Code used to generate the Figures can be found in the Rmd files Figure_3_FavoriteLongshot.Rmd for Figure 3 and Figures_124_OLR.Rmd for Figure 1, 2 and 4. The folder will also be used to store the generated figures.

**Experiments**

This folder includes two .ipynb files that can be used to replicate results with regard to real-world data (EconomicExperimentRealData.ipynb) and artificial data EconomicExperimentArtificialData.ipynb.

**Results**

Results for the experimental runs are automatically stored in this folder. The name of the results include information on whether it used real or artificial data, whether it displays raw results or result tables and which run the results refer to. For example real_raw_fixed_averageodds.xlsx illustrates raw results from real data for a run with fixed betting on average odds.

## Required steps for replication of the paper results

**Figures 1 to 4** Running of the .Rmd files in R will lead to a generation and storage of Fig1 to Fig4 from the manuscript. No further steps are needed.

**Tables 3 - 6**

Results of the Tables can be replicated using the Python code. Performing the runs does not require any specific computational power, but might require several minutes up to more than an hour per experimental run. Full replication of all results in Table 3 - Table 6 requires three experimental runs on artificial data and six experimental runs on real data. Results of Table 3 and 5 (just involving one experimental run each, can be directly replicated as one results file). Results of Table 4 and 6 need to be gathered from the results of several distinct experimental runs and thus cannot be replicated as one single results file. The information for Table 4 (Table 6) can be found in 12 (6) result files as specified below.

**Table 3**

-   Use EconomicExperimentArtificialData.ipynb
-   Make sure to use the right specification (config = experimentFL)
-   Run the full code
-   The results of Table 3 have been stored in /results/artificial_table_ExperimentFL_Fixed_bm2.xlsx

**Table 4**

-   Use EconomicExperimentArtificialData.ipynb
-   Replication requires three (i.e. two additional) experimental runs with specifications "config = experimentFL" as in Table 3, plus additionally "config = experimentHA" and "config = experimentDraw"
-   Run the full code for each of the specifications
-   The information required for Table 4 can be gathered from 12 result tables across all experimental runs

Favourite-Longshot Fixed 10% -\> artificial_table_ExperimentFL_Fixed_bm2 Favourite-Longshot Fixed 0% -\> artificial_table_ExperimentFL_Fixed_bm1 Favourite-Longshot Kelly 10% -\> artificial_table_ExperimentFL_Kelly_bm2 Favourite-Longshot Kelly 0% -\> artificial_table_ExperimentFL_Kelly_bm1 Home Advantage Fixed 10% -\> artificial_table_ExperimentHA_Fixed_bm2 Home Advantage Fixed 0% -\> artificial_table_ExperimentHA_Fixed_bm1 Home Advantage Kelly 10% -\> artificial_table_ExperimentHA_Kelly_bm2 Home Advantage Kelly 0% -\> artificial_table_ExperimentHA_Kelly_bm1 Draw Fixed 10% -\> artificial_table_ExperimentDraw_Fixed_bm2 Draw Fixed 0% -\> artificial_table_ExperimentDraw_Fixed_bm1 Draw Kelly 10% -\> artificial_table_ExperimentDraw_Kelly_bm2 Draw Kelly 0% -\> artificial_table_ExperimentDraw_Kelly_bm1

**Table 5**

-   Use EconomicExperimentRealData.ipynb
-   Make sure to use the right specification -- betting = FixedBetting(100) -- betting_description = 'fixed' -- odds_type = 'averageodds'
-   Run the full code
-   The results of Table 5 have been stored in /results/real_table_fixed_averageodds.xlsx. Moreover, the table includes the confidence interval reported in the text in relation to Table 5.

**Table 6**

-   Use EconomicExperimentRealData.ipynb

-   Replication requires six (i.e. five additional) experimental runs with the following specifications: betting = FixedBetting(100) -- betting_description = 'fixed' -- odds_type = 'averageodds' as from Table 3, plus additionally betting = ThresholdBetting(0.2) -- betting_description = 'threshold' -- odds_type = 'averageodds' betting = KellyBetting(100) -- betting_description = 'kelly' -- odds_type = 'averageodds' betting = FixedBetting(100) -- betting_description = 'fixed' -- odds_type = 'maximumodds' betting = ThresholdBetting(0.3) -- betting_description = 'threshold' -- odds_type = 'maximumodds' betting = KellyBetting(100) -- betting_description = 'kelly' -- odds_type = 'maximumodds'

-   Run the full code for each of the specifications

-   The information required for Table 6 can be gathered from six result tables across all experimental runs

Average Fixed -\> real_table_fixed_averageodds.xlsx Average Threshold(20%) -\> real_table_threshold_averageodds.xlsx Average Kelly -\> real_table_kelly_averageodds.xlsx Maximum Fixed -\> real_table_fixed_maximumodds.xlsx Maximum Threshold(30%) -\> real_table_threshold_maximumodds.xlsx Maximum Kelly - real_table_kelly_maximumodds.xlsx
