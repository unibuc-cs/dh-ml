---
title: "Introduction to Machine Learning"
subtitle: "Ensemble Learning"
author: "Traian-Florin Șerbănuță"
institute: "UNIBUC"
theme: "CambridgeUS"
urlcolor: "red"
linkstyle: "bold"
date: "March 9, 2021"
---

# Introduction

## Ensemble Learning

### Basic Idea

- Select multiple hypotheses from the hypothesis space (an __ensemble__)
  - e.g., train 100 different decision trees from same training set
- Combine their predictions
  - e.g., choose the class predicted by a majority in the ensemble

### Why it works?

- Assuming the _independence_ of errors made by each hypothesis
- If so, then the probability of numerous simultaneous errors is low

## Types of Ensemble Learning

- Boosting
  - iteratively improve a classifier
  - by giving more weight to misclassified examples
- Aggregating (Voting)
  - create an aggregate prediction
  - by combining multiple predictions (average, majority)
- Bootstrap AGGregatING  (Bagging)
  - train multiple instances of same classifier on samples of the training set
  - aggregate their predictions
- Stacking
  - Train a classifier to aggregate results of multiple classifiers

## Boosting ([AdaBoostClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier.html))

1. Assign to every training example the same weight
2. Train a "weak" model on weighted examples
3. For each example
   - if predicted incorrectly, increase its weight
   - if predicted correctly, decrease its weight
4. Train a new weak model on newly weighted examples
5. Repeat 3 and 4 a given number of times
   - or until a certain fitness criterion is met

### Weighted examples
- Higher weight - higher importance given by training algorithm
- E.g., increase number of times it appears in training set

## Aggregating ([VotingClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier.html#sklearn.ensemble.VotingClassifier))

### Training phase
- Train multiple classifiers
  - usually on the same training data

### Predicting phase
- Get a prediction from each trained classifier
- Aggregate the predictions
  - Hard Voting (used for predicting categorical data)

    Choose the category by majority-rule voting
  - Soft Voting
    
    Aggregated prediction is obtained by averaging individual ones

## Bootstrap Aggregating ([BaggingClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingClassifier.html))

![Bootstrap Aggregating](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c8/Ensemble_Bagging.svg/500px-Ensemble_Bagging.svg.png){ height=50% }\ 

### Training Phase (using a base classifier)
- Train multiple instances of the base classifier
- on __samples__ (with replacement) of the training data

### Predicting phase
- Same as for Aggregating w.r.t. trained classifiers

## Random Forest ([RandomForestClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html))

![Random Forest](https://upload.wikimedia.org/wikipedia/commons/7/76/Random_forest_diagram_complete.png){ height=50% }\ 

Same as Bootstrap Aggregating, but

- the base algorithm is DecisionTree
- additionally uses _attribute bagging_
  - samples (with replacement) features to be used for training each individual classifier


