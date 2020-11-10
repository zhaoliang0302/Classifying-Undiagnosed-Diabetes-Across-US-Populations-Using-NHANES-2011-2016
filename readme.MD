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
Then PCA was conducted with an exhibition of feature selection. Feature selection had alluded to the medical examination variables, however, due to the public health protocols sociodemographic variables were kept in model.

### Modeling
In the case of disease diagnosis false positives are far more favorable to have then false negatives.
Therefore, logistic regression 
Performed logistic regression at set thresholds of 0.25, 0.5, 0.75 to assess increase recall score.
Recall was favored over precision because it is more appropriate to have false positives then false negatives in the case with diagnosis. It is better overall to screen patients for disease than rather have no screening at all.

Following models were performed:
Decision trees with cvGrid
Bagged trees
Random Forest with cvGrid
Adaboost
Gradientboost
XGBoost with cvGrid
Support vector machine



# More coming soon!  
