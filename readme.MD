## 73% Recall Score for Classification of Undiagnosed Diabetes Status using Clinical and Questionaire Data from NHANES (2011-2016)

### Dataset
Aggregated medical examination data and questionaire data from NHANES 2011 to 2016. The dataset contains 29,902 observations.

### Outcome variable
The outcome variable (hemoglobin A1c) was recoded from continuous to categorical (none, diabetic, undiagnosed diabetic).
The categorical variable was combined with physician's self-report data to produce the final variable.

Diabetes was stratified into 3 groups. 
For example, 
  * Hemoglobin A1c < 6.5 and physician diagnosis no diabetes = None.
  * A1c > 6.5 and physician diagnosis no diabetes = undiagnosed diabetes.
  * A1c > 6.5 and physician diagnosis yes diabetes = diabetes.
### Data Prep
Based on domain knowledge, a handful of known risk factors were selected as features.

* Social Behavioral Factors: age, race, education, sex, citizen, alcohol, veteran, smoke, 
* Clinical Factors: BMI, BUN, systolicBP, AST, ALT

Categorical features were converted to dummies.

### Missing Data

![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_1.png)

Figure above shows the pattern of missing values. If we were to drop rows, we would have insufficient data.
The nature of survey data such as the NHANES is prone to having lots of missing values, and come in forms as step patterns.

Rather than imputing missing values by mean or median, I decided to use Multiple Imputation Chained Equations (MICE) to provide better estimates.

![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_2.png)

The figure above depicts the difference made through imputation. Since diabetes is our placeholder target variable, the density increases at point 0 and 1;
0 representing no diabetes and 1 with diabetes.


![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_5.png)

After, cleaning, imputing, and transforming our target variable (mentioned above) with 3 groups, we are left with the above proportion, which is evidently
imbalanced.


### Overview of Risk Factors by Diabetes Classes
![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_3.png)

The figure above can be a bit confusing to interpret due to the fact that these variables are categorical dummies' (I seperated dummy and non-dummy).
But, it is shown that those without a college degree or has an associates degree has a higher mean value closer to having diabetes. Non-Hispanic whites more cases of diabetes diagnoses than non-hispanic blacks; HOWEVER, looking at the undiagnosed columns, non-hispanic blacks appear to have higher undiagnosed cases than non-hispanic whites. Smokers, alcohols, and veterans have higher mean values in diagnosed and undiagnosed blocks compared to no diabetes, which is corroborated by research.

![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_4.png)

This figure depicts clinical factors and age* (social factor but continuous). All factors other than AST and ALT seem to be higher in diagnosed categories than non diabetics. However, AST and ALT shows a slight increase in undiagnosed which is interesting.

### Examine Correlations
![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_6.png)

The heatmap is a correlation between features or risk factors to investigate whether correlations are not too high - this would lead to multicollinearity.
All correlations seem to appear okay with age and BMI having highest correlation at 69%, but fortuantely not high enough for it to be discarded.


## Preprocessing and Splitting
Dataset were split using sklearn's 'train_test_split' with a test size of 20%.
Standardized and Normalized on only training set to mitigate data leakage, followed by transformation of training and testing set.

## Modeling
In the case of disease diagnoses, having higher recall than precision scores is favored, due to decrease chances of overlooking individuals with actual diseases left to be untreated. In this case, we can live with false positives.

### Logistic Regression OVR
Logistic regression OVR produced recall score for undiagnosed diabetes at 63% with most misclassifications with diagnosed cases.

![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_7.png)

### SVC Linear OVR

SVC Linear OVR produced highest recalled score for undiagnosed diabetes at 73% with most misclassifications with non-diabetic cases. 

![alt text](https://github.com/cspark2610/Classifying-Undiagnosed-Diabetes-Across-US-Populations-Using-NHANES-2011-2016/blob/master/images/img_8.png)

### Conclusion
SVC Linear resulted in highest recall score at 73%, despite having imbalanced class sets. OVR or OVA logistic regression and Linear SVC were able to handle the imbalance and produce decently high metrics. Unfortunately, I was unable to find a OVR approach using statsmodel package for interpretation; however, the results do seem appropriate given previous research. With more data and adding risk factors, it is possible to acheieve even higher recall scores, which will be very interesting, since undiagnosed cases is an overwhelming crisis in the US.
