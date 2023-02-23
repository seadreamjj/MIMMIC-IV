# MIMMIC-IV
Assignment for machine learning
Introduction

Readmissions to hospitals place a significant burden on care resources, and on patients' health. The interval between readmission is therefore a significant indicator of the performance of healthcare. 

Task

Your task is to use the MIMIC-IV dataset to develop a model/pipeline to predict whether or not a patient is likely to be readmitted within:

1. 30 days

2. 60 days

3. 90 days

If you develop/use more than one model, report the relevant scores for all of them. 

Report which features are most useful for predicting readmission. 

Ideally upload a jupyter file with your code and documentation. DO NOT upload the data, but create a placeholder for the data in the same folder as your code. Kindly do not use blankspaces in the datafile name, and do not include any hard coded paths in your code. 

Further Instructions/Tips:

1. You can find a number of pre-processing pipelines for this dataset as code, and open sourced. If you use any of them, please mention that you are using those. However, be careful about how these pipelines select/discard features. Using these will prevent you from understanding the data well. The choice is yours. 

2. For this particular assignment, and because the dataset is complex, you can choose to ignore some parts/features of the dataset, for instance any timeseries information pertaining to instrument measurements (BP for eg). If you do so, please report that. 


Conclusion

In this project, the aim is to predict the readmission of 30, 60, 90days, I read the data from the patients, the admission, the diagnoses, and icu data. For the admission, I filter out the dead ones and the planed entry, and calculate the next admission time. For the patients, I use the race, sex, age, and reduce dimensionality. For the diagnoses, I use the chart ICD_9_10_d_v1.1 (https://github.com/AtlasCUMC/ICD10-ICD9-codes-conversion) for the transformation from icd 10 to icd9. But I also notice that the code reflection between icd9 and icd 10 may be not one to one, which means one icd10 code can refer to two or more different icd9 codes. This may lead to bias. After that, I consider the first 3 num of icd9 code, and rearrange the matrix(here thanks for https://github.com/nicolaDeCristofaro/Predictive_Models_in_Healthcare/blob/master/04_readmission.ipynb). I adopt similar steps on the icu data, merge all the data together. Then check the null value and drop the columns that I don't need.

For prediction, I tried different methods on the prediction of 30 days, including random forest, SVM, XGBoost, and logistic regression. SVM (kernel =linear) is not the appropriate one, maybe I need to use another kernel. Among random forest, XGBoost and logistic regression, XGBoost has a little better performance (if just consider accuracy). And I applied it on the prediction of 60/90 days readmission. 

Among all the features,  the most important one differs for each model. It is interesting for discussion.
