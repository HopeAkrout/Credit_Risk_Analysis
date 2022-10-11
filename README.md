# Credit_Risk_Analysis

This project involves evaluating data using a number of different techniques to train and evaluate models with unbalanced classes in order to assess credit card risk.


## Overview

Using a dataset from LendingClub, the project is tasked with creating algorithms to oversample, undersample, use a combinatorial approach of over- and undersampling, use ensemble learner models that reduce bias on the dataset to predict credit risk.  In using five different methods, one can evaluate the performance of each model to recommend the best approach for credit risk prediction. 


## Results

The dataset had 68,470 rows that are assessed to be low-risk and 347 rows that are considered high-risk.  Because there is such a skew in the dataset of the two different groups, the algorithms will attempt to even out the numbers so that the data modeling has enough rows of data in each field to test and create a method of assessment.

* Oversampling

	* Naive Random Oversampling - Resampled training data so that both categories have 51,352 rows of data to test.
	
	Using RandomOverSampler from imbalanced-learn's Python add-on, the accuracy score is calculated at just under 63%:
	
	![image](https://user-images.githubusercontent.com/107294123/194967824-329f12cc-95af-4698-b212-2ddce8043195.png)
	
	![image](https://user-images.githubusercontent.com/107294123/194967844-a98002c8-53a9-480e-94f9-c0626629c468.png)


	* SMOTE Oversampling 
	Using SMOTE from imbalanced-learn's Python add-on, the accuracy score is calculated at just under 62.8%, so there is not a significant difference between the 		two oversampling methods:
	
	![image](https://user-images.githubusercontent.com/107294123/194968496-d3c9659c-5219-48ab-9406-9d587cacd536.png)
	
	![image](https://user-images.githubusercontent.com/107294123/194968518-e5d5f251-cfd5-4fae-912b-fa0b09addc04.png)
	

* Undersampling using ClusterCentroids

This method is an attempt to match the smaller data group, in this case the high-risk group.  In undersampling with ClusterCentroids the testing groups both have 260 rows for modeling.  The outcome shows a much lower accuracy rate of 51.8%:

![image](https://user-images.githubusercontent.com/107294123/194968729-bb056751-e8fb-42be-b04e-311900e74939.png)

![image](https://user-images.githubusercontent.com/107294123/194968749-c5ec928f-c1a0-451d-86ba-1f7acd796783.png)


* Combination (Over and Under) Sampling using SMOTEENN

This method created a testing group of 68,460 high risk and 62,011 low risk rows.  The results show that this method is more in line with the first two attempts at the highest accuracy rate yet at 64.1%:

![image](https://user-images.githubusercontent.com/107294123/194968970-cca9cb2b-7cb3-4f03-9e6c-8e0f2299f566.png)

![image](https://user-images.githubusercontent.com/107294123/194968995-69d04bdf-685f-4d28-8fe4-cf5346c0ddfe.png)


* Ensemble Learners 

	* Balanced Random Forest Classifier
	
	This prediction model using BalancedRandomForestClassifier from imbalanced-learn's Python add-on shows an even greater accuracy score of 78.8%.  This model 	    looks at which columns have the most weighted importance which previous algorithms don't have for analysis and was able to use that to create a more 		precise prediction as a result:
	
	![image](https://user-images.githubusercontent.com/107294123/194969185-310e3d31-d3f4-448a-af2b-5278c309d209.png)
	
	![image](https://user-images.githubusercontent.com/107294123/194969203-4aebe86e-11f4-4b3e-9c36-1db43c81068d.png)


	* Easy Ensemble AdaBoost Classifier
	
	The EasyEnsembleClassifier from imbalanced-learn's Python add-on is the most successful yet with an accuracy score of 93.1%:
	
	![image](https://user-images.githubusercontent.com/107294123/194969956-3970f6cd-dd21-4253-a22e-15362325a4c1.png)
	
	![image](https://user-images.githubusercontent.com/107294123/194969982-464209bf-367a-42df-b63e-d53c2b868e59.png)


## Summary

While some of the initial tests had a sub-standard accuracy rate and can't be considered viable for using as a model, the Ensemble AdaBoost classifier shows great promise of being a viable algorithm to use as a component of risk assessment.  As with any imperfect predictive method, anything less than 100% accuracy cannot be used as the sole assessment relied on to make determinations, but I think that it would be a good tool to use in parallel with other standardized evaluations, if for nothing else than as a starting point.  Currently, 12% of fintech loans end up in default (per https://blogs.worldbank.org/allaboutfinance/payment-fintechs-debt-enforcement-technology).  With the AdaBoost Classifier having a 6.9% error rate, there is still a chance of approving what is thought of as a low-risk loan that is actually an outlier the ends up in default, but the accuracy rate is still high enough that it may be worth using in a controlled test on applications and see if default rates go down as a result over a 12-month period.
