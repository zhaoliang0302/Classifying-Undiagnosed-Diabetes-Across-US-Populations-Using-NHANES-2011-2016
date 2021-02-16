# Currently editing
## 73% Recall Score for Classification of Undiagnosed Diabetes Status using Clinical and Questionaire Data from NHANES (2011-2016)

### Dataset
Medical examination data and Questionaire data from NHANES 2011 to 2016 were merged to produce the final dataset.

### Outcome variable
The outcome variable (hemoglobin A1c) was recoded from continuous to categorical (none, diabetic, undiagnosed diabetic).
The categorical variable was combined with physician's self-report data to produce the final variable.

Diabetes was stratified into 3 groups. 
For example, 
  Hemoglobin A1c < 6.5 and physician diagnosis no diabetes = None.
  A1c > 6.5 and physician diagnosis no diabetes = undiagnosed diabetes.
  A1c > 6.5 and physician diagnosis yes diabetes = diabetes.

### Missing Data
The nature of survey data such as the NHANES is prone to limitations such as the presence of missing data and step patterns.
In this dataset medical examination data possessed much higher number of missing values, so to curb this issue Multiple Imputation Chained Equations (MICE) 
was performed.

![alt text](https://github.com/cspark2610/medical-transcription-classification-/blob/main/images/img1.png)

### Processing and Split
Dataset was split into training and testing sets.
Standardized and Normalized on training set to mitigate data leakage, followed by transformation of training and testing set.

## Modeling
In the case of disease diagnoses, having higher recall than precision scores is favored to decrease the chances of overlooking individuals with actual disease and left to be untreated.

### Logistic Regression OVR
Logistic regression OVR produced recall score for undiagnosed diabetes at 63%.

### SVC Linear OVR
SVC Linear OVR produced highest recalled score for undiagnosed diabetes at 73%.
