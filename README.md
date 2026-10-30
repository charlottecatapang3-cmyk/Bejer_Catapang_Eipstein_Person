
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
- Embed your flowchart image here:
  ```markdown
  ![Preprocessing Flowchart](Eipsteinfiles_Flowchart_Bejer_Catapang.png)
  ```
  <p align="center"><<img width="1700" height="4960" alt="EipsteinFiles_Flowchart_Bejer_Catapang" src="https://github.com/user-attachments/assets/c1461d34-0701-48fa-aa99-6fe667916c59" />
 


  
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


### 🧹 PREPROCESSING SUMMARY

Based on the flowchart for the project involving the Epstein Files – Persons of Interest List dataset, the following preprocessing steps were applied to prepare the dataset for analysis, machine learning, and visualization.

**1. Loading the Dataset**

Loaded the `epstein_persons_cleaned.csv` dataset using Pandas. Created the original dataset (`df_original`), working dataset (`df`), and cleaning copy (`clean`) to preserve the original data and facilitate preprocessing.

**2. Inspecting the Dataset**

Examined the dataset's dimensions, column names, data types, descriptive statistics, unique values, and missing-value counts to understand its structure and identify potential data quality issues before preprocessing.

**3. Handling Missing Values**

Checked the `Bio` and `Nationality` columns for missing values. If missing values were present, replace missing `Bio` values with `"Not available"` and missing `Nationality` values with `"Unknown"`. If no missing values were found in these columns, the existing values were retained.

**4. Removing Duplicate Rows**

Checked the dataset for exact duplicate rows. If duplicates were found, remove them using duplicate-removal procedures and reset the index. Repeated values in the `Name` column were reported separately and were not automatically removed because identical names do not necessarily indicate duplicate records. If no exact duplicate rows were found, all records were retained.

**5. Fixing Data Types**

Convert the `Flights`, `Documents`, and `Connections` columns into numeric data types using `pd.to_numeric(errors="coerce")`. This ensured that the numerical variables could be used for statistical analysis and visualization. Any missing values created by unsuccessful conversions were also reported.

**6. Detecting and Assessing Outliers**

Used the Interquartile Range (IQR) method to identify potential outliers in `Flights`, `Documents`, and `Connections`. Values below the lower bound or above the upper bound were flagged and summarized. Detected outliers were retained unless they were independently verified as data-entry errors. If no outliers were detected, the observations were retained without modification.

**7. Encoding Categorical Variables**

Converted categorical variables into numerical representations suitable for machine learning. Applied one-hot encoding to the `Category` and `Nationality` columns and converted `In Black Book` into an integer representation. These transformations allowed categorical information to be incorporated into the model-ready dataset.

**8. Scaling Numerical Features**

Applied `StandardScaler` to the `Flights`, `Documents`, and `Connections` columns. Created corresponding scaled columns to standardize the numerical features, giving them approximately zero means and unit standard deviations. The scaled numerical features were then combined with the encoded categorical features to prepare the model-ready dataset.

**9. Saving the Cleaned Dataset**

Exported the cleaned dataset to `project_outputs/epstein_persons_cleaned.csv`. Also saved the encoded and scaled dataset to `project_outputs/model_ready_encoded_scaled.csv`. These files provided separate outputs for the cleaned data and the dataset prepared for machine learning.

**10. Preparing the Visualization Process**

Created the `project_outputs/plots/` directory to store the generated visualizations. Defined the `plot_functions` list and the `save_plot()` helper function to organize the visualization workflow and facilitate saving the resulting plots.

**11. Generating Data Visualizations**

Generated ten visualizations to examine the distribution of numerical variables, missing data, categorical records, relationships among variables, and overall data structure. These included a histogram of Flights, a histogram of Documents, a scatter plot of Flights versus Documents, a missing-values plot of the original dataset, a records-by-category plot, a multivariate scatter plot of Flights, Documents, and Connections, a correlation heatmap of the numerical variables, box plots of Flights, Documents, and Connections, a plot of mean count variables by category, and a Principal Component Analysis (PCA) plot.

Each visualization was formatted, saved as a PNG file in `project_outputs/plots/`, displayed, and closed, with its corresponding caption or insight printed.

**12. End of the Preprocessing Program**

Completed the data preprocessing and visualization workflow after all ten visualizations had been generated and saved. The resulting cleaned dataset, model-ready dataset, and visualization files were prepared for further analysis and interpretation.

---

## 📊 DESCRIPTIONS AND INSIGHTS FOR THE 10 DATA VISUALIZATIONS

The following descriptions and insights are based on the visualization code in your uploaded Jupyter Notebook for the Epstein Files – Persons of Interest List dataset. Each description explains what the plot presents, while each insight explains how the visualization can help interpret the data. The insights are phrased carefully because the presence of a record or a statistical relationship does not, by itself, establish wrongdoing.

---

### 1. Histogram — Distribution of Flights

<p align="center">
  <img s<img width="862" height="487" alt="Screenshot 2026-10-30 131324" src="https://github.com/user-attachments/assets/60f76d2a-4bdf-4273-9d7b-919decf80399" />
