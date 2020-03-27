## Classifying undiagnosed diabetes using NHANES 2011-2016

### Creating undiagnosed variable
If hemoglobin a1c(a1c) is < 6.5 and physician self-report diagnosis is 0 then no diabetes.
If a1c is > 6.5 and physician self-report diagnosis 0 then undiagnosed diabetes.
If a1c is > 6.5 and physician self-report diagnosis is 1 then diabetes.

### Visualize missing data pattern.
Medical examination data possess higher proportion of NaNs
Impute missing values using KNN imputer and Multiple Imputation.

### Generate seperate dataframes with corresponding missing value approach as well as baseline and compare.

### Proceed with multiple imputation dataset.

### Conduct PCA for feature selection, however due to interpretation of sociodemographic variables were kept in model.

### Standardized dataset after train test split.

### Conducted SMOTE to handle class imbalance.

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


