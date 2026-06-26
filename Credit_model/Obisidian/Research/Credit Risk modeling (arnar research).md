# Introduction :
### Credit Risk:
==Credit Risk = max{Actual Loss −Expected Loss,0} ==
Credit risk is thus the risk that the actual loss is larger than the expected loss

==Expected Loss = Probability of Default × Exposure at Default × Loss Given Default==
where: 
- *Probability of Default (PD):* expected probability that a borrower will default on the debt before its maturity, historical default record of other loans with similar characteristics, default probability of a borrower over a one year period. Often given as a rating
- *Exposure at Default (EAD):* the exact amount the borrower owes at the time of default and can easily be estimated at any time as the current exposure
- *Loss Given Default (LGD):* percentage of the actual loss of EAD, Banks protect themselves  by taking collateral or by holding credit derivatives as a securitization
### Credit Modeling:
- *credit rating models*: model PDs
- *credit pricing models*: combinations of PDs, EADs and LGDs to model the EL![[Pasted image 20260608095712.png]]

The rectangular boxes represent processes, the boxes with the sloped sides represent numerical informations.![[Pasted image 20260608101138.png]]

### Credit Assessment Models:
![[Pasted image 20260608103200.png]]

#### **Heuristic Models:**
- ***Rating Questionnaires:*** Points based. Frequently observed in the public sector. Example of questions for a public sector customer might be, sex, age, marital status and income.
- ***Qualitative Systems:*** Grade based. evaluate the applicant for each factor, final assessment would be a weighted or simple average of all grades.
- ***Expert Systems:*** software solutions which aim to recreate human problem solving abilities
- ***Fuzzy Logic Systems:*** 0-1

#### **Statistical Models :**
- ***Discriminant Analysis:*** Altman Z-Score 
$$
Z =0.12X_1+0.14X_2 +0.033X_3 +0.006X_4+0.999X_5
$$

where:
$$X1 = Working Capital / Total Assets. $$
*Measures net liquid assets in relation to the size of the company.*
$$ X2 = Retained Earnings / Total Assets. $$*Measures profitability that reflects the company’s age*
$$X3 = EBIT / Total Assets. $$*Measures operating efficiency apart from tax and leveraging factors.*
$$X4 = Market Value Equity / Book Value of Total Debt. $$*Measures how much firms market value can decline before coming insolvent.*$$X5 = Sales / Total Assets. $$*Standard measure for turnover and varies greatly from industry to indus try.*![[Pasted image 20260608121030.png]]

==The main advantage of DA, compared to other classification procedures is that the individual weights show the contribution of each explanatory variable. The result of the linear function is then also easy to interpret, as low Z-score is observed it represents a poor loan applicant.
The downside to DA is that it requires the explanatory variables to be normally distributed. Another prerequisite is that the explanatory variables are required to have the same variance for the groups to be discriminated. In practice this is however often thought to be less significant and thus often disregarded.==

- ***Logistic Regression:*** 

$$p(X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 X_1 + ... + \beta_k X_k)}}$$
- ***Classification and Regression Trees (CART)***:
- ***k-Nearest Neighbor (kNN)***:
- ***Support Vector Machine (SVM):
- ***Neural Networks***:

#### **Causal/Structural Models :**
- ***Option Pricing Models***
- ***Cash Flow Models***
- ***Fixed Income Portfolio Analysis***

#### **Hybrid Form Models**



# Data and Treatment :

## Data Dimensions:
- ***Quantitative***
- ***Qualitative***
- ***Customer factors***
- ***Other factors and figures***

Data is cleaned by removing newer and retiring companies (not observed in 2 successive years)
Then filtered by removing some of the variables with many missing values than others
Then split into 50% training set, 25% validation set, 25% test set.
To solve the rarity of default cases problem, The average performance of recursive evaluations is used.

#### Quantitative:

- Liquidity ratios measure the firm’s, availability of cash to pay debt.
- Leverage ratios measure the firm’s ability to repay long-term debt.
- Profitability ratios measure the firm’s use of its assets and control of its expenses to generate an acceptable rate of return.
- Activity ratios measure how quickly a firm converts non-cash assets to cash assets.
- Market ratios measure investor response to owning a company’s stock and also the cost of issuing stock. (not taken into consideration)

##### financial ratios:
- **liquidity**
$$liquidity = \frac{\text{Current Assets}}{\text{Current Liabilities}}$$

if liabilities = 0, liquidity = 1000

- **debt/leverage ratio**
$$\frac{\text{Debt}}{\text{EBITDA}} = \frac{\text{Net interest bearing debt}}{\text{Operating profit/loss} + \text{Depreciation/Amortization}}$$
with:
**Net interest bearing debt** = Subordinary loan capital+long term liabilities +Current liabilities to mortgagebanks+ Current bank liabilities +Current liabilities to group + Current liabilities to owner, etc. −Liquid funds−Securities − Group debt −Outstanding accounts from owner, etc.

