# This folder includes the original codes used to query MIMIC-III database, data cleaning and explorations, creating datasets, and final model training and validation.
# This project does not provide access to MIMIC-III database and the ipython files don't reveal raw data of the database.

Material and Methods
This retrospective study explores the efficacy of recurrent neural network in predicting mortality among patients in intensive care units (ICU) using commonly measured vital signs and physiological signals from electronic health records. Subsampling technique is used to tackle the imbalanced dataset. Multiple neural network algorithms are built and validated on a hold-out dataset with AUC and c-statistics.
1. Database
MIMIC-III is a large, single-center database of de-identified information pertaining to patients admitted to an intensive care unit at Beth Israel Deaconess Hospital from 2001 to 2012. It includes more than 40,000 patients’ data including vital signs, medications, laboratory measurements, notes charted by care providers, procedure codes, diagnostic codes, imaging reports, hospital length of stay, survival data, and more[22].
2. Cohort Selection
This study utilized the data of ICU admissions from MetaVision system, a subset of MIMIC-III database which stores data for patients admitted between 2008-2012. It is reasonable to use data collected in a span of five years since clinical practice evolves over time. In order to collect certain amount of observations for modeling, ICU stay shorter than 24 hours are excluded for analysis. Newborn admissions were also excluded since neonates have distinct physiological and pathological mechanism comparing to adults. There could be more than one admission in hospital admission per patient. In MIMIC-III database, ICU readmission within 24 hours of discharge is considered as one ICU admission. The data was split into training set (60%), validation set (20%), and test set (20%). Test set is used as a hold-out set only for validating the performance of models.
3. Features Selection
Ten physiological measurements are selected for modeling such as vital signs (e.g. heart rate (HR), systolic blood pressure (SBP), diastolic blood pressure (DBP), mean blood pressure
(mBP), respiratory rate (RR), body temperature (BT)), oxygen saturation (SpO2), use of machine ventilator, use of oxygenation therapy, and serum glucose (Glu), which are routinely measured or commonly recorded during ICU admission. Only data collected within first 24 hours after ICU admission is extracted for modeling. Data is then partitioned into one-hour interval and the first value of each parameters are extracted for each interval. Missing values are first filled by previous value and then filled with mean.
4. Primary Outcome
The primary outcome of this study is ICU mortality. Since MIMIC database only provides the data of mortality, mortality happened on the same day of ICU discharge is considered death during ICU admission.
5. Model Derivation and Validation
Resampling technique is used to tackle the imbalanced dataset (mortality take up 8.2% of the cohort). The mortality group is oversampled to a ratio of 1:1 against the survival group. Early stopping technique is used to prevent model overfitting. Logistic regression, feed forward neural network, recurrent neural networks (LSTM and GRU) are tested upon the datasets and are validated on hold-out dataset with AUC and c-statistics.

# 
