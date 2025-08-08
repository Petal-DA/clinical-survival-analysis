# Capstone Project - Clinical Survival Analysis

**Clinical Survival** 
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

* KRAS mutations are associated with higher mortality risk
    - "Mutation" is simplified as any change in the KRAS gene detected in the dataset 
      (e.g., G12 or G13 codon variants) versus wild-type (no mutation detected).
    - Validate via logistic regression using Event (0/1) as outcome and KRAS status as predictor.
    - Include Fisher's exact or Chi-square test for categorical comparison of mutation vs event.

* Driver mutations (KRAS or EGFR) are associated with higher mortality risk
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
  - t-tests and ANOVA to examine survival differences by stage and mutation status
- **Categorical Association**:
  - Fisher’s exact test and Chi-square test to analyse relationships between genetic mutations and outcomes
- **Predictive Modeling**:
  - Logistic Regression: Predicts mortality (binary)
  - Linear Regression: Models survival time (continuous)
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
* List all dashboard pages and their content, either blocks of information or widgets, like buttons, checkboxes, images, or any other item that your dashboard library supports.
* Later, during the project development, you may revisit your dashboard plan to update a given feature (for example, at the beginning of the project you were confident you would use a given plot to display an insight but subsequently you used another plot type).
* How were data insights communicated to technical and non-technical audiences?
* Explain how the dashboard was designed to communicate complex data insights to different audiences. 

## Unfixed Bugs
* Please mention unfixed bugs and why they were not fixed. This section should include shortcomings of the frameworks or technologies used. Although time can be a significant variable to consider, paucity of time and difficulty understanding implementation are not valid reasons to leave bugs unfixed.
* Did you recognise gaps in your knowledge, and how did you address them?
* If applicable, include evidence of feedback received (from peers or instructors) and how it improved your approach or understanding.

## Development Roadmap
* What challenges did you face, and what strategies were used to overcome these challenges?
* What new skills or tools do you plan to learn next based on your project experience? 


## Main Data Analysis Libraries
* Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.


## Credits 

* In this section, you need to reference where you got your content, media and extra help from. It is common practice to use code from other repositories and tutorials, however, it is important to be very specific about these sources to avoid plagiarism. 
* You can break the credits section up into Content and Media, depending on what you have included in your project. 

### Content 

- The text for the Home page was taken from Wikipedia Article A
- Instructions on how to implement form validation on the Sign-Up page was taken from [Specific YouTube Tutorial](https://www.youtube.com/)
- The icons in the footer were taken from [Font Awesome](https://fontawesome.com/)

### Media

- The photos used on the home and sign-up page are from This Open-Source site
- The images used for the gallery page were taken from this other open-source site



## Acknowledgements (optional)
* Thank the people who provided support through this project.
