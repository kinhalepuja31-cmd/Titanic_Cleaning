# Titanic_Cleaning

# Titanic Dataset - Data Quality Assessment & Preprocessing
##  Project Overview
Data cleanliness is a critical prerequisite for building accurate predictive models. In this task, the Titanic dataset was subjected to a thorough quality assessment, revealing significant data gaps in three specific features: `Cabin`, `Age`, and `Embarked`. Rather than utilizing listwise deletion (which skews distributions and shrinks sample size), a targeted data imputation strategy was implemented based on data types and distribution patterns.

##  Summary of Data Quality Findings

An initial inspection of the dataset (\(N = 891\) records) showed that **9 out of 12 columns are completely intact**. However, three critical structural gaps were identified:

*   **Cabin (77.1% Missing):** 687 records are missing specific cabin assignments. This immense sparsity makes mathematical imputation unfeasible.
*   **Age (19.9% Missing):** 177 records lack age information. Dropping these rows would discard roughly 20% of the dataset, creating massive selection bias.
*   **Embarked (0.2% Missing):** Only 2 records lack an embarkation port, posing a negligible analytical risk.

## Imputation & Data Cleansing Strategy

The missing values were addressed using a disciplined, documented strategy to preserve data integrity:

| Feature | Missing Count | Action Implemented | Justification |
| **`Embarked`** | 2 | Imputed with **Mode** (`'S'`) | Filled using the most frequent port of embarkation (`S`). With only two gaps, this preserves records perfectly without disrupting category weights. |
| **`Age`** | 177 | Imputed with **Median** | Since age is a skewed numerical variable, the median is a robust central tendency metric that stays unaffected by extreme outliers. |
| **`Cabin`** | 687 | Labeled as **`'Unknown'`** | Because over three-quarters of the column is blank, the missingness itself serves as a structural signal (strongly correlated with lower-class ticketholders). Gaps were explicitly hardcoded as `'Unknown'`. |


##  Getting Started

### Prerequisites
Make sure you have Python 3.x installed along with the required analytical libraries:
pip install pandas numpy matplotlib seaborn 

### File Dependencies
*   **Dataset:** Ensure that your source spreadsheet is named `Titanic-Dataset.xlsx` and placed inside your working directory or targeted `/content/` path.

### Execution
Run the cells sequentially within a Jupyter environment or run your Python file directly to view data frames and compile the final summary quality graph:
python Task12.py


## 📈 Visualizations Included
The script includes an automated data visualization routine using **Matplotlib** and **Seaborn**. It isolates columns containing missing variables from the original uncleaned file and plots a clean, horizontal bar chart highlighting the exact counts and percentage ratios of missing rows for executive presentation.

