# Capstone Project - Clinical Survival Analysis

This project investigates clinical survival data with the aim of uncovering patterns in patient outcomes based on tumour characteristics and genetic mutation status. It combines data cleaning, exploratory analysis, and interactive visualisations to support clear, evidence-based insights. The analysis is tailored for data analysts, developers, and non-clinical stakeholders interested in healthcare data interpretation, with visual tools built in Python (matplotlib, seaborn, Plotly) and Tableau.
# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


## Dataset Content

* Discovery cohort: 30 patients × 10 columns, complete clinical fields (no missing values).
* Validation cohort: 95 patients × 14 columns, includes KRAS and EGFR mutation data with some missing values.

**Note:** The dataset is described as "clinical data for both discovery and validation cohorts" on Kaggle, but it is not specified whether the data is simulated or derived from real-world electronic health records. For the purposes of this project, it will be treated as a realistic case study reflecting the kinds of data seen in single-institution clinical datasets.

Mutation columns (KRAS, EGFR) are simplified for interpretability:
- "Mutated" = any non-negative result
- "Wild-type" = 'Negative'
- "Unknown" = missing data


## Business Requirements
* Identify survival and mortality risk factors
* Support exploratory clustering and basic predictive modeling
* Deliver an interactive dashboard with at least 4 visualizations


## Hypothesis and how to validate?
* Stage is associated with shorter survival time
    - Validate via ANOVA or regression coefficient.

* KRAS genetic mutations are associated with higher mortality risk
    - "Mutation" is simplified as any change in the KRAS gene detected in the dataset 
      (e.g., G12 or G13 codon variants) versus wild-type (no mutation detected).
    - Validate via logistic regression using Event (0/1) as outcome and KRAS status as predictor.
    - Include Fisher's exact or Chi-square test for categorical comparison of mutation vs event.

* Driver mutations (in KRAS or EGFR genes) are associated with higher mortality risk
    - EGFR and KRAS are genes that help regulate cell growth. Mutations in either gene can cause cells to grow uncontrollably, which is a common feature in many cancers.
    - Simplifies clinical genomic data for non-specialist interpretation.
    - Validate via logistic regression and categorical testing.

## Project Plan

This project follows a structured workflow typical of data analytics methodology:

1. **Problem Framing**: Define the clinical relevance of survival analysis and genetic mutation status (e.g., KRAS/EGFR) in non-small cell lung cancer.
2. **Data Acquisition & Understanding**: Load and inspect two datasets — Discovery (n = 30) and Validation (n = 95) cohorts. Summarise their structure and completeness.
3. **Data Cleaning & Preprocessing**:
   - Address missing values
   - Standardise formats (e.g., mutation status, adjuvant therapy)
   - Encode categorical variables for modeling
4. **Exploratory Data Analysis (EDA)**:
   - Visualise survival patterns by stage and mutation
   - Compute correlations
   - Perform basic hypothesis testing (e.g., t-test, ANOVA)
5. **Modeling**:
   - Fit interpretable models (logistic regression, linear regression)
   - Evaluate predictors of mortality and survival time
6. **Dashboard Development**:
   - Create at least 4 Tableau visualisations (bar chart, scatter plot, pie chart, heatmap)
   - Tailor output for both technical and non-technical users
7. **Documentation & Deployment**:
   - Maintain a well-commented GitHub repository
   - Use markdown, visual summaries, and AI-assisted prompts (Copilot, ChatGPT) to enhance clarity and interpretation

This plan ensures that data cleaning, analysis, and interpretation follow a logical progression. Tools such as Git, Jupyter, Tableau, and Python libraries (e.g., Pandas, Seaborn, Plotly) support reproducibility and visual clarity.


## Rationale to Map Business Requirements to Data Visualisations

Each visualisation in this project is directly tied to a business requirement or analytical goal:

