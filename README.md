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
- **Objective:**
  <p align="justify">
  To explore, clean, preprocess, and visualize the Epstein Files – Persons of Interest dataset to better understand its structure, data quality, and the patterns present in its recorded information. The project examines attributes such as flight counts, document counts, connections, nationality, and category classifications. Through data preprocessing and exploratory data analysis, the group aims to identify missing values, analyze numerical distributions, examine relationships between variables, detect potential outliers, and explore categorical and temporal patterns where applicable. Using at least ten visualizations, the project seeks to produce a cleaner, more structured dataset and present meaningful findings that support a better understanding of the available data. All findings will be interpreted objectively, recognizing that a person's inclusion in the dataset does not establish wrongdoing or criminal involvement.
  </p>


## 🔄 3. Flowchart
- Embed your flowchart image here:
  ```markdown
  ![Preprocessing Flowchart](Eipsteinfiles_Flowchart_Bejer_Catapang.png)
  ```
  <p align="center"><img width="1540" height="5114" alt="EipsteinFiles_Flowchart_Bejer_Catapang" src="https://github.com/user-attachments/assets/239a0415-750c-44ef-a92f-f0df58acc7d6" />
 
 
### Decisions in Our Flowchart

<p align="justify">
Our flowchart includes four main decision diamonds that guide how we prepare the Epstein Files dataset and generate the visualizations.
</p>

**1. Missing Values?**

<p align="justify">
YES – Chosen: We found missing values in the Bio and Nationality columns. Instead of deleting entire rows, we filled the missing Bio values with "Not available" and the missing Nationality values with "Unknown". This allowed us to retain the records while addressing incomplete information.
</p>

<p align="justify">
NO: Not applicable, since missing values were identified in the original dataset.
</p>

**2. Duplicate Rows?**

<p align="justify">
YES – Chosen: We implemented drop_duplicates() to remove exact duplicate rows while retaining the first occurrence. We also checked repeated names separately because having the same name does not necessarily mean that two records are duplicates.
</p>

<p align="justify">
NO: If no exact duplicate rows were found, the dataset would remain unchanged during this step.
</p>

**3. Potential Outliers in Numerical Columns?**

<p align="justify">
YES – Chosen: We used the Interquartile Range (IQR) method to identify and flag potential outliers in the Flights, Documents, and Connections columns. We decided to retain the flagged values instead of removing them because unusually high counts may still contain relevant information.
</p>

<p align="justify">
NO: Proceed to the next preprocessing step without modifying the numerical values.
</p>

**4. More Plots? (i < 10)**

<p align="justify">
YES – Chosen: We continued the visualization loop until all ten required plots were generated, displayed, and saved as PNG files.
</p>

<p align="justify">
NO: After completing the tenth visualization, the loop stopped and the program proceeded to the end.
</p>

---

### 🛠️ Changes We Made

<p align="justify">
As we developed our code, we made several adjustments to ensure that our flowchart accurately represented the final preprocessing and visualization process for the Epstein Files dataset.
</p>

**1. We preserved separate copies of the dataset.**

<p align="justify">
We used df_original to preserve the original CSV for comparison and missing-value analysis. We also created working copies, including df and clean, to perform preprocessing without modifying the original data. This allowed us to examine the original records and compare them with the cleaned dataset.
</p>

**2. We specified how missing values were handled.**

<p align="justify">
Instead of filling missing numerical values with the median and categorical values with the mode, we used explicit placeholders for missing text fields. Missing biographies were replaced with Not available, while missing nationalities were replaced with Unknown. This prevented us from assigning unsupported personal details to individuals.
</p>

**3. We improved duplicate checking and data-type validation.**

<p align="justify">
We focused on exact duplicate rows rather than removing records based only on repeated names. We also validated the Flights, Documents, and Connections columns as numerical variables. Descriptive fields remained textual, while In Black Book was treated as a Boolean variable. We additionally checked whether an unnecessary index column was present in the CSV.
</p>

**4. We revised our outlier-handling method.**

<p align="justify">
We used the IQR method to flag potential outliers rather than automatically capping or deleting them. Since the dataset contains count variables, unusually high values should be examined before being classified as errors. Retaining these values helped preserve potentially meaningful information.
</p>

**5. We finalized the ten required visualizations.**

