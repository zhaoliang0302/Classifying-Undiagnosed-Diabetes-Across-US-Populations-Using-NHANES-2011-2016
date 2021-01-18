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
Thus, two imputation methods were performed to attempt to overcome this issue. KNN imputer and Multiple Imputation.
Both KNN and MI techniques were shown to have very similiar outcomes, however for the sake of this project, the dataset that had been imputed with MI was used for futher analysis.

### Processing and Split
The MI imputed dataset was split into training and testing sets.
Due to class imbalance among variables, sampling technique, SMOTE, was conducted.
Following SMOTE, the training set was standardized. 

## Modeling
In the case of disease diagnoses, having higher recall than precision scores is favored to decrease the chances of overlooking individuals with actual disease and left to be untreated.

### Multinomial Logistic Regression
Multinomial logistic regression was performed (3 classes) at several different thresholds.
It was found that by reducing the threshold to 25%, the overall recall score had seen an increase to ~58%.

### XGBoost (CV Grid)
XGBoost was also performed at different thresholds. However, while recall scores for nondiabetic and diabetic cases increased, the recall scores for undiagnosed cases remained around ~58%.

### Support Vector Machine
Support vector machine was performed at same three thresholds. It was found that recall scores increased for undiagnosed cases to 60%.

## Conclusion
While alghorithmns such as regression, XGBoost, and SVM are very powerful, more data pertaining to undiagnosed cases of diabetes needs to be acquired by the NHANES in order to enhance population surveillance. 
