Moody’s provide eight main categories of credit ratings:

       1.Moody’s Long-Term Ratings

       2.Moody’s Short-Term Ratings

       3.Moody’s Bank Deposit Ratings

       4.Moody’s Bank Financial Strength Ratings

       5.Moody’s Mutual Fund Ratings

       6.Moody’s Insurance financial strength Ratings

       7.Moody’s issuer Ratings

       8.Moody’s management quality ratings for US affordable housing provider and National Scale Ratings

# Long term ratings:
Ratings are assigned to a range of fixed income instruments including bonds, debentures and preferred stocks. This system reflects:
1. How likely an issuer of debt is to meet its obligation
2. indenture protection/ level of legal protection of the security

| **Codes** | **Categories**     | **Moody’s Ratings**        |
| --------- | ------------------ | -------------------------- |
| X1        | High Grade         | Aaa, Aa1, Aa2, Aa3         |
| X2        | Investment Grade   | A1, A2, A3                 |
| X3        | Upper Medium Grade | Baa1, Baa2, Baa3           |
| X4        | Medium Grade       | Ba1, Ba2, Ba3              |
| X5        | Lower Medium Grade | B1, B2, B3                 |
| X6        | Speculative Grade  | Caa1, Caa2, Caa3, Ca and C |
# Models:
### traditional statistical techniques:
		- logistic regression
		- linear discriminant analysis
		- Bayesian networks
1. average accuracy range of only 60 to 70% using financial statements ratios and other financial statement data
2. news effect on ratings : positive sentiment in reports and negative words in news articles significant in prediction 
### non parametric approaches:
		- Decision trees
		- kNN
1. Decision trees outperform kNN on imbalanced datasets(majority of low or high credit ratings)
2. non-parametric approaches perform better than traditional statistical approaches

### Kernel classifiers and other modern machine learning techniques
		- Artificial Neural Networks
		- SVM
		- Gaussian Process Classifier
1. SVMs had most success overall 
2. SVM embodies ***structural risk minimization*** principle: optimal balance between model complexity and empirical accuracy ==> reduce overfitting risk
3. SVM struggle with sparsity, big data, ability to construct parsimonious models for financial forecasting.
4. GPC have outperformed ANNs on smaller datasets
5. GPCs were found to outperform conventional SVMs, even when enhanced by true selection and dimensionality reduction schemes
6. GPCs deal with high dimensionality by using a fast variational Bayesian Algorithm

### Ensemble techniques 
		- random forest
		- gradient boosted machines
1. models are difficult to interpret due to complexity (black box models)
2. high predictive performance / partial explanation of  relationships between credit rating output and the input predictor variables

# Data and modelling:
variables = 27 ratios, 

       1.            Operating Margin,

       2.            Pre-tax Margin,

       3.            Return on Invested Capital,

       4.            Return on Assets,

       5.            Current Ratio,

       6.            Quick Ratio,

       7.            Current Asset to Total Assets,

       8.            Operating Income to Net Sales,
       
       9.            Retained Earnings to Total Assets,
       
       10.           Accounts Receivable to Sales,
       
       11.           Inventory to Sales,
       
       12.            `Sales to Total Assets,`
       
       13.            `Net Fixed Assets to Total Assets,
       
       14.            `Long-Term Debt to Total Assets,
       
       15.            `Total Liabilities to Total Liabilities and Equity,`
       
       16.            `Number of Employees,`
       
       17.            `Disposal of Fixed Assets,`
       
       18.            `Best Sales,`
       
       19.            `Total Assets,`
       
       20.            `Inventory to Current Assets,`
       
       21.            `Total Debt to Total Equity,`
       
       22.            `Total Debt to Total Capital Expenditure,`
       
       23.            `Cash Ratio,`
       
       24.            `Cash to Total Assets,`
       
       25.            `Asset Turnover,`
       
       26.            `Equity to Total Capital, and`
       
       27.            `Equity to Total Asset.`

rows = 308 S&P companies from Bloomberg, 
period = Jan 16, Nov 17 (nearly 2 years)
### Parametric Modelling Techniques:
These models are the best possible modelling techniques if the assumptions of the underlying data are satisfied :
#### _Multinomial Logistic Regression:_
3 assumptions behind the model:
1. observations are independent of one another, 
2. outcomes follow a categorical distribution derived from the covariates via a link function
3. there is a linear relationship between the covariates and the link-function-transformed outcome
link function = logit (logarithm of odds  -  0_1), other function are possible like probit (inverse normal distribution)

#### _Linear, Quadratic and Regularized Discriminant Analysis:_
**LDA:** 
- observations are independent of one another
- data categories are normally distributed, and cov matrix is assumed to be the same for all categories
- uses Bayes Theorem to estimate category prob given each input
**QDA:**
- cov matrix isn't the same for all categories
**RDA:**
- weighed average of LDA and RDA,
- uses regularization to find balance between common cov structure (LDA) and different cov structures for each category (QDA)
- statistically powerful if data is a multivariate normal and homoscedasticity is present
### Non Parametric and machine learning models:
Because often the assumptions mentioned for parametric models do not hold true for financial data. We use these models :
#### _Artificial Neural Networks_
#### _Support Vector-Machines_
#### _Gaussian Process Classifier_
#### _Random Forest (ensemble)_
#### _Gradient Boosted Machines (ensemble)_

# results:
_Table 2. Comparison of model accuracy_

| **Method** | **Overall Ranking** | **Average Accuracy** | **Average Kappa** |
| ---------- | ------------------- | -------------------- | ----------------- |
| **RF**     | 1                   | 64.6%                | 31.3%             |
| **SVM**    | 2                   | 63.6%                | 30.6%             |
| **ANN**    | 3                   | 60.8%                | 31.5%             |
| **GBM**    | 4                   | 62.3%                | 27.4%             |
| **LDA**    | 5                   | 61.7%                | 28.8%             |
| **RDA**    | 6                   | 60.4%                | 25.3%             |
| **MLR**    | 7                   | 59.6%                | 22.6%             |
| **GPC**    | 8                   | 61.6%                | 20.6%             |