# Module 20 Challenge Report 

## Overview of the Analysis

Analysis was done to evaluate the performance of a model based on loan risk. I used a dataset of historical lending activity from a peer-to-peer lending company to build a model that can identify the creditworthiness of borrowers. The data set included:

* Loan size
* Interest rate
* Borrower income
* Debt-to-income
* Number of accounts
* Derogatory marks
* Total debt
* Loan status

There are 77,537 records in the dataset. 75,036 have a healthy loan status and 2,500 have a high risk of defaulting.

<img src="Images\BalanceOfTargetValues.jpg" title="Balance of Target Values">

I first split the data into training and testing datasets. Then I fit a logistic regression model by using the training data. Then I made a prediction using testing data.

The balanced accuracy score: 


<img src="Images\BalancedAccuracyOriginal.jpg" title="Balanced Accuracy">

The confusion matrix:


<img src="Images\ConfusionMatrixOriginal.jpg" title="ConfusionMatrix">

The classification report:


<img src="Images\ClassificationReportOriginal.jpg" title="ConfusionMatrix">

The accuracy was pretty high and the model did pretty well when predicting healthy loans, but not for those with a high risk of defaulting. This makes sense because the number of healthy loan status far outweighed the number of risky loans in the dataset.

Because of this inequality, I used RandomOverSampler module from the imbalanced-learn library to resample the data.

The new dataset is now balanced:


<img src="Images\BalanceOfTargetValuesResampled.jpg" title="Balance of Target Values">

The balanced accuracy score:


 <img src="Images\BalancedAccuracyResampled.jpg" title="Balanced Accuracy">

The confusion matrix:


<img src="Images\ConfusionMatrixResampled.jpg" title="ConfusionMatrix">

The classification report:


<img src="Images\ClassificationReportResampled.jpg" title="ConfusionMatrix">


## Results


* *Machine Learning Model 1:*
  
  Accuracy: 0.9520479254722232

  Precision for healthy loan: 1.00

  Recall for healthy loan: 0.99

  Precision for risky loan: 0.85

  Recall for risky loan: 0.91

<br>

* *Machine Learning Model 2:*

  Accuracy: 0.9936781215845847

  Precision for healthy loan: 1.00

  Recall for healthy loan: 0.99

  Precision for risky loan: 0.84

  Recall for risky loan: 0.99

## Summary

The Machine Learning Model 2 performed better than Model 1. Not only is the accuracy much higher, but more importantly, the recall for risky loans is much higher. In the credit risk business, it is very important to not give loans to risky individuals. Therefore, the recall for risky loans needs to be extremely high.

Model 1 has a recall for risky loans of only 0.91. That might seem high, but it's not high enough in the credit risk business. That number needs to be as close to 1 as possible. The recall for risky loans is 0.99 in Model 2.

Personally, as a risk-adverse person, I would not use either model. I would want my recall for risky loans to be 1.0.
