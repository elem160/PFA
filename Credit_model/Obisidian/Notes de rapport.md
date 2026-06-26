## structural v reduced form


In contrast, standard machine learning and stochastic curve-fitting models are **purely data-driven (predictive) models**. They typically:

- Do not start with an underlying economic or behavioral theory.
- Focus entirely on maximizing predictive accuracy ($R^{2}$ or minimizing loss) rather than isolating specific parameter mechanisms.
- Easily capture complex, non-linear correlations but often struggle to identify true causal directions.

Summary Comparison

| Model Type [[1](https://www.sciencedirect.com/science/article/pii/S0039368123001425), [2](https://www.linkedin.com/pulse/inspir2es-thought-week-78-when-reduced-form-just-ok-preferable-faff--slplc), [3](http://ai2-website.s3.amazonaws.com/team/markh/J_Logic_Computation-2007-Hopkins-939-53.pdf), [4](https://www.thoughtco.com/definition-of-reduced-form-in-economics-1147125), [5](https://people.anu.edu.au/timothy.kam/work/teaching/econ4422/html/optimal-growth.html)] | Has Underlying Causal Theory? | Main Objective           | Can Handle Counterfactuals?       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- | ------------------------ | --------------------------------- |
| **Structural Models**                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Yes (Deeply rooted)           | Mechanistic Explanation  | Yes (Even if never seen before)   |
| **Econometric Reduced-Form**                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Yes (Derived from theory)     | Causal Impact Evaluation | Only within historical bounds     |
| **Pure ML / Stochastic Models**                                                                                                                                                                                                                                                                                                                                                                                                                                                    | No (Data-driven correlations) | Prediction / Forecasting | No (Fails if system rules change) |
## All my sources:
- Credit Risk Modeling - ==Arnar Ingi Einarsson== - *(Kongens Lyngby 2008 IMM-PHD-2008-1)*
- Manzo & Qiao. (2021), Deep Learning Credit Risk Modeling.  
- From Data to Financial Decision: Development and Implementation of a Credit Risk Scoring Model in the Moroccan Context - ==Imane Bouslikhane, Azzeddine Allioui== - *(ESCA Ecole de Management, Morocco)*
- Credit Rating Forecasting Using Machine Learning Techniques - ==Mark Wallis, Kuldeep Kumar and Adrian Gepp== - (_Bond University, Australia_)
- Moody's Investor service.
- Credit risk assessment with a multistage neural network ensemble learning approach - ==Lean Yu, Shouyang Wang, Kin Keung Lai ==
- ==Altman, Edward I., (1968)== - Financial ratios, discriminant analysis and the prediction of corporate bankruptcy - _(Journal of Finance; 23(4): 589-611)_
- ==Cox, David,(1972)== - Regression models and life tables, - _(Journal of the Royal Statistical Society, Series B, 34: 187-220)_
- Bank Al-Maghrib. Circulaire n° 19/G/2002
- Bank Al-Maghrib. (2007). Circular No. 26/G/2006 on the internal control system of credit institutions. Rabat: Bank Al-Maghrib. 
- Bank Al-Maghrib. (2025). Official website. Retrieved July 24, 2025, from https://www.bkam.ma
- Lakhnati, G. (2025). Cours Mesure et Gestion des Risques. ENSA Agadir
## Databases Used:
- 2029 US companies : https://www.kaggle.com/datasets/agewerc/corporate-credit-rating/data
- Mandeley : 
- NYSE and NASDAQ Companies (1999-2018) : 
- Qualitative_Bankruptcy
- Poland
- Taiwan

## IRB window for model testing
The development and implementation of the credit risk scoring model within the Moroccan banking context reveal a complex balance between methodological rigor, data limitations, and the practical demands of regulatory compliance. Notably, the use of a three year observation window, while constrained by data availability, represents a strategically justified compromise in an exploratory setting but remains below the five-year horizon recommended by Basel’s Advanced Internal Ratings-Based (IRB) approaches (BCBS, 2006). Such temporal truncation risks undermining the model’s robustness to economic cycles and its capacity to fully capture the latent dynamics of default behavior (Crook et al., 2007), thereby necessitating future extensions to enhance longitudinal stability and predictive accuracy.
## Error in a regression model:
- **Homoscedasticity** occurs when the **conditional variance** is constant (Var(Y|X) = σ²). Means the error terms are evenly spread across all values of the independent variables.
- **Heteroscedasticity** occurs when the **conditional variance** changes based on the value of X (Var(Y|X) = f(X)). Means the spread of the errors changes as the independent variables change, often creating a "cone" or "fan" shape on a graph
- **Unconditional variance** (Var(Y)) is a single, overall measure of total spread that does **not** look at X. It ignores whether the sub-groups within the data have stable or changing variances.
## Circulaire n° 19/G/2002:
Les créances sont réparties en 3 classes : 
- ***Les créances saines :*** règlement s’effectue à l’échéance, les contreparties dont la capacité à honorer leurs engagements, immédiats et/ou futurs, ne présente pas de motif d’inquiétude.
- ***Les créances en souffrance :*** risque de non recouvrement total ou partiel, détérioration de la capacité de remboursement immédiate et/ou future de la contrepartie.
	- Les créances pré douteuses: 90 jours
	- Les créances douteuses: 180 jours
	- Les créances compromises: 360 jours
- ***Les créances irrégulières :*** risque = en souffrance, contrepartie = saines
## Credit risk rating models:

| **Core Paradigm**                          | **Sub-Category**           | **Specific Models**                                                                               | **Input Data Type**                           | **Institutional Role**                                                       |
| ------------------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------- |
| **1. Judgemental & Heuristic**             | Expert Systems             | Qualitative Questionnaires, Delphi Method, Fuzzy Logic Systems                                    | Qualitative / Soft Data                       | Used for SMEs, startups, or as qualitative overlays.                         |
| **2. Classical Econometric / Statistical** | Parametric Scoring         | Logistic Regression, Probit Models, Linear Discriminant Analysis, Altman Z-Score                  | Quantitative (Financial Ratios)               | Primary baseline for regulatory compliance (Basel IRB).                      |
| **3. Machine Learning (Modern Tabular)**   | Non-Parametric & Ensembles | **XGBoost, LightGBM**, Random Forests, SVM, kNN, CART                                             | Quantitative / Mixed                          | Used for alternative risk assessment, benchmarking, and maximizing AUC/Gini. |
| **4. Structural & Market-Based**           | Contingent Claim Analysis  | Merton Option Pricing Model, Moody's KMV framework                                                | Market Data (Equity Value, Volatility) + Debt | Real-time monitoring of listed corporate entities.                           |
| **5. Dynamic Stochastic**                  | Credit Migration           | **Markov Chains (Discrete/Continuous)**, Survival Analysis (Cox Proportional Hazards)             | Historical Ratings, Macroeconomic Indicators  | Macro stress-testing, IFRS 9 Expected Credit Loss (ECL) modeling.            |
| **6. Hybrid Frameworks**                   | Combined Systems           | Integration of Machine Learning outputs with Expert Overrides, Knock-out rules, and Special Rules | All data types                                | Standard production environment in commercial banks.                         |

## Quelques repères théoriques:
• 1900: Thèse de Bachelier ”‘theorie de la speculation”’.
• 1952: Article de Markowitz ”‘ Portfolio selection”’ dans Journal of finance.
• 1964: Invention du modele CAPM par Sharp.
• 1970: Efficience des marches Eugene Fama.
• 1973: Theorie des options, Black and Scholes.
• 1977: Les modeles de taux Vasicek et de Cox, CIR.
• Depuis 80: Recherche intensif concernant la valorisation (pricing) des produits derivees et la couverture (hedging).
Nouveaux outils statistiques pour le risque de credit (selection de clientele, Scoring)
Publication de la methodologie Risk Metrics par JP Morgan, diffusion de la methode VaR.
Introduction de nouvelles mesures de risques AVaR, ES,TVaR,...

## Le développement des produits financiers:
• 1972: Foreign currency futures;
• 1973: Equity options (stock options);
• 1980: Swaps;
• 1981: Interest rate swaps;
• 1987: Path dependent options (exotiques: asiatiques, lookback);
• 1993: Captions (option sur cap) - Floortions;
• 1994: Credit default options;
• 1997: Weather derivatives....

## Réglementation prudentielle

La réglementation prudentielle a considérablement évolué ces dernières années sous l’impulsion des travaux du Comité de Bâle. Ces recommandations sont reprises par les autorités des différents pays.

- **En Europe :** Commission européenne.
    
- **Au Maroc :** Bank Al-Maghrib (BAM).
### Dates importantes

- **1988-1992 :** Accord de Bâle I (ratio de Cooke) ;
    
- **2004-2006 :** Bâle II (ratio de McDonough) ;
    
- **2013 :** Bâle III (prise en compte des aspects dynamiques : _stress tests_) ;
    
- **2022 :** FRTB (_Fundamental Review of the Trading Book_) : nouveau dispositif réglementaire pour le contrôle du risque de marché (remplacement de la VaR par l'ES et nécessité de calculs intensifs).


## Le bilan simplifié d’une banque
**1. Actif :**
- Actifs immobilisés ;
    
- Crédits et prêts ;
    
- Titres (placements, investissements, obligations, actions) ;
    
- Trésorerie (réserves détenues en compte à la banque centrale).
    
**2. Passif :**
- Fonds propres (capitaux, provisions) ; Les fonds propres sont des éléments du passif d’une banque. Ils regroupent : les actions et les certificats d’investissement, les réserves, le résultat non distribué.
  Le rôle des fonds propres :
	- Permettre la croissance de l’établissement (dépend de son capital) ;
	- Absorber les pertes et couvrir les risques (dus à des situations inattendues).

- Dette envers la banque centrale ;
    
- Dépôts ;
    
- Épargne des ménages.