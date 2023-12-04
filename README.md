# Long-term Mortality Prediction

**More info in the .ipynb notebook!**
- data processing
- data visualization
- modeling


## Introduction
Continuity of care, or quality of care over time, is important for patients, doctors, and hospitals. Research has shown that most patients being interviewed reported that they felt it was important to see or hear back from the same doctor regularly. According to survey data at the National Institutes of Health’s National Library of Medicine, many patients commented that continuity helps build up trust and confidence in the doctor, and they were likely to be provided with more consistent advice. From a physician’s viewpoint, knowing a patient’s long-term health data also helps them to give better suggestions. This increases efficiency because the doctor knows the patient’s history and can integrate new decisions efficiently without extensive investigation or record review from a whole-person perspective. If knowing what a patient’s health will look like 1 year from the current time at the population level, physicians could be alerted to the risk of the patient dying 1 year in the future and thereby recommend a specialized course of action for each patient. Other research also shows continuity of care may reduce healthcare costs because it facilitates the physician by making early recognition of problems possible. Therefore, there is a need to learn more about this long-term relationship between the patient and the physician that can potentially improve the quality of care for the entire population.

Predicting mortality in patients is a crucial step in long-term clinical healthcare research. Machine learning models help to quantify patient health, predict future outcomes, facilitate doctors with an assessment of the severity of illness, and determine the value of novel treatments. To predict whether a patient will die within a year of their admission, we used MIMIC-III (‘Medical Information Mart for Intensive Care’), a large, deidentified clinical database comprising information relating to patients who stayed within the ICU (intensive care units) at Beth Israel Deaconess Medical Center between 2001 and 2012. MIMIC-III is very exhaustive and includes information about 53423 distinct hospital admissions such as demographics, vital signs, medications, laboratory measurements, diagnostic codes, survival data, and more.

Past research has been done extensively in this field. In our research, we identified the SAPS II score which was used to measure the severity of disease for patients. The score was calculated with the below parameters: Age, Heart Rate, Systolic Blood Pressure, Temperature, Glasgow Coma Scale, Mechanical Ventilation or CPAP, PaO2, FiO2, Urine Output, Blood Urea Nitrogen, Sodium, Potassium, Bicarbonate, Bilirubin, White Blood Cell, Chronic diseases, Type of admission. We believe that the above parameters are highly relevant features to our goal. In addition, we wanted to explore other possible features that may be critical to determining a patient's mortality in a year. Thus, in this project, we created two data sets. One of the data sets consists of 17 raw features mentioned above. 17 raw features were found in table CHARTEVENT, ADMISSION, LABEVENT, and OUTPUT. The other data set consists of 17 raw features, in addition to all features that we found in INPUT, LABEVENT, and CHARTEVENT with low missing rates. We wanted to use the first data set as our benchmark and compare the performance between the two data sets.

## Datasets & models
dataset1- benchmark
dataset2- our selected features (much more than dataset1)
We compared 5 models on 2 datasets: Logistic Regression, Decision Tree, XGBoost,KNN,CNN

## Methods
- We perform propressing by imputer missing data and normalize data
- We split 2 datasets into features and lables for test(0.2) and train(0.8)
- We plot ROC curves for default models on datasets to roughly estimate the performance (result may change after parameter turing)
- We perform hyperparameter selection by grid search and cross validation
- We fit model and predict test result based on tured models


## Result

We compare model performance for two datasets and choose the best model-- XGBoost

-XBGoost is much better than other models(it is suitable for sparse hign dimension data)
-KNN performs better on dataset1(with less features) than set2(150 features)
-CNN achieves good performance but not outstanding(maybe not enough data or enough tuning). On the other hand, we think our data is not a sequential signal so may not achieve the best performance on 1D CNN.
-Tured decision tree is much better than the origin one(reduce bias) -Logistic regression is on the average performance.

Look into testing results for XGBoost on dataset2 for feature importance, we find the results on two datasets are not far away from each other. We believe it is because the data is sparse, so even when adding more data, it cannot reduce variance largely. On the other hand, the 17 features in dataset1 are more dense. So it can perform well even if it has few features. Moreover, since the features in the first dataset are commonly used in history, it means they are important features generally.
