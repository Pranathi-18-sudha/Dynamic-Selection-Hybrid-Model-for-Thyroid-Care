Project Title: A Dynamic Selection Hybrid Model for Advancing Thyroid Care With BOOST Balancing Method

Paper link: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10546976

Dataset link: https://www.kaggle.com/datasets/emmanuelfwerr/thyroid-disease-data

the purpose of this study is to develop a Dynamic Selection Hybrid Model for improving thyroid disorder diagnosis.
and we are going to implement BOOST Balancing Method to handle the imbalanced data.

BOOST => BS(Boosting with Sample Weighting), SMOTE (Synthetic Minority Over-sampling Technique), and Tomek Links (TL)

In this projetct, we are going to define user have Hypothyroid or Hyperthyroid and their conditions (Totally 8 classifications).
	1. hyperthyroid conditions:
   	 	1) A   Subclinical (initial)
    		2) B   T3 toxic
    		3) C   toxic goitre
    		4) D   secondary toxic

    	2. hypothyroid conditions:
    		5) E   Subclinical (initial)
    		6) F   primary hypothyroid
    		7) G   compensated hypothyroid
    		8) H   secondary hypothyroid


Algorithms: Decision Tree, SVM, KNN, catboost, xgboost, Random Forest, AdaBoost, Gradient Boost, Dynamic Selection Hybrid Model, (BOOST Balancing Method)


========================================

thyroidDF.csv - 9172 observations x 31 attributes

Features:
Here is the data with serial numbers (S.No.) added:

| S.No. | Feature Name           | Description                                                 | Data Type |
|-------|------------------------|-------------------------------------------------------------|-----------|
| 1     | age                    | age of the patient                                          | int       |
| 2     | sex                    | sex patient identifies                                      | str       |
| 3     | on_thyroxine           | whether patient is on thyroxine                             | bool      |
| 5     | on_antithyroid_meds    | Whether patient is on antithyroid meds                      | bool      |
| 6     | sick                   | Whether patient is sick                                     | bool      |
| 7     | pregnant               | Whether patient is pregnant                                 | bool      |
| 8     | thyroid_surgery        | Whether patient has undergone thyroid surgery               | bool      |
| 9     | I131_treatment         | Whether patient is undergoing I131 treatment                | bool      |
| 10    | query_hypothyroid      | Whether patient believes they have hypothyroid              | bool      |
| 11    | query_hyperthyroid     | Whether patient believes they have hyperthyroid             | bool      |
| 12    | lithium                | Whether patient use lithium. This will cause goiter and hypothyroidism                               | bool      |
| 13    | goitre                 | Whether patient has goitre. It is an abnormal enlargement of the thyroid gland | bool      |
| 14    | tumor                  | Whether patient has tumor                                   | bool      |
| 15    | hypopituitary          | Whether patient has a hypopituitary gland                   | float     |
| 16    | psych                  | Whether patient has psych issues                            | bool      |
| 17    | TSH_measured           | Whether TSH was measured in the blood                       | bool      |
| 18    | TSH                    | TSH level in blood from lab work                            | float     |
| 19    | T3_measured            | Whether T3 was measured in the blood                        | bool      |
| 20    | T3                     | T3 level in blood from lab work                             | float     |
| 21    | TT4_measured           | Whether TT4 was measured in the blood                       | bool      |
| 22    | TT4                    | TT4 level in blood from lab work                            | float     |
| 23    | T4U_measured           | Whether T4U was measured in the blood                       | bool      |
| 24    | T4U                    | T4U level in blood from lab work                            | float     |
| 25    | FTI_measured           | Whether FTI was measured in the blood                       | bool      |
| 26    | FTI                    | FTI level in blood from lab work                            | float     |
| 27    | TBG_measured           | Whether TBG was measured in the blood                       | bool      |
| 28    | TBG                    | TBG level in blood from lab work                            | float     |
| 29    | referral_source        | Referral source                                             | str       |
| 30    | patient_id             | Unique ID of the patient                                    | str       |

Target:
 	* target - hyperthyroidism medical diagnosis (str)
	

===================================================

Dynamic Selection Hybrid Model (DSHM)

+---------------------------+
|     Input Dataset (D)      |
|  Features: X (e.g., T3, T4)|
|  Labels: Y (e.g., Thyroid) |
+---------------------------+
              |
              v
+---------------------------+
|   Train-Test Split         |
| X_train, X_test, Y_train,  |
| Y_test                     |
+---------------------------+
              |
              v
+----------------------------------+
| Train Conventional Classifiers   |
| (e.g., DT, SVM, KNN, RF, AB, GB) |
+----------------------------------+
              |
              v
+----------------------------------------+
| Permutation Feature Importance (PFI)   |
| Evaluate Feature Importance            |
| for Each Classifier                    |
+----------------------------------------+
              |
              v
+---------------------------------------------------+
| Select Half-Most Effective Classifiers (HEC)      |
| (e.g., RF, AB, GB based on PFI results)           |
+---------------------------------------------------+
              |
              v
+----------------------------------------+
| Train Ensemble Methods                 |
| (e.g., Boosting, Bagging, Voting,      |
| Stacking)                              |
+----------------------------------------+
              |
              v
+--------------------------------------------+
| Select Most Efficient Ensemble Method (EEM)|
| (e.g., Stacking based on accuracy results) |
+--------------------------------------------+
              |
              v
+----------------------------------------------+
|       Train Meta-Model (e.g., Logistic       |
|   Regression) Using Classifier Predictions   |
+----------------------------------------------+
              |
              v
+---------------------------+
|      Final Prediction      |
|   Classify New Samples     |
|   (e.g., Healthy/Thyroid)  |
+---------------------------+