if debt < 0, ratio = -1000
if ebitda =< 0, ratio = 1000 

- **Return On total Assets**
$$ROA = \frac{\text{Operating profit/loss}}{\frac{1}{2} ({\text{Balance Sheet}}_0+{\text{Balance Sheet}}_{-1})}$$
if only the current balance sheet is available that value is used instead of the average.
Firms that have undergone large investments will generally have lower ROA, Startups have no balance sheet thus given -100

- **Solvency/equity ratio**

$$solvency = \frac {\text{Shareholders’ equity}}{\text{Balance sheet}}$$
if b.sheet = 0, solvency = -100


##### notes:

1. this research treats startups lack of historical financial statements by "Forcing" the startups into the existing model. (solvency/roa = -100)
2. model is built on book value derived financial ratios (outdated/rigid + don't represent market value), therefore predictive power is weakend
3. sector-relative financial ratios model outperforms the simple raw, firm-specific ratios model. Therefore ratios are scaled into key figures called "Scores" noted "$\tilde{\alpha}$" from 1 to 7 (1 being bad, 7 being good). If ratio is nonsense it's given either 1 or 7 (1 indicates poor creditworthiness, 7 indicates positive creditworthiness.)
   The final final scores are already adjusted to account for sector-specific norms, it is no longer necessary to analyze the data separately by sector.![[Pasted image 20260612113848.png]]

#### Qualitative:
- Management and strategy
- Sector stability and prospects
- Market position
- Staff situation production facilities and asset assessment
- Financial risk and management
- Refunding

Qualitative ratings from 1 to 7 (1 being bad, 7 being good) handled by the customer chief responsible for the loan application
If values are missing, we use PCA (principal component analysis method)
Qualitative figures are referred to as "φ" ![[Pasted image 20260612120900.png]]

#### Customer factors:
Noted "$\gamma$"
![[Pasted image 20260612121740.png]]

#### Other factors and figures:
- **RMC**: 
![[Pasted image 20260613134848.png]]

PDs are mapped to a final score which is on the range 1- 12.
- **KOB:** 
![[Pasted image 20260613135637.png]]  ![[Pasted image 20260613135704.png]]

If score => B50, score = 20. else if score < B50, score = 10
- **Other factors:** 
	- Lowest/Highest Earlier Rating (last 12 months) 
	- Guarantor Rating (firm that adopts debt in case of default)
	- Subjective Rating (credit expert opinion if some external factors influences creditworthiness)
	- Firms Identity Number
	- Default
	- Equity

## Treatment:
#### ***General Linear Models:***
##### *Linear Regression:*
##### *Least Squares Estimation:*
##### *Hypothesis Testing:*
##### *Goodness of Fit:*
##### *Normality:*
##### *Homoscedasticity:*
##### *Linearity:*

#### ***Generalized Linear Models:***
##### *Exponential family of Distributions:*
##### *Logistic Regression:*
##### *Model Selection and Assessment:*

#### ***Discriminant Analysis:***
##### *Linear Discriminant Analysis:*
##### *Quadratic Discriminant Analysis:*
##### *Support Vector Machine:*
#### ***k-Nearest Neighbors:***
#### ***CART:***
#### ***Principal Component Analysis***
##### *Solving PCA, eigenvalue decomposition:*

# Validation :
## Relative and Cumulative frequencies:
## ROC Curves:
## Measuring Discriminatory Power:
#### *AUC:*
#### *Gini Coefficient:*
#### *Pietra Index:*
#### *Conditional Information Entropy Ratio:*
#### *Brier Score:*
$$BS = \text{Variance} + \text{Calibration} - \text{Resolution}$$

$$BS = p(1 - p) + \frac{1}{N} \sum_{c=1}^{K} N_c (\hat{p}_c - p_c)^2 - \frac{1}{N} \sum_{c=1}^{K} N_c (p - p_c)^2 $$
#### *Reliability Diagrams:*
#### *Stability Analysis:*

# Results:
### General Results:
- **Discriminatory Power:** The LR model achieved a higher Area Under the ROC Curve (AUC) and superior statistical separation scores, proving it is significantly better at distinguishing between solvent and defaulting firms.
    
- **Rating Distribution:** While the RMC heavily clustered firms in the middle rating tiers, the LR model utilized the entire 1–12 rating scale more effectively, establishing a clearer gradient between credit profiles.
    
- **Calibration Accuracy:** Reliability diagrams revealed that the RMC was systematically miscalibrated and overly pessimistic, forecasting default rates much higher than observed reality. The LR model's probability predictions tracked much closer to the optimal baseline.
    
- **Portfolio Stability:** Transition matrices demonstrated that the LR model possessed higher year-over-year rating stability (71% vs. 65%), meaning highly-rated corporate clients were far less likely to experience erratic, sudden downgrades in subsequent years.
### PCA: