# Causal-Inference-Model-for-Bank-Client-Subscription
The primary goal is to assess the impact of marketing campaigns on the likelihood of bank clients subscribing to a term deposit by leveraging Causal Inference Techniques

# Objective

The objective of this project is to investigate the impact of two key marketing campaign variables, 'pdays' and 'campaign engagement level', on a client's decision to subscribe to a term deposit. The study employs causal inference methodologies to ascertain whether the frequency of contact (classified as 'low' and 'high' engagement) and the time since the last contact (segmented into 'low' and 'high' 'pdays') significantly sway the subscription outcome. Through this dual analysis, the project aims to pinpoint the most effective strategies for increasing term deposit subscriptions

# Data Source and Description

The [dataset](https://www.kaggle.com/code/janiobachmann/bank-marketing-campaign-opening-a-term-deposit/notebook) hails from a banking institution and encapsulates various client attributes, contact methods from the latest marketing campaign, and other key details. It includes diverse variables from demographic information like age and job type to engagement metrics such as the outcome of previous marketing contacts.

# Modelling Methodology

The modeling methodology began with data preprocessing, where irrelevant features were dropped, categorical variables were transformed into dummy variables, and the 'pdays' feature was binned to categorize the recency of client contact.

Two distinct causal inference techniques were employed: the UpliftRandomForestClassifier and UpliftTreeClassifier. The former aimed to measure the overall importance of features and the latter to visualize decision-making pathways and calculate uplift scores. Both models treated 'campaign' as the intervention variable to assess its impact on the 'deposit' outcome, which was dichotomized to represent subscription status.

Further, the S-learner and T-learner models, which utilized XGBClassifier and LGBMClassifier, estimated the Average Treatment Effect (ATE) and Individual Treatment Effect (ITE). These models provided insights into how the treatment—classified into 'low' and 'high' levels of campaign engagement—affected the likelihood of a client subscribing to a term deposit. The S-learner integrated treatment as a feature within a single model, while the T-learner estimated effects separately for control and treatment conditions and computed the difference to arrive at ITE.

Feature importance was gauged using both automatic and permutation methods to identify key predictors, and SHAP values were calculated to interpret the models' outputs and understand the influence of each feature

In a further iteration, 'pdays' was used as a treatment variable in place of 'campaign' to investigate its influence on the target variable. This additional model served to cross-validate the effects observed and to ensure a comprehensive analysis of the factors at play

# Results and Insights

**Results and Insights for 'Campaign' as Treatment Variable**

The analysis of 'Campaign' as a treatment variable revealed nuanced insights into the marketing campaign's effectiveness. Utilizing causal inference models, it was observed that the classification of campaign contacts into 'low' and 'high' engagement levels did not straightforwardly translate to increased likelihood of term deposit subscriptions. The Average Treatment Effect (ATE) values, derived from both S-learner and T-learner models, indicated a slight negative impact on subscription likelihood, suggesting that higher levels of engagement could potentially deter clients. 

The Individual Treatment Effect (ITE) distributions further underscored the heterogeneity in treatment effects across the client base. While some clients responded positively to increased contact, as evidenced by positive ITE values, a significant portion exhibited negative ITEs, indicating a decreased likelihood of subscription with higher campaign engagement. This variability suggests that client receptiveness to marketing campaigns is influenced by a myriad of factors beyond mere contact frequency


**Results and Insights for 'Pdays' as Treatment Variable**

Analyzing 'pdays' as a treatment variable offered a different perspective on the impact of temporal factors on marketing effectiveness. The division of 'pdays' into 'low' and 'high' categories aimed to assess how the recency of the last contact influences a client's decision to subscribe to a term deposit. The results from causal inference models presented a generally negative ATE, suggesting that a longer interval since the last contact does not necessarily improve the chances of subscription. This finding challenges the assumption that allowing more time between contacts would lead to a higher subscription rate by giving potential clients space to consider the offer




