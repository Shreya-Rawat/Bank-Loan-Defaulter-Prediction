# Bank-Loan-Defaulter-Prediction
## Advanced Machine Learning Project using Ensemble Techniques

### DOMAIN: Finance and Banking

### CONTEXT:
There seems to be no end to bad loans in the country. According to the Reserve Bank of India, the overall bad loans as of March 2021 stood at INR 8.35 lakh crore, compared to INR 8.96 lakh crore in March 2020. Banks run into losses when a customer doesn't pay their loans on time. Because of this, every year, banks have losses in crores, and this also impacts the country's economic growth to a large extend.
In this project, we will look at various attributes such as funded amount, term, interest rates, loan amount, balance,etc. to predict if a customer will be a loan defaulter or not. 

### PROJECT OBJECTIVE: 
The Goal is to predict if a customer will be a loan defaulter or not based on the given input features such as funded amount, term, interest rate etc. 

### DATASET DESCRIPTION:
Data set has around 67463 instances and 35 features and includes target column as Loan Status.(1=Defaulter and 0=Non Defaulters)
Dataset Source: https://www.kaggle.com/datasets/sachinsarkar/deloitte-hackathon

### ATTRIBUTES:
( Total 35 Attributes )

- ID: unique ID of representative.
- Loan Amount: loan amount applied.
- Funded Amount: loan amount funded.
- Funded Amount Investor: loan amount approved by the investors.
- Term: term of loan (in months).
- Batch Enrolled: batch numbers to representatives.
- Interest Rate: interest rate (%) on loan.
- Grade: grade by the bank.
- Sub Grade: sub-grade by the bank.
- Employment Duration: duration.
- Home Ownership: Owner ship of home.
- Verification Status: Income verification by the bank.
- Payment Plan: if any payment plan has started against loan.
- Loan Title: loan title provided.
- Debit to Income: ratio of representative's total monthly debt repayment divided by self reported monthly income excluding mortgage.
- Delinquency - two years: number of 30+ days delinquency in past 2 years.
- Inquires- six months: total number of inquiries in last 6 months.
- Open Account: number of open credit line in representative's credit line.
- Public Record: number of derogatory public records.
- Revolving Balance: total credit revolving balance.
- Revolving Utilities: amount of credit a representative is using relative to revolving_balance.
- Total Accounts: total number of credit lines available in representatives credit line.
- Initial List Status: unique listing status of the loan - W(Waiting), F(Forwarded).
- Total Received Interest: total interest received till date.
- Total Received Late Fee: total late fee received till date.
- Recoveries: post charge off gross recovery.
- Collection Recovery Fee: post charge off collection fee.
- Collection 12 months Medical: total collections in last 12 months excluding medical collections.
- Application Type: indicates when the representative is an individual or joint.
- Last week Pay: indicates how long (in weeks) a representative has paid EMI after batch enrolled.
- Accounts Delinquent: number of accounts on which the representative is delinquent.
- Total Collection Amount: total collection amount ever owed.
- Total Current Balance: total current balance from all accounts.
- Total Revolving Credit Limit: total revolving credit limit.
- Loan Status: 1 = Defaulter, 0 = Non Defaulters.

### Steps taken in the Project:
1) Data Cleaning including missing and duplicate values check, and removing redundant columns
2) Exloratory Data Analysis including univariate and multivariate analysis
3) Label encoding the categorical data
4) Handling imbalanced data using oversampling approach SMOTE
5) Selecting K best features using Backward Feature Elimination ( Reduced no. of features from 31 to 21 )
6) MODEL BUILDING: 
  - Base model (Random Forest) using the Original Imbalanced data
  - Tuned models:
    *(We used Grid Search method for finding the optimum set of hyperparameters)
    
    - Random Forest (criterion='entropy', max_depth=5, min_samples_split=3, n_estimators=50)
    - Gradient Boosting Classifier (n_estimators = 100, learning_rate = 0.09)
    - Stacking Classifier(with estimators RandomForest and Gradient Boosting Classifier, final_estimator= LogisticRegression())
    
    
 ### CONCLUSIONS:
 
 - Base Model: 
   - Base model used imbalanced data without any hyperparameter tuning
   - It reported strong bias towards the high frequency class and therefore the accuracy scores were good even though the minority class is wrongly predicted !

- Best Performing Model = 'Gradient Boosting Classifier' with 77.6% test accuracy having:
   - Optimum Hyperparameters = (n_estimators = 100, learning_rate = 0.09, random_state=6)
   - Backward feature selection (only 21 features instead of original 35)
   - Upsampled data
