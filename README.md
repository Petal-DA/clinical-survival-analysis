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
This project followed a structured, end-to-end data science workflow consisting of:

* Data Ingestion & Understanding:
Two datasets (discovery and validation cohorts) were loaded and reviewed for structure, completeness, and relevance to the business goals.
* Data Cleaning & Preparation:
Column names were standardized, missing data handled appropriately, and categorical variables (e.g. mutation status, stage) were simplified for interpretability.
* Exploratory Data Analysis (EDA):
Distribution plots and survival-time comparisons were generated using Python visualisation libraries (matplotlib, seaborn, plotly). Key survival-related variables were identified.
* Modelling:
Predictive models developed to explore how clinical and genomic factors influence survival outcomes.
* Dashboard & Communication:
Tableau used to build a visual analytics dashboard designed for stakeholders without technical or clinical backgrounds.
* Interpretation & Documentation:
Results were interpreted in context, with transparent assumptions and limitations outlined throughout.

This plan aligns with industry-standard data science pipelines while being flexible enough to accommodate clinical data constraints.


## Rationale to map Business Requirements to Data Visualisations
| Business Requirement                                  | Visualisation Type                           | Rationale                                                                                                      |
| ----------------------------------------------------- | -------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Assess survival by stage                              | Seaborn boxplot (Python)                     | Boxplots are intuitive for comparing distributions; stage groupings show clear time differences.               |
| Understand mutation impact on survival                | Plotly interactive boxplot                   | Plotly enables dynamic exploration of survival distributions by KRAS status, suitable for non-clinical users.  |
| Build an interpretable dashboard                      | Tableau bar charts, scatter plots, heat maps | These formats allow high-level insight while supporting filtering, drill-downs, and stakeholder interactivity. |
| Compare death events across clinical/genetic features | Contingency tables + pie/bar charts          | Enables frequency-based comparisons (e.g., mortality by mutation status) for categorical factors.              |


## Analysis techniques used
* Descriptive Statistics & Grouping:
Summary statsitics (e.g., median survival) by stage, mutation, and demographic variables were used to guide insights.
* Data Encoding & Simplification:
Complex variables like "Stage (TNM 8th edition)" and raw mutation codons were transformed into binary or categorical groupings (e.g., Early/Late stage, KRAS mutated/Wild-type) for interpretability.
* Survival Analysis (Boxplots):
Boxplots were used to visually compare survival time across categorical variables, highlighting potential clinical risk factors.
* Classification Models:
Logistic regression and tree-based models used to explore prediction of mortality using selected features.
* Categorical Association Testing:
Chi-square or Fisher's Exact Test used to assess dependence between mutation status and death event.

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
