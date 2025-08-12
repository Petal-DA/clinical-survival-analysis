# Capstone Project - Clinical Survival Analysis

This project investigates clinical survival data with the aim of uncovering patterns in patient outcomes based on tumour characteristics and genetic mutation status. It combines data cleaning, exploratory analysis, and interactive visualisations to support clear, evidence-based insights. The analysis is tailored for data analysts, developers, and non-clinical stakeholders interested in healthcare data interpretation, with visual tools built in Python (matplotlib, seaborn, Plotly) and Tableau.
# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


## Dataset Content

* Discovery cohort: 30 patients × 10 columns, complete clinical fields (no missing values).
* Validation cohort: 95 patients × 14 columns, includes KRAS and EGFR gene mutation data with some missing values.

### Key Definitions

* KRAS (Kirsten Rat Sarcoma Viral Oncogene Homolog) - A gene that produces a protein involved in cell signalling. Mutations in KRAS can lead to uncontrolled cell growth and are commonly linked to various cancers.
* EGFR (Epidermal Growth Factor Receptor) - A gene that codes for a protein on cell surfaces that helps regulate cell growth and division. Mutations in EGFR can cause abnormal signalling and are often associated with cancer development.

**Note:** The dataset is described as "electronic clinical data" for both discovery and validation cohorts on Kaggle (https://www.kaggle.com/datasets/imtkaggleteam/clinical-dataset), but it is not specified whether the data is simulated or derived from real-world electronic health records. For the purposes of this project, it will be treated as a realistic case study reflecting the kinds of data seen in single-institution clinical datasets.

Gene mutation columns (KRAS, EGFR) are simplified for interpretability:
- "Mutated" = any non-negative result
- "Wild-type" = 'Negative'
- "Unknown" = missing data


## Business Requirements
* Identify survival and mortality risk factors
* Support exploratory classification and basic predictive modelling
* Deliver an interactive dashboard with at least 4 visualizations


## Hypothesis and how to validate?
* Disease stage is associated with shorter survival time
    - Validate via analysis of variance (ANOVA).
      -This hypothesis compares survival time (a continuous outcome) across various disease stages (a categorical predictor). An ANOVA test is appropriate for determining whether mean survival times differ significantly across the stages.

* KRAS genetic mutations are associated with higher mortality risk
    - "Mutation" is simplified as any change in the KRAS gene detected in the dataset 
      (e.g., G12 or G13 codon variants) versus wild-type (no mutation detected).
    - Validate via logistic regression using Event (0/1) as outcome and KRAS status as predictor.
    
* Driver mutations (in KRAS or EGFR genes) are associated with higher mortality risk
    - EGFR and KRAS are genes that help regulate cell growth. Mutations in either gene can cause cells to grow uncontrollably, which is a common feature in many cancers.
    - Clinical genomic data were simplified for non-specialist interpretation.
    - Validated via logistic regression and categorical testing.

## Project Plan

This project follows a structured workflow typical of data analytics methodology:

1. **Problem Framing**: Define the clinical relevance of survival analysis and genetic mutation status (e.g., KRAS/EGFR) in patients with cancer.
2. **Data Acquisition & Understanding**: Load and inspect two datasets: Discovery (n = 30) and Validation (n = 95) cohorts. Summarise their structure and completeness.
3. **Data Cleaning & Preprocessing**:
   - Address missing values
   - Standardise formats (e.g., mutation status, adjuvant therapy)
   - Encode categorical variables for modeling
4. **Exploratory Data Analysis (EDA)**:
   - Visualise survival patterns by stage and mutation
   - Compute correlations
   - Perform basic hypothesis testing (e.g. ANOVA)
5. **Modeling**:
   - Fit interpretable models (logistic regression)
   - Evaluate predictors of mortality and survival time
6. **Dashboard Development**:
   - Create at least 4 Tableau visualisations (bar chart, scatter plot, box plot, heatmap)
   - Tailor output for both technical and non-technical users
7. **Documentation & Deployment**:
   - Maintain a well-commented GitHub repository
   - Use markdown, visual summaries, and AI-assisted prompts (Copilot, ChatGPT) to enhance clarity and interpretation

This plan ensures that data cleaning, analysis, and interpretation follow a logical progression. Tools such as Git, Jupyter, Tableau, and Python libraries (e.g., Pandas, Seaborn, Plotly) support reproducibility and visual clarity.


## Rationale to Map Business Requirements to Data Visualisations

Each visualisation in this project is directly tied to a business requirement or analytical goal:

| Business Requirement                              | Visualisation Type (Tool)                          | Rationale |
|----------------------------------------------------|-----------------------------------------------------|-----------|
| Compare mortality rates between genetic subgroups  | Grouped bar chart (Tableau)                         | Allows quick comparison of mortality rates between KRAS wild-type and KRAS-mutated patients. |
| Examine survival time differences by demographic factors | Box-and-whisker plot (Tableau)                      | Displays median survival days and spread by sex, highlighting differences in distribution. |
| Assess relationships between patient age and survival | Scatter plot with trend lines (Tableau)             | Shows overall correlation patterns and variation, with shapes to distinguish sex. |
| Explore combined mutation profiles (KRAS vs EGFR)  | Heatmap (Tableau)                                   | Reveals frequency distribution of mutation combinations to identify common vs rare profiles. |
| Deliver interactive, filterable clinical insights  | Integrated Tableau dashboard with multi-variable filters | Empowers users to filter by KRAS status, EGFR status, event (death/alive), and sex for flexible exploration. |

These visualisations were chosen for clarity, interpretability, and to ensure relevance for both clinical and non-clinical audiences.



## Analysis Techniques Used
This project applies several foundational and intermediate data analysis techniques:

**Descriptive Statistics**  
- Summary statistics (mean, median, standard deviation) for survival and numeric features.

**Data Visualisation**  
- Used Seaborn, Matplotlib, and Plotly to visualise survival distributions, correlations, and mutation associations.

**Hypothesis Testing**  
- ANOVA to examine survival differences by stage.  
- Log-rank test to compare survival between KRAS groups (mutated and wild-type).

**Categorical Association**  
- Relationships between genetic mutations and outcomes were evaluated using logistic regression models rather than standalone Chi-squared or Fisher’s exact tests. Logistic regression allows estimation of effect size (odds ratios) and adjustment for potential confounders, thereby providing more informative insights.

**Predictive Modelling**  
- Logistic Regression: Predicts mortality (binary outcome).  
- Kaplan-Meier Survival Analysis: Models survival probability over time by KRAS status.

**Data Preprocessing**  
- Categorical encoding with `pandas.get_dummies`.  
- Filtering unknown/missing data responsibly.

Notebook 3 focused on predictive modelling for clinical outcomes:  
- Logistic Regression: Both univariate and multivariate models were fit to assess associations between KRAS mutation status and mortality.  
- Kaplan-Meier Survival Analysis: Visualised and compared survival probabilities over time by KRAS status.  
- Log-rank test: Assessed statistical significance between survival curves.  
- Odds Ratio Visualisation: Bar plots with 95% confidence intervals were created for model interpretation.

**Use of AI Tools**  
GitHub Copilot and ChatGPT assisted with:  
- Writing and optimising code snippets.  
- Markdown generation and ideation.  
- Clarifying statistical methodology and simplifying clinical concepts for wider audiences.

## Limitations

This project analyzes a clinical dataset of 125 patient records (30 in the discovery cohort and 95 in the validation cohort). While modest by machine learning standards, this size reflects many real-world clinical studies, particularly those in early-phase or exploratory research.  

### Data Size Constraints  
- Small datasets increase the risk of overfitting and reduce generalizability.  
- As a result, simpler, interpretable models (e.g. logistic regression) were prioritized over complex models.  

### Statistical Power  
- With limited sample size, hypothesis testing may yield wide confidence intervals.  
- Smaller effects may go undetected due to reduced sensitivity.  
- Findings should be considered exploratory and hypothesis-generating.

### Data Imbalance & Sampling Bias  
- Class imbalance in outcomes (e.g. survival vs mortality) may influence model performance.  
- Some subgroups (e.g. mutation carriers) may be underrepresented.  
- These factors may introduce bias into both statistical summaries and predictive models.

## Ethical Considerations

### Patient Privacy and Data Use  
- All data are de-identified; no personally identifiable information is present.  
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
1. **Mortality by KRAS Mutation Status** – Grouped bar chart comparing mortality rates between KRAS wild-type and KRAS-mutated patients.
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
  - Convergence issues in early logistic regression models due to predictors being too similar to each other (multicollinearity). This was addressed by simplifying models and removing redundant predictors.

* Future plans:
  - Explore advanced modelling techniques (e.g., penalised regression, Cox proportional hazards models) to improve predictive performance.
  - Incorporate more comprehensive clinical datasets with larger sample sizes.
  - Enhance Tableau dashboards with more granular filters and patient sub-cohort breakdowns.
  - Explore the same or similar datasets using PowerBI.

## Main Data Analysis Libraries
* pandas for data loading, cleaning, and manipulation - e.g., converting categorical variables into dummy variables for modelling.
* numpy for numerical operations, including array handling and statistical calculations.
* matplotlib for the creation of survival curves and odds ratio visualisations.
* seaborn for enhanced statistical visualisations (e.g., boxplots, correlation heatmaps).
* plotly for interactive plot in exploratory data analysis.
* statsmodels for logistic regression modelling and generation of statistical summaries.

## Project Summary

This project integrated statistical analysis, predictive modelling, and interactive visualisations to examine how clinical and genomic factors influence survival in patients with cancer. The resulting Tableau dashboard distills complex data into clear, interactive insights tailored for both technical and non-technical audiences. While findings are exploratory due to dataset limitations, the approach provides a solid framework for future validation and extension in larger, more representative cohorts.

## Credits 
### Content 
- Jupyter notebook structure and README template adapted from the Code Institute’s Capstone Project template and guidelines.
- Statistical interpretation methods informed by publicly available resources on Kaplan-Meier survival analysis and logistic regression.
- Tableau dashboard design informed by the wireframe created during project planning.

### Media
- Dashboard wireframe created using Balsamiq.
- All charts and visualisations generated by the author using Python (matplotlib, seaborn, plotly) and Tableau Public.

## Acknowledgements
* Special thanks to Code Institute faciltator, Emma Lamont; data coach, Spencer Barriball; and subject matter expert, Niel McEwen, for general guidance and coaching on data analysis techniques, statistical approach and visualisation clarity.