<p align="justify">
We organized our visualization functions to cover numerical distributions, relationships among variables, missing values, category comparisons, potential outliers, and multivariate analysis. The ten plots include two histograms, a scatter plot, a missing-values bar chart, a category bar chart, a multivariate scatter plot, a correlation heatmap, box plots, a grouped category comparison, and a PCA scatter plot.
</p>

**6. We separated readable data from encoded and scaled data.**

<p align="justify">
We retained the cleaned dataset in its readable form and created a separate model-ready dataset. We applied one-hot encoding to Category and Nationality, converted In Black Book into an integer indicator, and used StandardScaler on the three numerical count variables. This allowed us to perform further numerical analysis without replacing the original counts in the cleaned dataset.
</p>

**7. We added captions and automatic figure saving.**

<p align="justify">
We organized the visualization code using plot_functions and a loop that executes each plotting function. Every graph is saved as a PNG file in project_outputs/plots/, and its corresponding caption or interpretation is displayed. This made the visualization process more organized and consistent with our flowchart.
</p>


### 🧹 PREPROCESSING SUMMARY

<p align="justify">
Based on the flowchart for the project involving the Epstein Files – Persons of Interest List dataset, the following preprocessing steps were applied to prepare the dataset for analysis, machine learning, and visualization.
</p>

**1. Loading the Dataset**

<p align="justify">
Loaded the `epstein_persons_cleaned.csv` dataset using Pandas. Created the original dataset (`df_original`), working dataset (`df`), and cleaning copy (`clean`) to preserve the original data and facilitate preprocessing.
</p>

**2. Inspecting the Dataset**

<p align="justify">
Examined the dataset's dimensions, column names, data types, descriptive statistics, unique values, and missing-value counts to understand its structure and identify potential data quality issues before preprocessing.
</p>

**3. Handling Missing Values**

<p align="justify">
Checked the `Bio` and `Nationality` columns for missing values. If missing values were present, replace missing `Bio` values with `"Not available"` and missing `Nationality` values with `"Unknown"`. If no missing values were found in these columns, the existing values were retained.
</p>

**4. Removing Duplicate Rows**

<p align="justify">
Checked the dataset for exact duplicate rows. If duplicates were found, remove them using duplicate-removal procedures and reset the index. Repeated values in the `Name` column were reported separately and were not automatically removed because identical names do not necessarily indicate duplicate records. If no exact duplicate rows were found, all records were retained.
</p>

**5. Fixing Data Types**

<p align="justify">
Convert the `Flights`, `Documents`, and `Connections` columns into numeric data types using `pd.to_numeric(errors="coerce")`. This ensured that the numerical variables could be used for statistical analysis and visualization. Any missing values created by unsuccessful conversions were also reported.
</p>

**6. Detecting and Assessing Outliers**

<p align="justify">
Used the Interquartile Range (IQR) method to identify potential outliers in `Flights`, `Documents`, and `Connections`. Values below the lower bound or above the upper bound were flagged and summarized. Detected outliers were retained unless they were independently verified as data-entry errors. If no outliers were detected, the observations were retained without modification.
</p>

**7. Encoding Categorical Variables**

<p align="justify">
Converted categorical variables into numerical representations suitable for machine learning. Applied one-hot encoding to the `Category` and `Nationality` columns and converted `In Black Book` into an integer representation. These transformations allowed categorical information to be incorporated into the model-ready dataset.
</p>

**8. Scaling Numerical Features**

<p align="justify">
Applied `StandardScaler` to the `Flights`, `Documents`, and `Connections` columns. Created corresponding scaled columns to standardize the numerical features, giving them approximately zero means and unit standard deviations. The scaled numerical features were then combined with the encoded categorical features to prepare the model-ready dataset.
</p>

**9. Saving the Cleaned Dataset**

<p align="justify">
Exported the cleaned dataset to `project_outputs/epstein_persons_cleaned.csv`. Also saved the encoded and scaled dataset to `project_outputs/model_ready_encoded_scaled.csv`. These files provided separate outputs for the cleaned data and the dataset prepared for machine learning.
</p>

**10. Preparing the Visualization Process**

<p align="justify">
Created the `project_outputs/plots/` directory to store the generated visualizations. Defined the `plot_functions` list and the `save_plot()` helper function to organize the visualization workflow and facilitate saving the resulting plots.
</p>

