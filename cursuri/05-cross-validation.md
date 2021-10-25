---
title: "Introduction to Machine Learning"
subtitle: "Cross-validation"
author: "Traian-Florin Șerbănuță"
institute: "UNIBUC"
theme: "CambridgeUS"
urlcolor: "red"
linkstyle: "bold"
toc: false
date: \today
---


## Cross-validation aims

* Main aim: detecting and preventing overfitting
* Secondary aim: estimating parameters for the training algorithm

# Detecting and preventing overfitting

## We've been doing cross-validation all along

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test =
    train_test_split(X, y, train_size = .66)
```

### The test set method
1. Randomly choose a percentage (say 33%) of the data to be the __test set__
2. The remainder is a __training set__
3. Run learning algorithm on training set
4. Estimate future performance with the test set

## The test set method

### Method
1. Randomly choose a percentage of the data to be the __test set__
2. The remainder is a __training set__
3. Run learning algorithm on training set
4. Estimate future performance with the test set

### Pros
- Very simple (that's why we've been using it)

### Contras
- Wasteful
  - we have 33% less data to train on
- Potentially misleading
  - If our dataset is small test set might simply be "lucky"
  - _Test-set estimator of performance has high variance_

## The leave-one-out method

Assume the dataset `D` consists of `R` examples.

1. for k = 1 to R:
   1. Let $(x_k, y_k)$ be the example of index k from `D`
   2. Train on the dataset `D` with $(x_k, y_x)$ removed
   3. Test and evaluate error for $(x_k, y_k)$
2. Report mean error for all examples


### Pros
- Doesn't waste data

### Contras
- Expensive

## The k-fold method

1. Partition the dataset in `k` sets of ~equal size (called __folds__)
2. for i = 1 to k:
   1. Let $D_i$ be the ith fold
   2. Train on the dataset `D` with fold $D_i$ removed
   3. Test and evaluate error for $D_i$
3. Report mean error for all folds

### Pros
- Flexible (by varying the parameter k)
  - 2-fold: approximately the same as test-set (with 50% selection)
  - R-fold: same as leave-one-out
- Good choices for k: 3, 5, 10
  - better than test-set, less expensive than leave-one-out

### Contras
  - more expensive than test-set, less precise
   than leave-one-out

# Choosing training algorithms

## Choosing the best training algorithms

### Estimating a parameter (e.g., `max_depth` for decision trees)

1. Select a cross-validation method `cv`
2. for each value of a parameter in a range
   - consider an instance $I$ of the learning method using that parameter
   - cross-validate $I$ using method `cv`
3. Select parameter for which cross-validation yielded best result

### Choosing a learning method

1. Select a cross-validation method `cv`
2. for each learning method $I$ to be evaluated
   - cross-validate $I$ using method `cv`
3. Select method for which cross-validation yielded best result

## Resources

* Andreew Moore's tutorial pages at CMU

  [https://www.cs.cmu.edu/~./awm/tutorials/overfit.html](https://www.cs.cmu.edu/~./awm/tutorials/overfit.html)


