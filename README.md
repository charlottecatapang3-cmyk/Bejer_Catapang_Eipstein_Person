
# 🕵️ BEJER_CATAPANG | EPSTEIN FILES – PERSONS OF INTEREST LIST

## 👥 1. Group Formation

- **Group Name:** B&C HistoriX
- **Members:** Bejer, Bryll Justine E. | Catapang, Charlotte
- **Assigned Theme:** Historical Events
- **Topic:** Epstein Files – Persons of Interest List

---

## 📊 2. Project Overview

- **Dataset Title:** Epstein Files – Persons of Interest List
- **Source (URL or Reference):** Kaggle – [Epstein List: Persons of Interest](https://www.kaggle.com/datasets/wilomentena/epstein-list-persons-of-interest?utm_source=chatgpt.com), uploaded by wilomentena.
- **License/Attribution:** The dataset was obtained from Kaggle and is attributed to its uploader, wilomentena. The original sources of the underlying records should also be acknowledged where applicable. The dataset's license should be verified on the Kaggle page before redistribution or reuse.
- **Objective:** To explore, clean, preprocess, and visualize the Epstein Files – Persons of Interest dataset to better understand its structure, data quality, and the patterns present in its recorded information. The project examines attributes such as flight counts, document counts, connections, nationality, and category classifications. Through data preprocessing and exploratory data analysis, the group aims to identify missing values, analyze numerical distributions, examine relationships between variables, detect potential outliers, and explore categorical and temporal patterns where applicable. Using at least ten visualizations, the project seeks to produce a cleaner, more structured dataset and present meaningful findings that support a better understanding of the available data. All findings will be interpreted objectively, recognizing that a person's inclusion in the dataset does not establish wrongdoing or criminal involvement.


## 🔄 3. Flowchart

### 🧭 Decisions in Our Flowchart

Our flowchart includes four main decision diamonds that guide how we prepare the Epstein Files dataset and generate the visualizations.

**1. Missing Values?**

We first checked whether the original dataset contained missing values. If missing values were found, we replaced missing entries in the Bio column with Not available and missing entries in the Nationality column with Unknown. This allowed us to preserve the records without inventing personal information. If no missing values were found in a particular column, its values remained unchanged.

**2. Duplicate Rows?**

We checked for exact duplicate rows in the dataset. If duplicate records were found, we removed the additional copies while retaining the first occurrence. We also examined repeated names separately because individuals with the same name may have different categories, flight counts, document counts, or connections. Therefore, repeated names alone were not treated as duplicate records.

**3. Potential Outliers in Numerical Columns?**

We applied the Interquartile Range (IQR) method to identify potential outliers in the Flights, Documents, and Connections columns. Values outside the calculated lower and upper limits were flagged for further examination. Instead of automatically removing or capping these values, we retained them because unusually high counts may represent legitimate observations in the dataset. Only values independently confirmed as data-entry errors would warrant correction.

**4. More Plots? (i < 10)**

This decision controls the visualization loop. If i < 10 is true, the program executes the next visualization function in plot_functions, generates the graph, adds its title and axis labels, saves it as a PNG file, and displays its caption or interpretation. The counter then increases by one, and the condition is checked again. Once all ten visualizations have been generated, the loop ends.

---

### 🛠️ Changes We Made

As we developed our code, we made several adjustments to ensure that our flowchart accurately represented the final preprocessing and visualization process for the Epstein Files dataset.

**1. We preserved separate copies of the dataset.**

We used df_original to preserve the original CSV for comparison and missing-value analysis. We also created working copies, including df and clean, to perform preprocessing without modifying the original data. This allowed us to examine the original records and compare them with the cleaned dataset.

**2. We specified how missing values were handled.**

Instead of filling missing numerical values with the median and categorical values with the mode, we used explicit placeholders for missing text fields. Missing biographies were replaced with Not available, while missing nationalities were replaced with Unknown. This prevented us from assigning unsupported personal details to individuals.

**3. We improved duplicate checking and data-type validation.**

We focused on exact duplicate rows rather than removing records based only on repeated names. We also validated the Flights, Documents, and Connections columns as numerical variables. Descriptive fields remained textual, while In Black Book was treated as a Boolean variable. We additionally checked whether an unnecessary index column was present in the CSV.

**4. We revised our outlier-handling method.**

We used the IQR method to flag potential outliers rather than automatically capping or deleting them. Since the dataset contains count variables, unusually high values should be examined before being classified as errors. Retaining these values helped preserve potentially meaningful information.

**5. We finalized the ten required visualizations.**

We organized our visualization functions to cover numerical distributions, relationships among variables, missing values, category comparisons, potential outliers, and multivariate analysis. The ten plots include two histograms, a scatter plot, a missing-values bar chart, a category bar chart, a multivariate scatter plot, a correlation heatmap, box plots, a grouped category comparison, and a PCA scatter plot.

**6. We separated readable data from encoded and scaled data.**

We retained the cleaned dataset in its readable form and created a separate model-ready dataset. We applied one-hot encoding to Category and Nationality, converted In Black Book into an integer indicator, and used StandardScaler on the three numerical count variables. This allowed us to perform further numerical analysis without replacing the original counts in the cleaned dataset.

**7. We added captions and automatic figure saving.**

We organized the visualization code using plot_functions and a loop that executes each plotting function. Every graph is saved as a PNG file in project_outputs/plots/, and its corresponding caption or interpretation is displayed. This made the visualization process more organized and consistent with our flowchart.


# 🧹 PREPROCESSING SUMMARY

Based on the flowchart for the project involving the Epstein Files – Persons of Interest List dataset, the following preprocessing steps were applied to prepare the dataset for analysis, machine learning, and visualization.

### 1. Loading the Dataset

Loaded the `epstein_persons_cleaned.csv` dataset using Pandas. Created the original dataset (`df_original`), working dataset (`df`), and cleaning copy (`clean`) to preserve the original data and facilitate preprocessing.

### 2. Inspecting the Dataset

Examined the dataset's dimensions, column names, data types, descriptive statistics, unique values, and missing-value counts to understand its structure and identify potential data quality issues before preprocessing.

### 3. Handling Missing Values

Checked the `Bio` and `Nationality` columns for missing values. If missing values were present, replace missing `Bio` values with `"Not available"` and missing `Nationality` values with `"Unknown"`. If no missing values were found in these columns, the existing values were retained.

### 4. Removing Duplicate Rows

Checked the dataset for exact duplicate rows. If duplicates were found, remove them using duplicate-removal procedures and reset the index. Repeated values in the `Name` column were reported separately and were not automatically removed because identical names do not necessarily indicate duplicate records. If no exact duplicate rows were found, all records were retained.

### 5. Fixing Data Types

Convert the `Flights`, `Documents`, and `Connections` columns into numeric data types using `pd.to_numeric(errors="coerce")`. This ensured that the numerical variables could be used for statistical analysis and visualization. Any missing values created by unsuccessful conversions were also reported.

### 6. Detecting and Assessing Outliers

Used the Interquartile Range (IQR) method to identify potential outliers in `Flights`, `Documents`, and `Connections`. Values below the lower bound or above the upper bound were flagged and summarized. Detected outliers were retained unless they were independently verified as data-entry errors. If no outliers were detected, the observations were retained without modification.

### 7. Encoding Categorical Variables

Converted categorical variables into numerical representations suitable for machine learning. Applied one-hot encoding to the `Category` and `Nationality` columns and converted `In Black Book` into an integer representation. These transformations allowed categorical information to be incorporated into the model-ready dataset.

### 8. Scaling Numerical Features

Applied `StandardScaler` to the `Flights`, `Documents`, and `Connections` columns. Created corresponding scaled columns to standardize the numerical features, giving them approximately zero means and unit standard deviations. The scaled numerical features were then combined with the encoded categorical features to prepare the model-ready dataset.

### 9. Saving the Cleaned Dataset

Exported the cleaned dataset to `project_outputs/epstein_persons_cleaned.csv`. Also saved the encoded and scaled dataset to `project_outputs/model_ready_encoded_scaled.csv`. These files provided separate outputs for the cleaned data and the dataset prepared for machine learning.

### 10. Preparing the Visualization Process

Created the `project_outputs/plots/` directory to store the generated visualizations. Defined the `plot_functions` list and the `save_plot()` helper function to organize the visualization workflow and facilitate saving the resulting plots.

### 11. Generating Data Visualizations

Generated ten visualizations to examine the distribution of numerical variables, missing data, categorical records, relationships among variables, and overall data structure. These included a histogram of Flights, a histogram of Documents, a scatter plot of Flights versus Documents, a missing-values plot of the original dataset, a records-by-category plot, a multivariate scatter plot of Flights, Documents, and Connections, a correlation heatmap of the numerical variables, box plots of Flights, Documents, and Connections, a plot of mean count variables by category, and a Principal Component Analysis (PCA) plot.

Each visualization was formatted, saved as a PNG file in `project_outputs/plots/`, displayed, and closed, with its corresponding caption or insight printed.

### 12. End of the Preprocessing Program

Completed the data preprocessing and visualization workflow after all ten visualizations had been generated and saved. The resulting cleaned dataset, model-ready dataset, and visualization files were prepared for further analysis and interpretation.