**11. Generating Data Visualizations**

<p align="justify">
Generated ten visualizations to examine the distribution of numerical variables, missing data, categorical records, relationships among variables, and overall data structure. These included a histogram of Flights, a histogram of Documents, a scatter plot of Flights versus Documents, a missing-values plot of the original dataset, a records-by-category plot, a multivariate scatter plot of Flights, Documents, and Connections, a correlation heatmap of the numerical variables, box plots of Flights, Documents, and Connections, a plot of mean count variables by category, and a Principal Component Analysis (PCA) plot.
</p>

<p align="justify">
Each visualization was formatted, saved as a PNG file in `project_outputs/plots/`, displayed, and closed, with its corresponding caption or insight printed.
</p>

**12. End of the Preprocessing Program**

<p align="justify">
Completed the data preprocessing and visualization workflow after all ten visualizations had been generated and saved. The resulting cleaned dataset, model-ready dataset, and visualization files were prepared for further analysis and interpretation.
</p>

---

## 📊 DESCRIPTIONS AND INSIGHTS FOR THE 10 DATA VISUALIZATIONS

<p align="justify">
The following descriptions and insights are based on the visualization code in your uploaded Jupyter Notebook for the Epstein Files – Persons of Interest List dataset. Each description explains what the plot presents, while each insight explains how the visualization can help interpret the data. The insights are phrased carefully because the presence of a record or a statistical relationship does not, by itself, establish wrongdoing.
</p>

---

### 1. Histogram — Distribution of Flights

<p align="center">
  <img <img width="937" height="590" alt="output 1" src="https://github.com/user-attachments/assets/1fef4781-304d-43ae-b3ac-ed63bce3ade7" />



| **Description** | **Insight** |
|---|---|
| <p align="justify">This histogram illustrates the distribution of flight counts among the 1,264 records in the dataset. The horizontal axis represents the number of recorded flights, while the vertical axis indicates the frequency of observations within each interval. The visualization includes a Kernel Density Estimation (KDE) curve and reference lines representing the mean and median to provide a clearer understanding of the distribution histogram displays the distribution of flight counts among the individuals recorded in the dataset.</p> | <p align="justify"> The distribution shows that 1,168 records (92.4%) have zero recorded flights, while only 96 records (7.6%) have at least one flight. The mean is 2.17, whereas the median is 0, with a maximum recorded value of 553. The considerable difference between the mean and median indicates a strongly right-skewed distribution, where a small number of records account for substantially higher flight counts.</p> |

---

### 2. Histogram — Distribution of Documents

<p align="center">
  <img  <img width="937" height="590" alt="output 2" src="https://github.com/user-attachments/assets/7adfad5f-3c58-4fec-b67d-013f34901d2e" />

    
| **Description** | **Insight** |
|---|---|
| <p align="justify">This histogram presents the distribution of document counts across the 1,264 records in the dataset. The horizontal axis represents the number of recorded documents, while the vertical axis indicates the frequency of observations within each interval. A KDE curve and reference lines for the mean and median are included to illustrate the concentration and variability of document counts.</p> | <p align="justify">The histogram reveals that 1,066 records (84.3%) have zero recorded documents, while 198 records (15.7%) have at least one document. The calculated mean is 1.64, while the median is 0, and the maximum recorded value reaches 900. This substantial difference between the mean and median indicates a highly right-skewed distribution. The results suggest that document counts are concentrated among zero and lower values, with a relatively small number of records accounting for extremely high counts.</p> |

---

### 3. Scatter Plot — Flights vs. Documents

<p align="center">
  <img <img width="929" height="684" alt="output 3" src="https://github.com/user-attachments/assets/e2b6845b-4fcb-4164-afe9-d3a0c0f624b3" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This scatter plot examines the relationship between flight counts and document counts across the dataset. Each point represents an individual record, with Flights displayed on the horizontal axis and Documents on the vertical axis. A linear trend line is included to illustrate the general direction of the relationship, while the Pearson correlation coefficient measures the strength and direction of their linear association.</p> | <p align="justify">The calculated Pearson correlation coefficient is 0.691, indicating a moderately strong positive linear relationship between Flights and Documents. This suggests that records with higher flight counts generally tend to have higher document counts. However, the concentration of observations near the lower values and the presence of extreme observations may influence the overall relationship. The result indicates an association between the two variables but does not establish a causal relationship.</p> |

