Note: If you cannot render the notebook, copy paste url into 
# Machine learning Fairness
https://nbviewer.jupyter.org/

The aim of this page is to:
- Become aware of human unfairness that can inadvertently be reproduced by ML algorithms.
- Be aware of proactive data exploration to identify sources of unfairness before training a model and then evaluating a model to test for said unfairness
- Being aware of how your models/data can be used to propagate unintentional maliciousness.

## Ethics
"Ethics" refers to systematizing, defending, and recommending concepts of right and wrong conduct. For ethical guidelines we can refer to the Principles stated in the Belmont Report:

"The Belmont Report was first written by the National Commission for the Protection of Human Services of Biomedical and Behavioral Research. Prompted in part by problems arising from the Tuskegee Syphilis Study (1932–1972: where African-American men in the study were only told they were receiving free health care from the United States government when in actuality the purpose of the study was to observe the natural history of untreated syphilis) and based on the National Commission for the Protection of Human Subjects of Biomedical and Behavioral Research (1974–1978), the Department of Health, Education and Welfare (HEW) revised and expanded its regulations for the protection of human subjects 45 CFR part 46 in the late 1970s and early 1980s. The Belmont Report[2] summarizes ethical principles and guidelines for research involving human subjects. Three core principles are identified: respect for persons, beneficence, and justice. Three primary areas of application are also stated. They are informed consent, assessment of risks and benefits, and selection of subjects. According to Vollmer and Howard, the Belmont Report allows for a positive solution, which at times may be difficult to find, to future subjects who are not capable to make independent decisions. "


### 1. Respect for Persons:
    - informed consent
    - respect for individuals’ autonomy
    - respect individuals impacted
    - protection for individuals with diminished autonomy or decision making capability
    
### 2. Beneficence:
    - Do not harm
    - assess risk
    
### 3. Justice:
    - equal consideration
    - fair distribution of benefits of research
    - fair selection of subjects
    - equitable allocation of burdens
    
Over and above the core principles we have:

### 4. Respect for Law and Public Interest
    - legal due diligence
    - transparency in methods and results
    - accountability
    
### 5. Security
    - both information security and cognitive security. 
    
## Bias
When we store observations of the world we tend to assume that the observations go without saying. And then our understandings going forward which shape our view of the world are dependent on that experience. This shapes the way we interact with things that do not match that experience. This is called a cognitive blind spot - Assuming your experience is typical. 

Machine learning models are not necessarily inherently objective. Engineers train models by feeding them a data set of training examples, and human involvement in the provision and curation of this data can make a model's predictions susceptible to cognitive blind spots of that engineer as well as the cultural context in which the model was developed.

When building models, it's important to be aware of common human cognitive biases that can manifest in your data and your models, so you can take proactive steps to mitigate their effects

Types of bias:

Bias may be introduced through the bias in data itself or bias in the way the data is collected.

#### Human bias in data - unconscious bias from the world that we may reflect in ML when using the worlds data

    - Reporting bias - people tend not to report the world from an objective stand point, and do not reflect the real world context
    - Selection bias - not random samples
    - Coverage bias
    - non-response bias
    - sampling bias
    - Overgeneralisation - based on limited information (tendency to generalize what is true of individuals to an entire group to which they belong)
    - In group bias - preference for members of a group which you also belong 
    - Out-group homogeneity - people and groups that are unfamiliar to us (groups to which we do not belong) are more similar to each other and more likely to be stereotyped
    
#### Human bias in collection and annotation - unconscious bias in our procedures that might reflect in ML

    - Implicit bias - personal experience doe not necessarily apply more generally
    - Confirmation bias - more likely to process info we agree with
    - automation bias - systems seem more objective when actually they may not be
#### Human bias in requirements of the system - unconscious bias with regards to the solution proposed for a problem

# 3 Steps to protect your machines from you
## Step 1
The first step is to check your own implicit biases, you can do that here: 

https://implicit.harvard.edu/implicit/takeatest.html

## Step 2
The next step is to develop with fairness in mind

## Step 3
Last step: Publish with context so that anyone who comes across your work is aware, this should be done for the data you collect and the models you develop. This is done with Datasheets for your datasets and your models

# Steps 2 and 3 expanded
## There are tentatively two steps in the data process:
   
### 1. EDA (Exploratory data analysis) with fairness in mind
    