</p>

| **Description** | **Insight** |
|---|---|
| This histogram displays the distribution of flight counts among the individuals recorded in the dataset. The horizontal axis represents the number of flights, while the vertical axis represents the number of records within each interval. It helps identify common flight-count ranges and determine whether the distribution is concentrated at lower values or extends toward higher values. | The plot is intended to show whether most records have relatively low flight counts and whether a smaller number of records have substantially higher counts. If the distribution has a long right tail, the flight counts are positively skewed, meaning a few high values may influence the mean. The actual distribution should be confirmed by examining the generated histogram. |

---

### 2. Histogram — Distribution of Documents

<p align="center">
  <img <img width="856" height="477" alt="Screenshot 2026-10-30 131340" src="https://github.com/user-attachments/assets/d512acd7-3347-447b-bdb9-6f578f084298" />
</p>

| **Description** | **Insight** |
|---|---|
| This histogram illustrates how document counts are distributed across the records. The horizontal axis represents the number of documents, and the vertical axis shows how many records fall within each interval. It helps reveal the concentration, spread, and possible skewness of the document-count variable. | The visualization can indicate whether document counts are concentrated among lower values or whether a small number of records have much higher counts. A long right tail would suggest that document counts vary considerably across records. This pattern can help identify unusually high values for further examination, but it does not explain why those counts differ. |

---

### 3. Scatter Plot — Flights vs. Documents

<p align="center">
  <img <img width="862" height="485" alt="Screenshot 2026-10-30 131355" src="https://github.com/user-attachments/assets/36c7f3b4-b454-46dc-871c-46361845052d" />
</p>

| **Description** | **Insight** |
|---|---|
| This scatter plot examines the relationship between flight counts and document counts. Each point represents a record, with Flights on the horizontal axis and Documents on the vertical axis. The plot helps identify possible associations, clusters, and observations with unusually high values in either variable. | The Pearson correlation coefficient is calculated by the notebook to quantify the direction and strength of the linear relationship between Flights and Documents. A positive correlation indicates that higher flight counts tend to be associated with higher document counts, while a negative correlation indicates an inverse relationship. A value near zero suggests a weak linear association. However, correlation does not establish causation or explain the circumstances behind individual records. |

---

### 4. Bar Chart — Missing Values in the Original Dataset

<p align="center">
  <img <img width="981" height="477" alt="Screenshot 2026-10-30 131411"src="https://github.com/user-attachments/assets/19f93d54-1331-4306-8dc7-d5b35bb3db9f" />
</p>

| **Description** | **Insight** |
|---|---|
| This bar chart presents the number of missing values in each column of the original dataset before preprocessing. Each bar corresponds to a column, and its height represents the number of missing cells. The visualization helps identify which variables contain incomplete information and may require data-cleaning procedures. | The `Bio` and `Nationality` columns contain missing entries in the supplied dataset. These missing values are addressed during preprocessing by replacing them with `"Not available"` and `"Unknown"`, respectively. Identifying missing values helps improve data completeness, although replacing missing entries does not recover the original information. |

---

### 5. Bar Chart — Records by Category

<p align="center">
  <img <img width="975" height="475" alt="Screenshot 2026-10-30 131424" src="https://github.com/user-attachments/assets/ac728c67-704d-4c35-bb6f-68d1b3066c59" />
</p>

| **Description** | **Insight** |
|---|---|
| This bar chart displays the number of records belonging to each category in the `Category` column. The horizontal axis represents the category labels, while the vertical axis indicates the number of records assigned to each category. It provides an overview of the dataset's categorical composition. | The chart helps determine which categories are most and least represented in the dataset. If some categories have considerably more records than others, the dataset may have an imbalanced category distribution. This imbalance should be considered when comparing categories or conducting further analysis. Category membership alone does not imply wrongdoing. |

---

### 6. Multivariate Scatter Plot — Flights, Documents, and Connections

<p align="center">
  <img <img width="808" height="597" alt="Screenshot 2026-10-30 131438" src="https://github.com/user-attachments/assets/6c38e710-4166-418d-8c3c-c489954367ee" />
</p>

| **Description** | **Insight** |
|---|---|
| This multivariate scatter plot examines three numerical variables simultaneously. Flights is displayed on the horizontal axis, Documents on the vertical axis, and Connections are represented by the color of each point. This approach allows the relationships among the three count variables to be explored in a single visualization. | The plot can reveal whether records with higher flight counts also tend to have higher document counts or connection counts. Differences in point colors may help identify groups of observations with similar or contrasting connection counts. Points located far from the main concentration may warrant additional statistical examination. However, the visualization does not establish the nature or significance of any individual's connections. |

---

### 7. Correlation Heatmap — Flights, Documents, and Connections

<p align="center">
  <img <img width="732" height="602" alt="Screenshot 2026-10-30 131451" src="https://github.com/user-attachments/assets/f918b6c1-d6f2-408c-bfa4-6dd3a0c7b659" />
</p>

