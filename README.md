# Supervised Machine Learning - Credit Risk Analysis
***
## Overview of the Analysis
* Refer to credit_risk_resampling.ipynb file for for analysis performed for the project

* The purpose of this analysis is to use a provided csv dataset of historical lending data to build & evaluate a predictive model that determines the creditworthiness of potential borrowers.

* The provided csv file gave histoical lending data on borrowers.  The features of the data set included loan size, interest rate, borrower income, debt to income, number of accounts, derogatory marks & total debt.  The targert or response of the data set was termed loan status.  A 0 indicated a good/healthy loan and a 1 indicated a loan that was at high risk of default.

* Data Set Overview - The data set had a total of 77,536 records.  The number of healthy loans in the data set was 75,036 and the nubmer of high risk loans was 2500.  This can be categorized as an imbalanced data set (75036 vs 2500).

* The stages of the ML process used for this analysis began with initial import of dependencies and a read in of the csv file used for the analysis. Next data preprocessing & EDA was undertaken. In these steps the data was split into features (X) and response (y), examined for balance and split into a training set and testing set using the train test split methodology in scikit-learn.  Following this, ML was performed on the data as presented using a model-->fit-->predict workflow.  The model utilized for this was a Logistic Regression model that was fitted to the training data and then predictions were made on the test data for outcome.  Noting earlier that the data was imbalanced, the ML process was subsequently repeated but the intial data was resampled using the random over sampler function in scikit-learn. This allowed the model-->fit-->predict process to be run on a balanced representative data set. 
## Results

Machine Learning Models were evaluated via balanced accuracy scores and the precision & recall scores of the models.

* Machine Learning Model 1:
  *  Model 1 had a balanced accuracy score of 0.95 or 95%. The use of the balanced accuracy score is useful for imbalanced data sets (as is the case here) as it avoids inflated performance estimates.  Thus, we can conclude that overall Model1 was 95% "correct" in its predictoins of true positives and true negatives.

  * Model 1 had a precision score of 1.0 for predicting healthy loans and a precision score of 0.85 for high risk loans. Prediction is a measure of how well the "positives" class is predicted. A model with no false positives has perfect precision.So we can say that all positives were predicted 100% correctly for the good loans and 85% correct for the high risk loans. 

  * Finally recall is a critical metric in unbalanced data sets as it gives the ability to optimize the model.  Recall, sometimes termed sensitivity, is the ratio of truely correct positive samples. If a model has perfect recall it would have no false negatives. Model1 was able to achieve 99% recall on the healthy loans and 91% on the high risk loans.


* Machine Learning Model 2:
  *  Model 2 (Random Over Sample) maintained a very similar precision of 84% as compared to model1's 85% precision.  The benefits of random over sampling to account for the data imblance previously mentioned can be noted in Model2's accuracy and recall scores.  Accuracy for model2 increased to 99% from 95% and recall increased to 99% for high risk loans from 91%.

## Summary

* The logistic regression model fit with over-sampled data predicts both the healthy loan (0) and the high risk loan (1) very well. The healthy loan sees precision recall and f1 scores of 1.0, 0.99 & 1.0 respectively. This is similar to the original data but we saw imporvements in the spec score (up to 0.99 from 0.91) the geo score (up to 0.99 from 0.95) and the iba score (up from 0.91 to 0.99) for healthy loans.  For the high risk loans we saw even better improvements.  Precision remained roughly the same (0.85 original vs 0.84 over sample) while all other scores increased for the over sampled data for high risk loans.  This leads me to conclude that the over sampling not only predicted BOTH loan type very well, but it also did a better job of prediction as compared to the original logistic regression model. The random over sampled logistic regression model would be the recommended model to use between the two.
* Performance seems to have some dependence on wether we are predicting 0 vs 1 with the original data set.  Once we account for imbalance by random over sampling, the model predicts both 0 and 1 very well.  Again, the recommendation is for model2.