---

### 4. Bar Chart — Missing Values in the Original Dataset

<p align="center">
  <img <img width="1264" height="684" alt="output 4" src="https://github.com/user-attachments/assets/c26af99d-ce21-482b-a5e4-3f0fcc342f9b" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This visualization presents the missing-value patterns in the original dataset using a missingness heatmap and a horizontal bar chart. The heatmap identifies the locations of incomplete entries across the records, while the bar chart summarizes the total number of missing values in each column. It provides an overview of the dataset's completeness before preprocessing.</p> | <p align="justify">The original dataset contains 744 missing values across two columns. The Bio column has 1 missing entry (0.1%), while the Nationality column has 743 missing entries (58.8%). The remaining columns contain no missing values. To address these incomplete entries, the missing Bio value was replaced with "Not available", while missing Nationality values were assigned "Unknown". This approach preserves all 1,264 records while making missing information explicitly identifiable.</p> |

---

### 5. Bar Chart — Records by Category

<p align="center">
  <img <img width="1057" height="684" alt="output 5" src="https://github.com/user-attachments/assets/a4fe4750-7da5-4a28-b900-573cc689f49f" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This horizontal bar chart illustrates the distribution of the 1,264 records according to their corresponding classifications in the Category column. Each bar represents a category, while its length indicates the number of records assigned to that classification. Numerical labels display both the frequency and percentage of each category, allowing comparisons of their representation within the dataset.</p> | <p align="justify">The associate category has the highest representation, containing 801 records (63.4%), followed by business with 146 records (11.6%) and celebrity with 80 records (6.3%). Meanwhile, military-intelligence has the lowest representation, with only 3 records (0.2%), followed by royalty with 9 records (0.7%). These results demonstrate an uneven categorical distribution, with associates accounting for nearly two-thirds of the dataset. This imbalance should be considered when comparing the characteristics of different categories.</p> |

---

### 6. Multivariate Scatter Plot — Flights, Documents, and Connections

<p align="center">
  <img <img width="1123" height="778" alt="output 6" src="https://github.com/user-attachments/assets/648c4e43-75ff-4ea4-9e7a-3d0f07332a86" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This multivariate scatter plot examines three numerical variables simultaneously: Flights, Documents, and Connections. Flights is represented on the horizontal axis, Documents on the vertical axis, and Category is distinguished through different point colors. The size of each marker represents the number of Connections, allowing the visualization to communicate three numerical or categorical characteristics within a single plot.</p> | <p align="justify">The visualization represents all 1,264 records, with recorded values reaching a maximum of 553 Flights, 900 Documents, and 123 Connections. Most observations are concentrated near the lower values, while a smaller number extend toward substantially higher counts. The marker sizes provide an additional comparison of connection counts, while the different colors distinguish the ten categories. These patterns demonstrate considerable variation among the records and highlight observations that may require further statistical examination.</p> |

---

### 7. Correlation Heatmap — Flights, Documents, and Connections

<p align="center">
  <img <img width="822" height="686" alt="output 7" src="https://github.com/user-attachments/assets/75fe4c58-8876-449d-8430-02c2c4ef9fe3" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This correlation heatmap presents the Pearson correlation coefficients among Flights, Documents, and Connections. Each cell displays the correlation between a pair of numerical variables, with values ranging from -1 to +1. The diagonal values represent the perfect correlation of each variable with itself, while the remaining cells illustrate the strength and direction of relationships between different variables.</p> | <p align="justify">TThe heatmap reveals positive correlations among all three numerical variables. Flights and Connections have the strongest relationship, with a coefficient of 0.884, followed by Documents and Connections at 0.789. Meanwhile, Flights and Documents have a correlation coefficient of 0.691. These results indicate that higher values in one variable generally tend to be associated with higher values in the other variables. Among the three relationships, Flights and Connections demonstrate the strongest linear association. However, these correlations do not establish causation.</p> |
---

### 8. Box Plots — Flights, Documents, and Connections