An EDA is one in order to understand the dynamics of your data. The idea of doing an EDA with fairness in mind is to ensure that the data skewness within your data-set does not result in unintentional discrimination. It is a good idea to make sure that you investigate the following to ensure they make sense (to you and contextually) for all your features, paying special attention to 

1. Features that exhibit unusual behavior
     a. Data spread/skewness/imbalance 
     b. Top value and bottom value / min and max
     c. Missing values/Nans
     d. Unique values/ zeros 
     e. Train set label imbalance
2. Correlations between features
3. Test/Train set split balance if its a supervised task
4. Any domain questions that may be worth exploring

The following statistical descriptors assist with the above
Central tendency - mode, median, mean
Dispersion - range, quartiles, interquartile range, variance/standard deviation, 
co-movement - co-variance + correlation, linear relationships/non-linear relationships between features

 ### 2. Datasheet for your dataset
    
These questions are "For dataset creators, the primary objective is to encourage careful reflection on the process of creating, distributing, and maintaining a dataset, including any underlying assumptions, potential risks or harms, and implications of use. For dataset consumers, the primary objective is to ensure they have the information they need to make informed decisions about using a dataset, including information about its composition, collection process, recommended uses, and restrictions, as well as any underlying assumptions, potential risks or harms"

Gebru, T., Morgenstern, J., Vecchione, B., Vaughan, J.W., Wallach, H.M., Daumé, H., & Crawford, K. (2018). Datasheets for Datasets. ArXiv, abs/1803.09010.

A. Motivation

    - [ ] A.1 Purpose: For what purpose was this dataset created?
    - [ ] A.2 Creator: Who created the dataset?
    - [ ] A.3. Funding: Which party required the creation of this dataset?
    
B. Composition

    - [ ] B.1 Data format: What data mediums are present in the dataset e.g documents, photos, relational data?
    - [ ] B.2 Volume: How much data is there?
    - [ ] B.3 Sample percentage: Is the data a sample of a larger set and is it sampled at random, is there information missing?
    - [ ] B.4 Instance composition: Is the data raw or is it features?
    - [ ] B.5 Labels: Is there a label or target and is there a recommended test and train split?
    - [ ] B.6 Relationship: Are there relationships between data collections?
    - [ ] B.7 Noise: Is there noise in the dataset?
    - [ ] B.8 Source: Is the data self sourced or does it rely on external resources (e.g twitter) and will data not change?
    - [ ] B.9 Personal Information: Does the dataset contain confidential information?
    - [ ] B.10 Offensive information: Does the dataset contain disturbing information?
    - [ ] B.11 People: Does the dataset relate to people?
    - [ ] B.11.11 Subpopulation: Does the dataset identify subpopulations?
    - [ ] B.11.12 Privacy: Is it possible to identify individuals and their persona sensitive informatin (e.g data that reveals race, ethnicity, sexual orientation, religion)?

C. Collection Process

    - [ ] C.1 Acquisition: How was data acquired (e.g directly observable, reported by subjects, indirectly from other data)?
    - [ ] C.2 Collection mechanism: What collection mechanism was used to collect data (e.g sensor, manual human curation, software program, API)
    - [ ] C.3 Sampling: If the dataset is a subset of a larger population, what was the sampling process?
    - [ ] C.4 Timeframe: What was the timeframe over which data was collected?
    - [ ] C.5 Ethical considerations: Was ethical approval required for data collection, what kind?
    - [ ] C.6 People: Does the dataset relate to people?
        - C.6.1 Source: Did you collect data from individuals directly or from a third party?
        - C.6.2 Consent: Did the individuals give consent for their data to be collected and were they given the option to revoke consent?
    - [ ] C.6.3 Potential Impact: Has a potential impact analysis of this dataset on these people been conducted? 
    
D. Preprocessing

    - [ ] D.1 Preprocessing:  Was any prepossessing conducted?
    - [ ] D.2 Raw Data availability: Is the raw data available? 
    - [ ] D.3 Method availability: Is the preprocessing method/software available? 
    
E. Uses

    - [ ] E.1 Previous usage: Has the dataset been used previously, provide access points if available?
    - [ ] E.2 Future use: Is there anything about the dataset that may impact future uses?
    - [ ] E.3 Prohibited use: Are there tasks for which the dataset should not be used?
    
