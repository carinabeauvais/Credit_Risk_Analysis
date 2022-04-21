# Credit Risk Analysis
## Overview
The objective is to analyze data on credit card usage to predict credit risk. We are oversampling and undersampling the data and using a combination approach to fit models and make predictions in order to evaluate the models.

### Results
Naive Random Oversampling: Using the RandomOverSampler to resample data so minority class data are randomly selected to add to the training set to balance both classes. Logistic regression model was used to fit the dataset for evaluation of the testing data. 

![Naive Random Oversampling](https://user-images.githubusercontent.com/96350410/164509965-86bbe73d-4bb7-4f4f-b363-387cbfea9701.png)

* The balanced accuracy score is 62.5% which is not very high.
* The precision scores were skewed toward low-risk loans which highly successful predictions, while the high-risk loans were not accurately predictated, so again, not a great model.
* The recall score shows it is slightly better at identifying low-risk loands versus high-risk loans but overall not very good scores at all.
* The F1 score for both high and low were 0.79 and 0.02 further indicating a poor model for evaluating high-risk loans.

SMOTE Oversampling: Like random sampling, the size of the minority class was increased but based on surrounding data rather than random selection. Logistic regression model was used to fit the dataset to evaluate the model. 

![SMOTE](https://user-images.githubusercontent.com/96350410/164511057-9721fa81-cb73-4abb-9954-86b4aae45c6f.png)

* Here the balanced accuracy score is 65%, so a little higher than random sampling but not much.
* The precision scores here are similar to random sampling as well where almost all low-risk loans were correctly predicted but few of the high-risk ones were correctly predicted. Still not a good model for high-risk loan evaluation.
* The recall for low-risk was 64% while high-risk was 66%, reinforcing this is not a great model.
* The F1 scores were the same as in the random sampling, and similarly we find this is not a great model.

Undersampling: Using Cluster Centroids to resample the data and reduce the majority class. Logistic regression was used to fit the data for evaluation.

![Undersampling](https://user-images.githubusercontent.com/96350410/164511963-6e301f0b-0150-42ac-a77e-343ff269ca94.png)

* Here the balanced accuracy score was around 53% which is even worse than random sampling and oversampling.
* The precision scores here are still skewed towards low-risk loans as almost all were accurately predicted but almost none of the high-risk loans were accurately predicted. This is the worst model yet for predicting high-risk loans.
* The recall scores were 61% and 45% which are not effective predictions.
* The F1 scores were 0.62 and 0.01, also indicating this model does not accurately predict high-risk loans.

Combination Sampling: Using SMOTEENN we removed the outliers and resampled the data. Logistic regression was then used to fit the data and evaluate the model.

![Combination](https://user-images.githubusercontent.com/96350410/164513243-54749148-3c79-4d87-a56b-3d6498fe6d6c.png)

* The balanced accuracy score is around 62% which is worse than the previous models tested.
* The precision scores are also skewed towards low-risk loans.
* The high-risk recall score was slightly higher here at 69% with the low-risk score being 54% which is only slightly better at identifying high-risk loans accurately.
* The F1 scores for both low and high-risk loans are 0.70 and 0.02, so again, not a great model for high-risk loans. 

Balanced Ramdon Forest Classifier: BalancedRandomForestClassifier was used with 100 estimators to classify the testing data.

![BalancedForestClassifer](https://user-images.githubusercontent.com/96350410/164514149-c674a4fd-9334-4b7d-9993-ef525c440a07.png)

* The balanced accuracy score for this model is higher at 78.7%.
* The precision for high-risk loans is 0.04 which is low compared to low-risk loans at 1.00 which indicates a high number of false positives. 
* The recall score was much higher at 91% and the high-risk loans improved to 67% so is accurately predicting true positives for low-risk loan.
* The F1 score for low-risk loans is 0.95 indicating a good model for classifying low-risk loans. High-risk loan were 0.07 so still not great for high-risk loans. 

Easy Ensemble AdaBoost Clarifier: Here we used the EasyEnsembleClassifier algorithm with 100 estimators to classify the testing data. 

![EasyEnsemble](https://user-images.githubusercontent.com/96350410/164515130-a3d1753c-4bc5-4d1f-b51f-14c15987daee.png)

* The balanced accuracy score for this model is much higher at 92.5%.
* The precision score for high-risk loans was 0.07 which is low compared to low-risk loans which were 1.00 which indicates many false positive making it unreliable for high-risk loans.
* The recall score for both low and high-risk loans were high at 94% and 91% which means the classifier is good at predicting true positives for both loan types.
* The F1 score for low-risk loans was 0.97 which is great although the high-risk loans were 0.14 which isn't great but is better than the other models.

#### Summary
Based on the above results the Easy Ensemble AdaBoost Classifer would be the best of the models fitted with the highest accuracy score. It was able to correctly classify more of both loan types then the other models. With that being said, none of these models were great at predicting high-risk loans accurately. If we were wanting a model that accurately predicted high-risk loans, none of these models would be ideal. The problem could be due to overfitting. We could more closely evaluate features that are truly correlated with the target variable to fit a model that more accurately predicts high-risk loans. 