<p align="center">
  <img <img width="984" height="684" alt="output 8" src="https://github.com/user-attachments/assets/7c18de7b-dc16-42bb-b0ff-f390dd2156c6" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This visualization presents box plots for Flights, Documents, and Connections to compare their medians, interquartile ranges, variability, and potential outliers. Each box represents the interquartile range (IQR), while the line inside the box indicates the median. Diamond markers represent the mean, and individual points beyond the whiskers identify potential outliers based on the IQR method.</p> | <p align="justify">The box plots show that all three variables have a median of 0 and an interquartile range of 0, indicating that at least 75% of the records have zero values for each variable. The mean values are 2.17 for Flights, 1.64 for Documents, and 0.94 for Connections. Using the IQR method, 96 flight observations, 198 document observations, and 157 connection observations are identified as potential outliers. Since the upper quartile and lower quartile are both zero, all nonzero observations exceed the calculated upper fence. These values should not automatically be removed because they may represent valid observations within the dataset.</p> |

---

### 9. Grouped Bar Chart — Mean Count Variables by Category

<p align="center">
  <img <img width="1353" height="778" alt="output 9" src="https://github.com/user-attachments/assets/f9229784-3aaa-4718-bab5-caeca0d3e6a8" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This visualization compares the average values of Flights, Documents, and Connections across the eight most frequently represented categories in the dataset. The three panels display the mean values of each numerical variable separately, while the horizontal bars represent the different category classifications. This arrangement allows comparisons of average flight, document, and connection counts across categorical groups.</p> | <p align="justify">The results show that the Other category has the highest average values across all three numerical variables, with 10.76 Flights, 8.07 Documents, and 3.22 Connections. It is followed by Politician in average Flights (2.48), Associate in average Documents (1.80), and Politician in average Connections (1.52). In contrast, Academic has the lowest average flight count at 0.12, while Celebrity has the lowest average document count at 0.08. These differences indicate that the numerical characteristics vary across categories. However, the number of observations in each category should also be considered when interpreting the averages.</p> |

---

### 10. Principal Component Analysis (PCA) Plot

<p align="center">
  <img <img width="1106" height="781" alt="output 10" src="https://github.com/user-attachments/assets/40415c30-51ee-4e89-af2b-a3b017f8f3e5" />


| **Description** | **Insight** |
|---|---|
| <p align="justify">This PCA scatter plot presents a two-dimensional representation of the dataset using Principal Component Analysis. The analysis uses standardized numerical variables, the In Black Book indicator, and one-hot-encoded Category and Nationality variables. The resulting dataset contains 80 features, which are transformed into two principal components, PC1 and PC2. Each point represents an individual record, while different colors distinguish the category classifications. The axis labels indicate the percentage of total variance explained by each principal component.</p> | <p align="justify">The first principal component (PC1) explains 4.77% of the total variance, while the second principal component (PC2) explains 3.27%. Combined, the two components account for only 8.04% of the total variation in the original 80-feature dataset. This indicates that the two-dimensional representation captures only a relatively small portion of the dataset's overall information. Although the visualization helps examine possible similarities, differences, and group distributions among records, the limited explained variance means that apparent clusters should be interpreted cautiously. Additional principal components would be needed to represent a greater proportion of the dataset's variability.</p> |


---

## 🔑 Key Insights

1. **Flight and document counts are highly concentrated at zero.** <p align="justify">Approximately 92.4% of records have zero recorded flights, while 84.3% have zero recorded documents. Both variables exhibit strongly right-skewed distributions, with a relatively small number of records accounting for substantially higher counts. The median for both variables is zero, despite their respective mean values of 2.17 and 1.64.</p>

2. **The dataset is dominated by the associate category.** <p align="justify">Of the 1,264 records, 801 (63.4%) belong to the associate category, followed by business with 146 (11.6%) and celebrity with 80 (6.3%). This indicates an uneven categorical distribution, with associates representing nearly two-thirds of the dataset. Such an imbalance should be considered when comparing categories and interpreting their statistical summaries.</p>

3. **Flights, documents, and connections have positive correlations.** <p align="justify">All three numerical variables demonstrate positive linear relationships. Flights and Connections have the strongest correlation at 0.884, followed by Documents and Connections at 0.789 and Flights and Documents at 0.691. These results indicate that higher recorded counts in one variable generally tend to occur alongside higher counts in another. However, correlation does not establish causation.</p>

