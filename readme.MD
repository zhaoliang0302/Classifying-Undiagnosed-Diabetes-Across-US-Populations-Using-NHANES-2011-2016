## Classifying Diabetes and Undiagnosed Diabetes Status using NHANES (2011-2016)

### Dataset
Medical examination data and Questionaire data from NHANES 2011 to 2016 were merged to produce the final dataset.

### Outcome variable
The outcome variable (hemoglobin A1c) was recoded from continuous to categorical (none, diabetic, undiagnosed diabetic).
Then the categorical variable was combined with physician's self-report data to produce the final variable.

Diabetes was stratified into 3 groups. 
For example, 
  Hemoglobin A1c < 6.5 and physician diagnosis no diabetes = None.
  A1c > 6.5 and physician diagnosis no diabetes = undiagnosed diabetes.
  A1c > 6.5 and physician diagnosis yes diabetes = diabetes.

### Missing Data
The nature of survey data such as the NHANES is prone to limitations such as the presence of missing data.
In this dataset medical examination data possessed much higher number of missing data (NaNs).
Multiple Imputation chained equations was performed to attempt to overcome this issue.


### Processing and Split
Dataset was split into training and testing sets.
Standardized and Normalized on training set to mitigtgate data leakage, followed by transformation of training and testing set.

## Modeling
In the case of disease diagnoses, having higher recall than precision scores is favored to decrease the chances of overlooking individuals with actual disease and left to be untreated.

### Logistic Regression
Logistic regression OVR produced highest recall score for undiagnosed diabetes,

