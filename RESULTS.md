# Assignment 5: Health Data Classification Results

This file contains your manual interpretations and analysis of the model results from the different parts of the assignment.

## Part 1: Logistic Regression on Imbalanced Data

### Interpretation of Results

In this section, provide your interpretation of the Logistic Regression model's performance on the imbalanced dataset. Consider:

- Which metric performed best and why?
- Which metric performed worst and why?
- How much did the class imbalance affect the results?
- What does the confusion matrix tell you about the model's predictions?

*Accuracy performed the best with a score of 0.9168. This is because the model correctly predicted the majority class most of the time given the imbalance observed in the dataset.*  

*Recall/Sensitivity performed the worst with a score of 0.3. This is because the model failed to predict true positives, the minority cases, most of the time in the imbalanced data*  

*The impact imbalance score was relatively high at 0.6161. This indicates class balance severely affected the model.*

*It shows the model does a fairly good job predicting true negative cases (majority class) but not true positive cases (minority class).*

## Part 2: Tree-Based Models with Time Series Features

### Comparison of Random Forest and XGBoost

In this section, compare the performance of the Random Forest and XGBoost models:

- Which model performed better according to AUC score?
- Why might one model outperform the other on this dataset?
- How did the addition of time-series features (rolling mean and standard deviation) affect model performance?

*The XGBoost AUC score performed better than the Random Forest (AUC: 0.9774 vs AUC: 0.9992), though both performed well*  

*XGBoost is known for sequentially building trees and correcting errors of the models iteratively instead of randomly. It also has built-in regulrization methods for better features generalization. The sythetic datset is also fairly small, slightly imbalanced, and has clinical features with nonlinear patterns that could probably more easily detected with this model*

*Since these two models achieved near perfect classification accuracy, the time-series features likely helped with predictive performance by smoothing out fluctutations and mitigating outliers*

## Part 3: Logistic Regression with Balanced Data

### Improvement Analysis

In this section, analyze the improvements gained by addressing class imbalance:

- Which metrics showed the most significant improvement?
- Which metrics showed the least improvement?
- Why might some metrics improve more than others?
- What does this tell you about the importance of addressing class imbalance?

*For some reason, SMOTE actually decreased the model accuracy and performance metrics overall, likely due to the nature of synthetic and imbalanced data, so I set the sampling strategy to be 0.5. With this modification these were the improvement scores: {accuracy: -1.26%, precision: -23.31%, recall: 143.56%, f1: 44.98%, auc: 1.04%}. The accuracy decreased by 23% (more false positiveS) and the precision decreased by a fairly large amount. This represents the model's deprovement in predicting positive cases. However, the recall significant improved by 143%, indicating the model's ability to correct detect positive cases (sensitivity), which was likely a minority class before. The SMOTE helped balance the distribution of classes, which is likely why the f1-score also increased a large amount and AUC score increased slightly in reponse to better positive and negative discrimination*

## Overall Conclusions

Summarize your key findings from all three parts of the assignment:

- What were the most important factors affecting model performance?
- Which techniques provided the most significant improvements?
- What would you recommend for future modeling of this dataset?

*Class distribution (the nature of the data) was a huge consideration prior to modeling. The SMOTE demonstrated how balancing minority classes led to a significant improvement in the f1-score. The XGBoost demonstrated to be a robust and well-rounded machine learning model for handling imbalanced and dimensional data, so I would recommend both of these for future modeling.*