4. **Nationality information has substantial missingness.** <p align="justify">The original dataset contains 743 missing nationality entries, equivalent to approximately 58.8% of all records. Meanwhile, the Bio column contains only one missing entry. To address these incomplete values, missing Nationality entries were replaced with Unknown, while the missing Bio entry was replaced with Not available. This preprocessing approach preserves the records while making incomplete information identifiable, although it does not recover the original missing details.</p>

5. **A small number of records have unusually high numerical counts.** <p align="justify">The maximum recorded values reach 553 flights, 900 documents, and 123 connections, while the median for all three variables is zero. Using the Interquartile Range (IQR) method, 96 flight observations, 198 document observations, and 157 connection observations are identified as potential outliers. Furthermore, Principal Component Analysis (PCA) shows that PC1 explains 4.77% of the variance, while PC2 explains 3.27%, resulting in a combined explained variance of only 8.04%. This indicates that the two-dimensional PCA representation captures a relatively small portion of the variation across the 80 encoded and standardized features.</p>

---

<p align="justify">
Overall, the analysis reveals a dataset characterized by an uneven categorical distribution, substantial missing information in the Nationality column, highly right-skewed numerical variables, and positive correlations among Flights, Documents, and Connections. The identification of potential outliers and the application of PCA further demonstrate the importance of examining data distributions and relationships before conducting additional analysis. These findings provide a statistical overview of the available records and should not be interpreted as evidence of wrongdoing or illegal involvement by any individual.
</p>


## 7. How to Run
<p align="justify">
The project notebook is designed to run in Google Colab. Follow the steps below to reproduce the data preprocessing procedures, visualizations, and generated outputs for the Epstein Files – Bejer-Catapang project.
</p>

### 1. Access the Google Colab Notebook
<p align="justify">
- Open the project repository and locate `Bejer_Catapang_Eipstein_Person.ipynb`.
- Download the notebook and upload it to [Google Colab](https://colab.research.google.com/?utm_source=chatgpt.com).
</p>

### 2. Prepare the Dataset
<p align="justify">
- Download the Epstein List – Persons of Interest dataset from [Kaggle](https://www.kaggle.com/datasets/wilomentena/epstein-list-persons-of-interest?utm_source=chatgpt.com).
- The notebook uses `epstein-persons-2026-02-13_cleaned.csv`, which contains the information required for the data preprocessing procedures and visualizations.
- Follow the notebook's dataset-loading instructions. If automatic dataset loading is unavailable, upload the CSV file when prompted by the notebook.
</p>

### 3. Install Dependencies and Run the Notebook
<p align="justify">
- Make sure the required Python libraries are available in the Google Colab environment.
- If dependency installation is required, install the packages listed in `requirements.txt`, including pandas, numpy, matplotlib, seaborn, and scikit-learn.
- Execute the notebook cells sequentially, starting from the first cell.
- Allow each section to finish before proceeding to the next one.

The notebook performs dataset inspection, missing-value analysis and handling, duplicate checking, data-type verification, data cleaning, outlier detection, categorical analysis, feature preparation, and data saving.
</p>

### 4. Review the Generated Results
<p align="justify">
After executing the notebook, review the generated visualizations and findings.

- The notebook produces ten visualizations with corresponding descriptions and insights.
- Review the key findings and interpretations presented in the notebook.
- Examine the distribution of numerical variables, relationships between selected variables, categorical patterns, missing values, and other relevant characteristics of the dataset.
- Check the generated preprocessing summary for the actual dataset statistics and results.

### 5. Locate the Output Files
<p align="justify">
The notebook generates the following outputs:

| File/Folder                               | Description                                                                        |
| ----------------------------------------- | ---------------------------------------------------------------------------------- |
| `data/cleaned_epstein_persons.csv`        | Cleaned dataset after the preprocessing procedures.                                |
| `data/encoded_scaled_epstein_persons.csv` | Processed dataset containing encoded and scaled numerical features, if applicable. |
| `results/`                                | Generated visualizations, key findings, and preprocessing summaries.               |
</p>

### 6. Verify the Results
<p align="justify">
Review the notebook's verification section to confirm that:

- The generated CSV files can be loaded successfully.
- The expected columns are present in the cleaned dataset.
- Missing values and duplicate records are handled according to the implemented preprocessing procedures.
- Numerical and categorical data are processed appropriately.
- The original dataset remains unchanged.
- The generated visualizations, results, and summary files are saved successfully.
</p>
