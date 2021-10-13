# Heart_Failure_Analysis
Implementation of feature selection and exploring dimensionality reduction in predicting survival of patients with heart failure
# Background

Heart failure is a pathological condition in which the heart muscles are so weak that they cannot pump enough blood for body's needs. 
Under heart failure, the heart does not stop pumping so it does not necessarilty leads to patient's death. When a patient with heart failure
gets admitted in the hospital, several tests are performed to monitor critical parameters that are critical for determining heart's functioning 
capacity. However, as indicated in the research paper by Davide Chicco et al through machine learning methods that not all of these parameters contribute to
heart failure. It may not be necessary to conduct all these tests thus, saving resources and expediting the release of appropriate treatment plan
for the affected patients. 

# Dataset
UCI dataset (https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records) containing the medical records of 299 heart failure patients collected at the Faisalabad Institute of Cardiology and at the Allied Hospital in Faisalabad (Punjab, Pakistan), during April–December 2015 is analyzed.The patients consisted of 105 women and 194 men, and their ages range between 40 and 95 years old. The dataset contains 13 features, which report clinical, body, and lifestyle information described. Some features are binary: anaemia, high, blood pressure, diabetes, sex, and smoking. The death event feature is used as the target and states that if the patient died or survived. The dataset is imbalanced where the survived patients (death event = 0) are 203 i.e. 67.89%, while the dead patients (death event = 1) are 96 i.e. 32.11 %. 

# Methods
Before begining the analysis, the dataset is normalized. The feature 'time' corresponding to patient's stay in hospital is dropped from this analysis. Pearson correlation coefficients are then computed for each of the remaining input features. There is no strong correlation found among the features. The data is split into train/test with 80-20 split. Supervised Binary classifier models are implemented on the normalized features using linear/non-linear machine learning classification algorithms such as Logistic Regression, Linear SVM,KNN, MLP, etc. For each classifier model, corresponding hyperparmeter tuning is done. Feature selection is implemented prior to classifying by ranking the feature importances using Random Forest Classifiers. The objective is to determine the critical features among the given features that would effectively describe the data. Dimensionality reduction using Principal Component Analysis is also explored.

# Metrics
For each classifier their performance is compared through metrics such as recall, precision, F1-score, MCC (Mathew Correlation Coefficient), ROC_AUC, sensitivity, and specificity.

# Results
1. Data pre-processing and visualization: No strong correlation found among the given features. 

![image](https://user-images.githubusercontent.com/28870788/137041511-fee215c6-1f14-4088-b334-9df1702a2927.png)

![image](https://user-images.githubusercontent.com/28870788/137041364-d64878b1-9e24-49f3-a132-7e2e332a17f5.png)

2. Imbalanced dataset: Percentage of positive values in training dataset target= 31.38; Percentage of positive values in test dataset target= 35.0

3. Feature selection using Random Forest Classifier: Top 3 features ranked are serum_creatinine (7), age (0), and ejection_fraction (4). Thus, in order to determine whether there will be heart failure or not in a patient, these are the three most important features of the patient which need to be considered.

![image](https://user-images.githubusercontent.com/28870788/137041293-1ab7aad8-2098-43bd-9c9f-2507acf63415.png)

4. Supervised Binary Classifiers (Target: DEATH_EVENT, 0=> Negative, 1=> Positive): 

![image](https://user-images.githubusercontent.com/28870788/137040935-c4ecd4b5-6885-4b6a-b4a4-40d44305bae6.png)

5. Dimensionality Reduction using PCA: Variance plot:  PCA output indicates 7 components needed to capture 95% of variance in the input data. Going from 11 to 7 is not a significant reduction in dimension.

![image](https://user-images.githubusercontent.com/28870788/137041120-0cb7d67b-b859-4262-9f6c-fed105f98588.png)

# Conclusions
1. Serum_creatinine, Age, and Ejection fraction are the key indicators of whether the patient will suffer a death due to heart failure.
2. Supervised binary linear/non-linear classifier models built and their performance reported for the chosen metrics.
3. Dimensionality reduction explored using PCA with no useful outcome. 

# Reference
- Heart failure clinical records Data Set: https://archive.ics.uci.edu/ml/datasets/Heart+failure+clinical+records
- Davide Chicco, Giuseppe Jurman: "Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone". BMC Medical Informatics and Decision Making 20, 16 (2020). [https://doi.org/10.1186/s12911-020-1023-5]



