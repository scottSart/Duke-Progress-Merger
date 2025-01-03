# README for Synthetic Control Analysis and Panel Regression

## Overview
This project implements a synthetic control analysis and panel regression to study the effects of treatments (post-2016 events) on North Carolina and South Carolina energy markets. The study uses multiple datasets and Python libraries to conduct the analysis and visualize the results.

## Project Structure

### 1. Data Preparation
- Normalize variables like energy spend (coal, natural gas, fuel) by dividing by $1 Mn
- Compute energy consumption (kWh) for commercial, residential, and industrial customers.
- Fill missing values in computed columns with `0`.
- Apply logarithmic transformations to key variables to reduce skewness and prepare for regression models.

### 2. Panel Regression
- Use `PanelOLS` from `linearmodels.panel` to estimate fixed effects regressions for NC and SC separately.
- Dependent variables: Logarithm of price variables (`log_Pr_res`, `log_Pr_com`, `log_Pr_indus`).
- Independent variables include customer counts, energy consumption, and interaction terms representing treatments.
- Results for NC and SC are stored and exported to a TXT file.

### 3. Synthetic Control
- Use the `pysyncon` library to implement synthetic control for NC and SC at both state and IOU levels.
- Identify predictors for residential, commercial, and industrial energy price analysis.
- Fit synthetic control models and plot paths comparing treated and control groups before and after the 2016 treatment year.

## Key Scripts and Functions
- **`export_all_results_to_txt`**: Exports regression results to a TXT file for detailed review.
- **`Dataprep` and `Synth`**: Prepare and fit synthetic control models for visualizing counterfactuals.
- **Visualization**: Includes path plots for treated vs. synthetic control over time.

## Dependencies
- Python Libraries:
  - `pandas`: Data manipulation.
  - `numpy`: Numerical computations.
  - `linearmodels.panel`: Panel regression.
  - `pysyncon`: Synthetic control analysis.

## Datasets
- **Input datasets**:
  - `iou_balanced`: Contains IOU-level energy data.
  - `NC_reg`, `SC_reg`: Subsets of state-level data for NC and SC.
- **Key variables**:
  - `Rev_*`: Revenue data for commercial, residential, and industrial sectors.
  - `Pr_*`: Price variables for respective sectors.
  - Interaction terms like `Post16XtreatedNC` and `Post16XtreatedSC`.

## Running the Scripts
1. Ensure all required libraries are installed (`pip install pandas numpy linearmodels pysyncon`).
2. Load the datasets into the script.
3. Run the regression models and synthetic control sections sequentially.
4. Review regression outputs and synthetic control plots.

## Outputs
- **Regression Results**: Saved as a TXT file (`all_results.txt`).
- **Synthetic Control Plots**: Visualizations for residential, commercial, and industrial price impacts over time.
