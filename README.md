# Capstone Project - Clinical Survival Analysis

**Project XYZ** is a comprehensive data analysis tool designed to streamline data exploration, analysis, and visualisation. The tool supports multiple data formats and provides an intuitive interface for both novice and expert data scientists.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


## Dataset Content
* Discovery: 30 rows × 10 columns, complete
* Validation: 95 rows × 14 columns, sparse Type.Adjuvant column


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
* Outline the high-level steps taken for the analysis.
* How was the data managed throughout the collection, processing, analysis and interpretation steps?
* Why did you choose the research methodologies you used?

## The rationale to map the business requirements to the Data Visualisations
* List your business requirements and a rationale to map them to the Data Visualisations

## Analysis techniques used
* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques. Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?

## Limitations and Ethical considerations
This project uses a clinical dataset of 125 patient records (30 in the discovery cohort and 95 in the validation cohort). While modest by machine learning standards, this size is representative of many real-world clinical studies, where:
    • Patient recruitment is challenging due to strict eligibility criteria.
    • Early-phase or condition-specific trials often enroll dozens to low hundreds of participants.
    • Larger, multi-center Phase III or IV studies may reach several hundred or thousands, but are less common for exploratory or single-institution studies.
Limitations and Impact on Analysis
    • Machine Learning Constraints
        ○ Small datasets increase the risk of overfitting and reduce generalizability.
        ○ Simple, interpretable models (linear and logistic regression) were chosen over complex algorithms to reflect responsible use of limited data.
    • Statistical Power
        ○ Hypothesis testing and regression analyses may have wider confidence intervals and lower sensitivity to small effects.
        ○ Findings are therefore exploratory and hypothesis-generating, rather than conclusive.
Bias and Representativeness
    • Small sample sizes can overrepresent or underrepresent certain patient subgroups, introducing potential sampling bias.
    • Event imbalance (alive vs deceased) may impact classification accuracy.
    • All results are presented with contextual caveats, avoiding overgeneralization.
Privacy and Responsible Reporting
    • Data is fully de-identified, ensuring patient confidentiality.
    • Analytical outputs are reported with caution and transparency, emphasizing that results are illustrative and educational.
    • Future studies with larger, multi-center cohorts would enhance predictive power and clinical applicability.


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
