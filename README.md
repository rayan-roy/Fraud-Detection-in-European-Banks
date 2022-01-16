# Fraud-Detection-in-European-Banks
This repo contains my solution to the Kaggle Challenge of Fraud Detection in European Banks. The dataset can be found in [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud?select=creditcard.csv#). The dataset comprises of transactions made by credit cards in September 2013 by European cardholders that occured in two days. There are 492 frauds transaction out of 284,807 transactions. 

The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions. Our goal is to classify if a transaction is fraud, with 1 being Yes and 0 being No.

# EDA:
Due to security reason, several variables/predictors didn't have any name on them. As a result, we had to remove those variables. However, there were two variables time and amount we will explore the two questions:
*   Are there certain amount/threshold that are being declared as fraud?
*   Are there any trends in fraud/normal payment over time or any seasonality?
*   Are there any patterns between amount and time?

We discovered that majority of the transaction were occuring in the day. As for the amount, we see that normal payments ranged from $0-$100000 while fraud payments ranged from $0-$300. Although 300 may not be large, if there are hundreds of them, they do add up to large sum. There were no pattern found between amount and time.

# Modelling + Results:
There were 4 models used namely random Forest, XGBoost classifier, Gradient Boost (GBM) classifier, CatBoost and LightGBM. Since the data is highly imbalanced, we cannot look at the confusion matrix. Rather, we would have to look at the ROC-AUC curve scores. 
- The random forest classifier had a ROC-AUC score of 0.879945 for the training data
- The XGBoost model had a ROC-AUC score of 0.879912 for the training data
- The Gradient Boosting Classifier had a ROC-AUC score of 0.8065 for the training data
- The CatBoost had a ROC-AUC score of 0.88658 for the training data
- The LightGBM had a ROC-AUC score of 0.62443 for the training data

Based on the ROC-AUC curve score, we chose the CatBoost model. After fitting the CatBoost model, we got an ROC-AUC score of 0.872378 in the test set, which is pretty good.
