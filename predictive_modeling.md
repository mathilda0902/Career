# 120 Interview Questions

## Predictive Modeling
- (Given a dataset) analyze this dataset and give a model that can predict this response variable.
  - Answer: split dataset into train-validation-test. CV to check performance of chosen model. Classification or regression problem. Visualization.
- What could be some issues if the distribution of the test data is significantly different than the distribution of the training data?
  - Answer:
    - overfitting will happen in training set, then the accuracy of test set will be low.
    - causes: sample selection bias, non-stationary environment
    - covariate shift or concept shift
    - solution: ________________________

- What are ways to make model more robust to outliers?
  - Answer:
    - regularization: L1/L2 reduce variance (to increase bias)
    - change algo: use tree-based methods in place of regression models.
    - change data: remove data or transform data (log)

- What are differences that you expect in a model that minimizes squared error vs absolute error? When is each case appropriate?
  - Answer:
    - MAE is more robust in terms of outliers, but cannot be numerically optimized. If model is easy to fit, use MAE.
    - MSE: easy to compute gradient.
    - MSE corresponds to maximizing likelihood of Gaussian random variables

- What error metric to evaluate how good a binary classifier is? What if the classes are imbalanced? What if there are more than 2 groups?
  - Answer:
    - Precision and recall.
    - logloss/deviance: Pros: error metric based on probabilities, Cons: very sensitive to false positives, negatives.
    - When there are more than 2 groups, we can have k binary classifications and add them up for logloss. Some metrics like AUC is only applicable in the binary case.

- What are various ways to predict a binary response variable? Compare two models and when appropriate to use? What's the difference between these? (SVM, logistic regression, Naive Bayes, Decision Tree, etc.)
  - Answer:
    - Logistic regression:
      - pros: features roughly linear (problem roughly linearly separable), robust to noise (regularization to avoid overfitting), output comes as probabilities, used as baseline
      - cons: cannot handle categorical features
    - SVM:
      - pros: can deal with problems that are not linearly separable, non-linear kernel
      - cons: slow to train, not efficient for large scale problems
    - Naive Bayes:
      - pros: independence assumption works well for word frequency features, so can be used in text categorization
      - cons: conditional independence of every other feature should be met
    - Tree ensembles:
      - pros: can deal with categorical features very well, non-parametric; no need to worry about outliers.
      - Gradient boosted trees work better, parameters are hard to tune.
      - RF usually performs worse than GBT
    - Deep Learning:
      - works well for image classification problems

- What is regularization and where might it be helpful? example?
  - Answer:
    - When model is overfitting to the training data, to reduce variance and increase bias, we can use regularization to reduce the complexity of model. Eg: use L1 Lasso regularization to penalize large coefficients.

- Why might it be more preferable to include fewer predictors?
  - Answer:
    - curse of dimensionality, random noises introduced, computational cost, increase tendency of overfitting

- How would you design the people you may know feature on LinkedIn or Facebook?
  - Answer:
    - Find strong unconnected people in weighted connection graph
      - Define similarity as how strong the two people are connected
      - Given a certain feature, we can calculate the similarity based on:
        - friend connections (neighbors)
        - Check-in’s people being at the same location all the time.
        - same college, workplace
        - Have randomly dropped graphs test the performance of the algorithm
    - ref. News Feed Optimization:
      - Affinity score: how close the content creator and the users are
      - Weight: weight for the edge type (comment, like, tag, etc.). Emphasis on features the company wants to promote
      - Time decay: the older the less important
