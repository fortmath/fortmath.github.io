---
layout: post
title:  "Playing with the Titanic data set"
categories: stats
tags: data-science
---

Playing with the [Titanic data set from Kaggle](https://www.kaggle.com/c/titanic/data), and trying to jot down some thoughts here along the way. SOme resources I am using as guide posts/inspirations:

* TDSS: [Titantic Data Science Solutions](https://www.kaggle.com/startupsci/titanic-data-science-solutions)
* RS: [Raman Sah's analysis](https://github.com/ramansah/kaggle-titanic/blob/master/Analysis.ipynb)
* HV: [Hal Varian's analysis](http://people.ischool.berkeley.edu/~hal/Papers/2013/ml.pdf)

---

## Generic questions

### Data cleaning
* Identifying features (potentially critical, e.g. Age) that may miss significant amount of data.
* How can we fill them in? 
  * One approach is fill in the null's, using median of other features.
     * This effectively means we have a good sense of how (distribution of) missing feature depends on the other features.

### Feature extraction
* TDSS' generic approach
  * Turns continuous quantity into categorical ones
  * Some fairly weird artificial feature construct (product of age and class?)

### Modeling/Evaluation
* TDSS' generic approach
  * Seems like random bashing. For example,
     * Logistic regression assumes that survival rate is linear wrt the features he constructed. This is unintuitive to me.
     * SVM assumes the decision boundary is linear. This is also unintuitive to me.
    What is the right way to approach this?
  * Zero cross validation :/

---

