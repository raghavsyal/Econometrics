## 📖 Overview
This project conducts an econometric analysis of crop production for major crops across Indian districts for the year 2017.  
The primary objective is to model the relationship between crop output and various agricultural inputs, while controlling for environmental factors like rainfall and soil quality.

The analysis involves merging multiple datasets, performing necessary data cleaning and feature engineering, and estimating two distinct types of production functions:

- **Cobb-Douglas Production Function**  
- **Quadratic Production Function**

Through these models, the project aims to answer key economic questions regarding **production efficiency**, **returns to scale**, **diminishing marginal returns**, and **input complementarity**.

---

## 💾 Datasets
The analysis utilizes three separate district-level datasets for the year 2017:

1. **Crop Production and Inputs (ECO221_Project_2025_Final.csv)**  
   Contains district-level data on:
   - Crop Name (`crop`)  
   - Area under Cultivation (`area1000hectares`)  
   - Total Production (`production1000tonnes`)  
   - Irrigated Area (`irrigatedarea1000hectares`)  
   - Fertilizer Consumption (Nitrogen, Phosphate, and Potash in tonnes)  

2. **Rainfall Data (RF_DistrictWise_ECO221_2025.csv)**  
   District-wise monthly rainfall data for 2017.  

3. **Soil Quality Data (Salinity_Alkalinity_ECO221_2025.csv)**  
   District-level index on land degradation due to excess salinity/alkalinity.  

---

## 🛠️ Methodology

The project is executed in two main parts: **Data Preprocessing** and **Econometric Modeling**.

### Part 1: Data Preprocessing and Merging
- **Data Consolidation:**  
  The three datasets (crop production, rainfall, and soil quality) are merged into a single comprehensive file for analysis.  
  Standardizing district names is crucial to avoid data loss.  

- **Rainfall Summary:**  
  Since rainfall data is monthly, a district-wise seasonal rainfall variable is constructed to reflect crop-specific growing seasons.  

- **Variable Transformation:**  
  - To handle log-transformations with zero irrigated area, a new variable is created:  
    `Irrigated Area (new) = Irrigated Area + 1`.  
  - **Unirrigated Area** is defined as:  
    `Total Cropped Area - Irrigated Area (new)`.  

---

### Part 2: Econometric Modeling

#### A. Cobb-Douglas Production Function
- **Form:**  
  ![Cobb-Douglas](https://latex.codecogs.com/svg.latex?Y%20=%20A%20X_1^{\alpha_1}X_2^{\alpha_2}\dots%20X_k^{\alpha_k})
 

- **Model Specification:**  
  - Dependent variable: `log(production)`  
  - Independent variables: `log(area)`, `log(irrigated area)`, `log(unirrigated area)`, fertilizer consumption  
  - Environmental controls: rainfall, soil quality index (not log-transformed)  

- **Diagnostics:**  
  - Outlier detection  
  - Multicollinearity checks  
  - Residual plots for model validation  

#### B. Quadratic Production Function
- **Form:**  
  $$ Y = \beta_0 + \beta_1 X_1 + \beta_2 X_1^2 + \beta_3 X_2 + \beta_4 X_2^2 + \dots $$  

- **Model Specification:**  
  - Variables are kept in original levels  
  - Squared terms included to test for diminishing returns  

---

## ❓ Key Research Questions

1. Provide a detailed summary of all variables in the final merged dataset.  
2. Using the Cobb-Douglas model, interpret estimated coefficients for inputs and controls (with units).  
3. What are the **returns to scale**? Test constant returns to scale for farmer-controlled inputs.  
4. How do **outliers** and **multicollinearity** affect estimation?  
5. Using the Quadratic model, test for **diminishing marginal product** of each input.  
6. Test for **input complementarity** (e.g., effectiveness of fertilizer with vs. without irrigation).  
7. Test whether production functions differ across Indian regions.  
8. Compare Cobb-Douglas and Quadratic models: which is preferable and why?  

---