| **Description** | **Insight** |
|---|---|
| This heatmap presents the Pearson correlation coefficients among Flights, Documents, and Connections. The variables appear along both axes, and each cell contains a coefficient ranging from −1 to +1. Values closer to +1 indicate stronger positive linear relationships, values closer to −1 indicate stronger negative linear relationships, and values near zero indicate weaker linear relationships. | The heatmap helps identify which pairs of numerical variables have the strongest and weakest linear associations. Strong positive correlations would indicate that two count variables tend to increase together, while weak correlations would suggest a less consistent linear relationship. The numerical coefficients displayed in the heatmap should be used to determine the actual strength and direction of these relationships. Correlation does not establish causation. |

---

### 8. Box Plots — Flights, Documents, and Connections

<p align="center">
  <img <img width="848" height="473" alt="Screenshot 2026-10-30 131503" src="https://github.com/user-attachments/assets/79c786cf-ccfa-4a68-8a58-1fe29df3939b" />
</p>

| **Description** | **Insight** |
|---|---|
| This visualization presents box plots for Flights, Documents, and Connections to compare their distributions, medians, variability, and potential outliers. Each box represents the interquartile range, while the line inside the box represents the median. The whiskers and individual points help reveal the spread of the observations and values that may be unusually high or low. | The box plots help identify which numerical variables have greater variability and which contain potential outliers. Variables with long upper whiskers or points above the main distribution may have a small number of unusually high counts. These observations should be examined carefully rather than automatically removed, since extreme values may be valid records. Because the variables may have different scales, their relative spreads should be interpreted with caution. |

---

### 9. Grouped Bar Chart — Mean Count Variables by Category

<p align="center">
  <img <img width="1092" height="472" alt="Screenshot 2026-10-30 131515" src="https://github.com/user-attachments/assets/153bd9c6-1671-4585-bbc6-d1c1d244c56f" />
</p>

| **Description** | **Insight** |
|---|---|
| This grouped bar chart compares the mean values of Flights, Documents, and Connections across the different categories in the dataset. The horizontal axis represents the category labels, and the vertical axis shows the mean count. Each category contains separate bars for the three numerical variables, allowing their average values to be compared across groups. | The chart helps identify categories with higher or lower average flight, document, and connection counts. Differences in the means may indicate that the numerical characteristics of the records vary across categories. However, the number of records in each category should also be considered, since categories with few observations may have means that are more sensitive to individual values. These differences are descriptive and do not establish the reasons behind the observed patterns. |

---

### 10. Principal Component Analysis (PCA) Plot

<p align="center">
  <img <img width="856" height="610" alt="Screenshot 2026-10-30 131526" src="https://github.com/user-attachments/assets/f6f37b3a-ae54-4f37-98ad-1b98beb10636" />
</p>

| **Description** | **Insight** |
|---|---|
| This PCA scatter plot represents the standardized Flights, Documents, and Connections variables in two dimensions using the first two principal components, PC1 and PC2. Each point represents a record, and the axis labels indicate the percentage of variance explained by each component. PCA reduces the dimensionality of the numerical data while retaining as much variation as possible in the selected components. | The plot helps reveal potential clusters, similarities, and unusual observations based on the combined patterns of the three standardized count variables. Points positioned close together have more similar representations in the two-dimensional PCA space, while widely separated points have more distinct representations. The percentages shown on the axes indicate how much of the total variation is captured by each component. Since the plot is exploratory, any apparent clusters or unusual points would require further analysis before drawing conclusions. |


---

## 🔑 Key Insights

1. **Flight and document counts are highly concentrated at zero.** Approximately 92.4% of records have zero recorded flights, while 84.3% have zero recorded documents. This indicates that the numerical variables are strongly right-skewed, with a small number of records having substantially higher counts.

2. **The dataset is dominated by the associate category.** Of the 1,264 records, 801 belong to the associate category, followed by business with 146 and celebrity with 80. This uneven distribution should be considered when comparing categories and interpreting their statistical summaries.

3. **Flights, documents, and connections have positive correlations.** Flights and Connections have the strongest correlation at approximately 0.884, followed by Documents and Connections at 0.789 and Flights and Documents at 0.691. These relationships suggest that higher recorded counts in one variable tend to occur alongside higher counts in another, although correlation does not imply causation.

4. **Nationality information has substantial missingness.** The original dataset contains 743 missing nationality entries, making it the column with the greatest amount of missing information. Replacing these entries with `Unknown` allows the dataset to be processed more consistently but does not recover the missing nationality details.

5. **A small number of records have unusually high numerical counts.** The maximum recorded values are 553 flights and 900 documents, while the median for Flights, Documents, and Connections is zero. PCA further shows that the first two principal components explain approximately 96.7% of the variance in the three standardized count variables, allowing most of their numerical variation to be represented in two dimensions.

---

Overall, the analysis reveals a dataset with uneven category representation, incomplete information, highly skewed numerical variables, and strong positive relationships among recorded counts. These findings describe patterns in the dataset and should not be interpreted as evidence of wrongdoing by any individual.