| Business Requirement                            | Visualisation Type                      | Rationale |
|--------------------------------------------------|------------------------------------------|-----------|
| Identify survival differences by stage of disease   | Seaborn boxplots, Tableau bar chart      | Visualise median survival time and variability across cancer stages |
| Explore KRAS/EGFR mutation effects               | Plotly stacked bar plot, Tableau pie chart    | Highlight mutation status distribution and outcome association |
| Identify correlations between numerical features | Seaborn heatmap                          | Guide feature selection, flag collinearity |
| Deliver interactive insights                     | Tableau dashboard (multiple visuals)     | Enable intuitive filtering and storytelling for both clinical and technical audiences |

These choices prioritise interpretability and accessibility for both data scientists and stakeholders less familiar with clinical contexts.


## Analysis Techniques Used

This project applies several foundational and intermediate data analysis techniques:

- **Descriptive Statistics**:
  - Summary statistics (mean, median, standard deviation) for survival and numeric features
- **Data Visualisation**:
  - Used `Seaborn`, `Matplotlib`, and `Plotly` to visualise survival distributions, correlations, and mutation associations
- **Hypothesis Testing**:
  - ANOVA to examine survival differences by stage
  - Log-rank test to compare survival between KRAS groups (mutated and wild-type)
- **Categorical Association**:
  - Fisher’s exact test and Chi-square test to analyse relationships between genetic mutations and outcomes
- **Predictive Modeling**:
  - Logistic Regression: Predicts mortality (binary outcome)
  - Linear Regression: Models survival time (continuous variable)
- **Data Preprocessing**:
  - Categorical encoding with `pandas.get_dummies`
  - Filtering unknown/missing data responsibly
  
 Notebook 3 focused on predictive modeling for clinical outcomes. The following techniques were applied:
- **Logistic Regression**: To assess the association between KRAS mutation status and mortality, both univariate and multivariate models were fit. A reduced model was used to resolve convergence issues due to multicollinearity.
- **Kaplan-Meier Survival Analysis**: Used to visualize and compare survival probabilities over time by KRAS status.
- **Log-Rank Test**: Assessed statistical significance between survival curves.
- **Odds Ratio Visualization**: Bar plots with 95% confidence intervals were created for model interpretation.

- **Use of AI Tools**:
- GitHub Copilot and ChatGPT assisted with:
  - Writing/optimising code snippets
  - Markdown generation and ideation
  - Clarifying statistical methodology and simplifying clinical concepts for wider audiences

## Limitations

This project analyzes a clinical dataset of 125 patient records (30 in the discovery cohort and 95 in the validation cohort). While modest by machine learning standards, this size reflects many real-world clinical studies, particularly those in early-phase or exploratory research.  

### Data Size Constraints  
- Small datasets increase the risk of overfitting and reduce generalizability.  
- As a result, simpler, interpretable models (e.g. linear and logistic regression) were prioritized over complex models.  

### Statistical Power  
- With limited sample size, hypothesis testing may yield wide confidence intervals.  
- Smaller effects may go undetected due to reduced sensitivity.  
- Findings should be considered exploratory and hypothesis-generating.

### Data Imbalance & Sampling Bias  
- Class imbalance in outcomes (e.g. survival vs mortality) may influence model performance.  
- Some subgroups (e.g. smokers, mutation carriers) may be underrepresented.  
- These factors may introduce bias into both statistical summaries and predictive models.

## Ethical Considerations

### Patient Privacy and Data Use  
- All data is de-identified; no personally identifiable information is present.  
- The dataset was sourced from a public domain (Kaggle) with open access.  
- The project adheres to ethical standards for secondary data use.

### Transparency and Interpretation  
- All findings are presented with appropriate context and caveats.  
- Interpretations avoid overstating significance or suggesting clinical applicability.  
- Code, assumptions, and data transformations are openly documented.

### Responsible Use of Clinical Data  
- Analytical outputs are for illustrative and educational purposes only.  
- No clinical decisions should be derived from this project’s outputs.  
- Future validation with larger, multi-center datasets would be required for clinical relevance.

## Dashboard Design
The interactive Tableau dashboard communicates the project’s key clinical insights to both technical and non-technical audiences.  
It contains four visualisations arranged for intuitive navigation and filtering:
1. **Mortality by KRAS Mutation** – Grouped bar chart comparing mortality rates between KRAS wild-type and KRAS-mutated patients.
2. **Survival Time by Sex** – Box-and-whisker plot showing the distribution of survival days by patient sex, highlighting differences in median survival and spread.
3. **Age vs Survival Days** – Scatter plot illustrating the relationship between patient age and survival time, with trend lines and shapes to differentiate sex.
4. **KRAS vs EGFR Mutation** – Heatmap showing the intersection of KRAS and EGFR mutation profiles and corresponding patient counts.