F. Distribution

    - [ ] F.1 Third parties: Will/can the dataset be distributed to third parties how?
        F.1.1 How?
        F.1.2 When?
        F.1.3 Under copyright?
    - [ ] F.2 Restrictions: Are there distribution restrictions?
    
G. Maintenance

    - [ ] G.1 Who: Who is maintaining the dataset if it is being maintained?
    - [ ] G.2 Contact: How can the maintainer be contacted
    - [ ] G.3 Updtes: Will the dataset be updated    
    
    
## There are tentatively two steps in the model process:

### 1. EMA (Exploratory model analysis) with fairness in mind

The idea of doing an EMA with fairness in mind is to ensure that the model skewness does not result in unintentional danger or harm. This includes understanding how certain features influence the accuracy results of your model. A models transparency can be investigated by checking:

Model feature dependence - which features have the highest weight
Performance of feature subsets - if the model performs better on particular subsets over others


https://github.com/adebayoj/fairml

https://github.com/pymetrics/audit-ai

https://github.com/dssg/aequitas

Theres many more - https://github.com/jphall663/awesome-machine-learning-interpretability

### 2. Datasheet for your Model

When distributing your trained model with particular weights, a particular user context is embedded within that model. It is your responsibility to ensure that you are aware of the context embedded in your model but also that any user of your trained model is aware of this context. The best way to do this is with a checklist like below. (from https://github.com/drivendataorg/deon)

A. Data Collection

    - [ ] A.1 Informed consent: If there are human subjects, have they given informed consent, where subjects affirmatively opt-in and have a clear understanding of the data uses to which they consent?
    - [ ] A.2 Collection bias: Have we considered sources of bias that could be introduced during data collection and survey design and taken steps to mitigate those?
    - [ ] A.3 Limit PII exposure: Have we considered ways to minimize exposure of personally identifiable information (PII) for example through anonymization or not collecting information that isn't relevant for analysis?
    
B. Data Storage

    - [ ] B.1 Data security: Do we have a plan to protect and secure data (e.g., encryption at rest and in transit, access controls on internal users and third parties, access logs, and up-to-date software)?
    - [ ] B.2 Right to be forgotten: Do we have a mechanism through which an individual can request their personal information be removed?
    - [ ] B.3 Data retention plan: Is there a schedule or plan to delete the data after it is no longer needed?
    
C. Analysis

    - [ ] C.1 Missing perspectives: Have we sought to address blindspots in the analysis through engagement with relevant stakeholders (e.g., checking assumptions and discussing implications with affected communities and subject matter experts)?
    - [ ] C.2 Dataset bias: Have we examined the data for possible sources of bias and taken steps to mitigate or address these biases (e.g., stereotype perpetuation, confirmation bias, imbalanced classes, or omitted confounding variables)?
    - [ ] C.3 Honest representation: Are our visualizations, summary statistics, and reports designed to honestly represent the underlying data?
    - [ ] C.4 Privacy in analysis: Have we ensured that data with PII are not used or displayed unless necessary for the analysis?
    - [ ] C.5 Auditability: Is the process of generating the analysis well documented and reproducible if we discover issues in the future?
    
D. Modeling

    - [ ] D.1 Proxy discrimination: Have we ensured that the model does not rely on variables or proxies for variables that are unfairly discriminatory?
    - [ ] D.2 Fairness across groups: Have we tested model results for fairness with respect to different affected groups (e.g., tested for disparate error rates)?
    - [ ] D.3 Metric selection: Have we considered the effects of optimizing for our defined metrics and considered additional metrics?
    - [ ] D.4 Explainability: Can we explain in understandable terms a decision the model made in cases where a justification is needed?
    - [ ] D.5 Communicate bias: Have we communicated the shortcomings, limitations, and biases of the model to relevant stakeholders in ways that can be generally understood?
    
E. Deployment

    - [ ] E.1 Redress: Have we discussed with our organization a plan for response if users are harmed by the results (e.g., how does the data science team evaluate these cases and update analysis and models to prevent future harm)?
    - [ ] E.2 Roll back: Is there a way to turn off or roll back the model in production if necessary?
    - [ ] E.3 Concept drift: Do we test and monitor for concept drift to ensure the model remains fair over time?
    - [ ] E.4 Unintended use: Have we taken steps to identify and prevent unintended uses and abuse of the model and do we have a plan to monitor these once the model is deployed? 
