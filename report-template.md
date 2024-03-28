Overview of the Analysis
Lending companies lend money/properties to borrowers with the expectation that the borrower will either return the asset or repay the lender. Credit Risk is associated with a borrower not returning an asset or paying a loan back causing a lender to lose money. This is measured by lenders in many ways, however in this analysis we will use Machine Learning to analyze a dataset of historical lending activity from a peer-to-peer lending services company to build a model that can identify the creditworthiness of borrowers.


Using a machine learning model, I will try to determine which loans are healthy (low-risk) or non-healthy (high-risk) based on the loan status provided by the lending company.

The Logistic Regression Algorithm is the best tool to use for our machine learning model since it is widely used to predict the probability of a target variable in classification problems.

Using the dataset provided by the lending company, I created a Logistic Regression Model that generated an accuracy score of 95%. Although the model generated a high-accuracy, the models recall value (0.91) for non-healthy loans is lower than the recall value (0.99) for healthy loans. This indicates that the model will predict loan status's as healthy better than being able to predict loan status's as non-healthy. This is due to the dataset being imbalanced, meaning that most of the data belongs to one class label (in this case healthy loans greatly outweighed non-healthy loans).

Taking a look at the code in step 3 [Split the Data into Training and Testing Sets], using the value_counts function, we are able to see that the data is highly imbalanced. The majority class is healthy loans [0] and the minority class is non-healthy loans [1]:

loan_status
0    75036
1     2500
Name: count, dtype: int64

Logistic Regression Model fitted with Imbalanced Data:

The Logistic Regression model fitted with the Imbalanced DataSet predicted healthy loans 100% of the time and predicted non-healthy loans 85% of the time.


The model fitted with imbalanced data has a higher possibility of making these mistakes:

a healthy loan (low-risk) is classified as a non-healthy loan (high-risk).
a non-healthy loan (high-risk) is classified as a healthy loan (low-risk).

According to the models recall scores, the model made 1% of mistakes when predicting healthy loans and made 9% of mistakes when predicted non-healthy loans.

Classification Report of Imbalanced DataSet
                    precision    recall  f1-score   support

  (0) Healthy Loan       1.00      0.99      1.00     18765
(1) High Risk Loan       0.85      0.91      0.88       619

          accuracy                           0.99     19384
         macro avg       0.92      0.95      0.94     19384
      weighted avg       0.99      0.99      0.99     19384


The model generated an accuracy score of 95% but could be improved due to the dataset being imbalanced.


Summary
A lending company might want a model that requires classifying healthy loans and non-healthy loans correctly most of the time:

healthy loans being identified as a non-healthy loan might be more costly for a lending company since it might cause the loss of customers.

non-healthy loans being identified as a healthy loan might also be more costly for a lending company due to the loss of funds being provided by the lender.
The lending company would most likely want fewer False Positives due to the high possibility of a lender loosing provided funds when classifying non-healthy loans as healthy. The data below is shown in the confusion matrices which indicates how many healthy/non-healthy loans the model predicted correctly/incorrectly.
According to the confusion matrix, Accuracy for both healthy and high-risk loans is 0.95, very accurate!, A high precision score is important to minimize false positives, which can lead to a loss of potential customers, a high recall score is important to minimize false negatives, which can lead to significant financial losses, This logistic regression model has high accuracy (0.99).