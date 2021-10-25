---
title: "Introduction to Machine Learning"
subtitle: "Classification: Naive Bayes and Logistic Regression"
author: "Traian-Florin Șerbănuță"
institute: "UNIBUC"
theme: "CambridgeUS"
urlcolor: "red"
linkstyle: "bold"
toc: false
date: \today
---

# Bayes' Rule for Learning

## Bayes' Rule

![Bayes' Rule: Confidence increase based on new evidence](https://www.freecodecamp.org/news/content/images/size/w2000/2020/07/Screenshot-2020-07-21-at-23.44.38-1.png)


## Bayes' Rule's Importance

- Describes how to update a belief given some evidence
  - That is, it describes the act of learning

![Bayes' Equation with English Subtitles](https://www.freecodecamp.org/news/content/images/2020/07/Screenshot-2020-07-19-at-22.58.48.png)


## Bayes' Rule Explained


![Bayes' Equation with English Subtitles](https://www.freecodecamp.org/news/content/images/2020/07/Screenshot-2020-07-19-at-22.58.48.png)\ 

- Posterior probability (updated probability after the evidence is considered)
- Prior probability (the probability before the evidence is considered)
- Likelihood (probability of the evidence, given the belief is true)
- Marginal probability (probability of the evidence, under any circumstance)


## Remember Conditional Probability?

![P(win | sleep) and related conditional probabilities](https://www.freecodecamp.org/news/content/images/2020/07/Screenshot-2020-07-22-at-22.51.41.png){ height=80% }


## Using Bayes' Rule in Real Life

### Scenario

- you're working on your ML project and don't have time to waste
- your neighbor is watching local team playing soccer in the World Cup
- you hear cheering
- you would like to estimate the likelihood that your team scored.

. . .

$$P(goal | cheering) = P(goal) \cdot \frac{P(cheering | goal)}{P(cheering)}$$

## Estimating the Posterior Probability

$$P(goal | cheering) = P(goal) \cdot \frac{P(cheering | goal)}{P(cheering)}$$

1. write down the posterior probability of a goal, given cheering
2. estimate the prior probability of a goal as 2%
3. estimate the likelihood probability of cheering for a goal as 90%
   - perhaps your neighbor won't celebrate if team is losing badly
4. estimate the marginal probability of cheering – this could be because:
   - a goal has been scored (2% of the time, times 90% probability); or
   - any other reason, such as the other team missing a penalty or having a 
     player sent off (98% of the time, times perhaps 1% probability)


$$P(goal | cheering) = 0.02 \cdot \frac{0.9}{0.02 \cdot 0.9 + 0.98 \cdot 0.01} = \frac{0.018}{0.018 + 0.0098} = 64.74%$$

## Further Reading

- [J.B. Kadane. (2009). Bayesian Thought in Early Modern
Detective Stories: Monsieur Lecoq, C. Auguste Dupin and Sherlock Holmes. Statistical Science 24(2) 238--243](https://arxiv.org/pdf/1001.3253.pdf)

# Naïve Bayes Classification

## General description

- There are n features, inputs to the classifier
- There are K possible classes, outputs for the classifier
- Given a class Ck, we want to compute the probability of the true class 
  being Ck given the observed inputs __x__ = x1 ... xn

  $$ P(C_k | x_1, \ldots, x_n) $$

. . .

- By Bayes' formula:

  $$ P(C_k | {\bf x})  = \frac{P(C_k) \cdot P({\bf x} | C_k)}{P({\bf x})} \mbox{, where}$$

  - P(C_k) is the default probability of the class
    - either 1/K, or based on the training set
  - P(__x__) is the default probability of x (doesn't actually matter)

## The (naïve) independence assumption

- By Bayes' formula:

  $$ P(C_k | {\bf x})  = \frac{P(C_k) \cdot P({\bf x} | C_k)}{P({\bf x})} \mbox{, where}$$

  - P(C_k) is the default probability of the class
  - P(x) is the default probability of x (doesn't actually matter)

- Assuming input features independent and P(__x__) doesn't matter:

  $$ P(C_k | {\bf x}) \sim P(C_k) \cdot \prod_{i=1}^n{P(x_i | C_k)}$$

## Training Classification parameters

$$ P(C_k | {\bf x}) \sim P(C_k) \cdot \prod_{i=1}^n{P(x_i | C_k)}$$

### Problem
We need a way to estimate

- P(Ck) the default probability of class Ck
- P(xi | Ck) the probability of feature i to have value xi in class Ck

### Solution
- P(Ck) can be estimated as the proportion of examples in the class

- P(xi | Ck) is estimated depending on assumed distribution

  - E.g., for Gaussian Naïve Bayes (good when inputs are continuous),
    - assumes normal distribution of the features in each category
    - computes mean and variance of each input in each category
    - computes probability for a new xi based on how well it fits the curve

## Naïve Bayes Classification Algorithms

- GaussianNB implements the Gaussian Naive Bayes algorithm for classification
  - The likelihood of the features is assumed to be Gaussian.

- MultinomialNB implements the naive Bayes algorithm for multinomially distributed data
  - used for text classification (with word count vectors)

- BernoulliNB: Naive Bayes for data distributed according to Bernoulli
  - used for text classification (with word occurrence vectors)

- CategoricalNB: for discrete features that are categorically distributed


## Naïve Bayes Classification: Strengths and Weaknesses

### Strengths

- They are really fast
- Work with small training data
- They are decent as classifiers
- used for spam detection, document classification

### Weaknesses 

- Class probability is not very accurate
- If sufficient training data available, there are better methods.


# Logistic Regression


## Remember the Odds?

$$ \mbox{The odds of an event happening} = \frac{\mbox{Number of ways it can happen}}{\mbox{Number of ways it doesn't happen}} $$

### Examples

- In a coin toss there are two possible outcomes: head, or tail

  Odds head = 1:1

- Trowing a die there are 6 possible outcomes

  Odds 3 = 1:5

- Trowing two dice there are 36 possible outcomes

  Odds 4 = 3:33 = 1 : 11

- removing a marble from a bag with 3 red marbles and 2 blue

  there are 5 possible outcomes

  odds red = 3:2


## Probability, Odds, the Logit Function, Sigmoid Function

- We want to compute  p = _P( y=1 | __x__ )_
  - The chance that the given example __x__ belongs to first category
  - it's a real in the interval _[0,1]_

- Odds of y=1 | __x__  is given by formula _p / (1 - p)_
  - it's a positive real

- The Logit Function: _logit(p) = log(p / (1 - p))_ 
  - it's any real number

- The Sigmoid (Logistic) Function is the inverse of the Logit function.
  - a = log(p / 1 - p) = -log((1 - p)/p) = -log(1/p - 1)
  - log(1/p - 1) = -a, whence 1/p - 1 = exp(-a), whence 1/p = 1 + exp(-a)
  
    $$p = Logistic(a) = \frac{1}{1 + e ^ {-a}}$$

## Idea Behind Logistic Classification

- Assume the logit is a linear combination of the inputs
  - _logit(p) =  w0 + w1*x1 + … wn * xn_
- The classifier learns weights _w0, ..., wn_ from training set
- Then predicts _P(y=1 | x)_ as _Logistic(w0 + w1*x1 + … wn * xn)_

![Logistic function is a good discriminator!](https://miro.medium.com/max/485/1*Xu7B5y9gp0iL5ooBj7LtWw.png){ height=50% }

## References

- [Peter Gleeson. Bayes' Rule --- Explained for Beginners](https://www.freecodecamp.org/news/bayes-rule-explained/)

- [J00n (2020). Logistic Regression 101 — Basics. on Medium](https://medium.com/@jsy9/logistic-regression-101-2c5617429e01)