### Interactivity and Filters
The dashboard includes filters for:
- **KRAS Mutation**
Toggle between wild-type and mutated cases.
- **EGFR Mutation**
Focus on wild-type or mutated EGFR genetic status.
- **Event (Death / Alive)**
Isolate patients based on survival outcome.
- **Sex (Male / Female)**
Examine survival and clinical patterns stratified by patient sex.

These filters allow users to explore subsets of the data and see how key metrics shift across different patient groups.

### Design for Mixed Audiences
- **Non-technical users** benefit from clear labels, intuitive colour coding, and concise captions.
- **Technical users** can explore more granular details through tooltips, which display counts, percentages, and category definitions on hover.

### Live Dashboard
The dashboard is publicly accessible via Tableau Public:  
[View the Live Dashboard](https://public.tableau.com/app/profile/petal.smart/viz/clinical_survival_analysis_dashboard/ClinicalSurvivalDashboard?publish=yes)


## Unfixed Bugs
No critical bugs remain in the final deliverable. Minor issues during development included:
* Tableau dashboard filter behaviour
In early iterations, interacting with some charts unintentionally hid entire data categories. This was resolved by removing unnecessary filters.
* Inconsistent variable naming between datasets
The cleaned discovery and validation datasets used different default column names and encodings (e.g., Sex_Male vs sex_M). This caused errors in early analysis and model building. This was addressed by standardising column names and focusing the Tableau dashboard on the validation dataset, which had a consistent structure.

These issues were identified and resolved through iterative testing and cross-checking outputs.

## Development Roadmap
* Challenges faced:
  - Tableau’s interface was still fairly unfamiliar, leading to delays in creating interactive and visually appealing charts. This was overcome with guided exploration, assistance from Chat GPT, step-by-step adjustments, and testing chart interactivity.
  - Convergence issues in early logistic regression models due to multicollinearity. This was addressed by simplifying models and removing redundant predictors.

* Future plans:
  - Explore advanced modelling techniques (e.g., penalised regression, Cox proportional hazards models) to improve predictive performance.
  - Incorporate more comprehensive clinical datasets with larger sample sizes.
  - Enhance Tableau dashboards with more granular filters and patient sub-cohort breakdowns.
  - Explore the same or similar datasets using PowerBI

## Main Data Analysis Libraries
* pandas for data loading, cleaning, and manipulation - Example: converting categorical variables into dummy variables for modelling.
* numpy for numerical operations, including array handling and statistical calculations.
* matplotlib for the creation of survival curves and odds ratio visualisations.
* seaborn for enhanced statistical visualisations (e.g., boxplots, correlation heatmaps).
* plotly for interactive plot in exploratory data analysis.
* statsmodels for logistic regression modelling and generation of statistical summaries.

## Project Summary

This project integrated statistical analysis, predictive modelling, and interactive visualisations to examine how clinical and genomic factors influence lung cancer survival. The resulting Tableau dashboard distills complex data into clear, interactive insights tailored for both technical and non-technical audiences. While findings are exploratory due to dataset limitations, the approach provides a solid framework for future validation and extension in larger, more representative cohorts.


## Credits 
### Content 
- Jupyter notebook structure and README template adapted from the Code Institute’s Capstone Project template and guidelines.
- Statistical interpretation methods informed by publicly available resources on Kaplan–Meier survival analysis and logistic regression.
- Tableau dashboard design informed by the wireframe created during project planning.

### Media
- Dashboard wireframe created using Balsamiq.
- All charts and visualisations generated by the author using Python (matplotlib, seaborn, plotly) and Tableau Public.

## Acknowledgements
* Special thanks to Code Institute faciltator, Emma Lamont; data coach, Spencer Barriball; and subject matter expert, Niel McEwen, for general guidance and coaching on statistical approach and visualisation clarity.
