---
title: "Introduction to Machine Learning"
author: "Traian-Florin Șerbănuță"
institute: "UNIBUC"
theme: "CambridgeUS"
urlcolor: "red"
linkstyle: "bold"
date: "February 16, 2021"
toc: "false"
---


### This week's objectives

- To better know each-other

- To give you an idea about what is to come

- To discuss how you will be evaluated

- To briefly introduce (some) Machine Learning (concepts)


# To better know each-other

### Short Self-Presentation

#### Name

Traian Florin Șerbănuță

#### Job

Associate Professor of Computer Science @ UNIBUC

#### Interests

Programming Languages, Logical Systems, Program Verification, Proof-Assistants

#### Prior Experience with Machine Learning / AI

Used to worked for a start-up developing intelligent agents


# Course Syllabus


### Overall course objectives

#### To be able to ...


- ... understand basic machine learning terminology
- ... research other methods in addition to the ones presented in the class
- ... identify an appropriate machine learning technique for a particular problem in one’s own area of interest
- ... train and evaluate a model
- ... document the process of selecting a model, training it, and evaluating it, as well as to reflect on the obtained results.


## Course Contents and Organization

### Course Contents

- Introduction to machine learning
  + what is it good for?
  + classes, methods, algorithms
- Predictive modeling cycle
- Pitfalls and solutions: over-fitting and regularization
- Supervised learning
  + Classification (predicting a category)
  + Regression (predicting a quantity)
  + Model- vs instance- based learning
  + Decision Trees
- unsupervised learning
  + dimensionality reduction
  + clustering
- Neural Networks

### Structure of a Weekly Lecture

- A new machine learning method / concept is introduced
  + discussion about its applicability
- Hands-on tutorial exhibiting the method
  + ask any questions about how it's done
- Students experiment with applying the method 
  + ask for assistance if stuck
- Homework – apply the method without assistance at home
  + feedback next week

### Resources

#### Tutorial / Lab / Homeworks

- Jupyter Notebooks on [kaggle.com](http://kaggle.com)

- Create your account today! (if you don't already have one)

#### If you want to learn at your own pace

- https://www.kaggle.com/learn

- Artificial Intelligence: A Modern Approach
  + by Stuart Russell and Peter Norvig
  + [aima.cs.berkeley.edu](http://aima.cs.berkeley.edu/)

## Course Completion

### Final grade

Homeworks (4p) + Project (5p) + 1p = 10p

### Homeworks (4p)

#### Complete each week's homework!

- Homework is posted after each class lecture (same day)
- Homework must be submitted before next class lecture (link to the notebook)
- No late submission policy
  + no points given for homeworks not submitted on time
  + it's better to submit partial solution than to be late

### Project (5p)

#### Three avenues to success
- Standard Approach
- Competitive Approach
- Academic Approach

#### Deadlines

- Choosing a project: end of March
- Submitting a project: end of semester
  - except for the "academic" ones which must be delivered earlier

### Standard Approach

- Develop two prediction models based for your own data
- Train and evaluate the models
- Present the problem and document the process
- Reflect on the results
- All of it in a Notebook on Kaggle

### Competitive Approach

- Compete in a Kaggle competition
  + [www.kaggle.com/competitions](https://www.kaggle.com/competitions)
- Same requirements as for the Standard Approach, but for a pre-fixed problem

### Academic Approach

- Prepare and deliver one class lecture on a topic you're familiar with

- Must follow the Structure of a Weekly Lecture
  + prepare lecture, tutorial, class exercises, and homework
  + Materials must be submitted for feedback one day before the scheduled delivery

# Machine Learning at a Glance

### Why / when do we need machine learning?

- Large volumes of data
  + sensorial input when driving a car
  + reviews on movies / products
  + activity logs on a server
- Limited capacity to manually analyze data


## What is Machine Learning?

### Machine Learning Definition

- A type of Artificial Intelligence
- Automatically "train" models (_learn_) based on prior experience (_data_)
  + choose a type of model
  + identify patterns in given data
  + learn = tune model's parameters
- Use (_learned_) model to analyze new experiences
  + run the model on new data
  + recognize "learned" patterns

### Machine Learning Process

![Machine Learning Process](https://www.simplilearn.com/ice9/article_detailed_content_img/machine-learning-process.jpeg){ width=75% }

### Machine Learning Categories

- Supervised Learning
- Unsupervised Learning
- Reinforcement Learning

### Supervised/Unsupervised Learning

![Supervised/Unsupervised Learning](https://www.researchgate.net/publication/329533120/figure/fig1/AS:702267594399761@1544445050584/Supervised-learning-and-unsupervised-learning-Supervised-learning-uses-annotation.png){ height=90% }

### Supervised Learning

- Input data describes a relation mapping input to output
- Model attempts to learn this relation (concept learning)
- Examples: Sentiment Analysis, Spam Detection, Disease Prediction

### Unsupervised Learning

- Input data is unlabelled: contains inputs but no outputs
- Model attempts to identify patterns
  - cluster data in similar groups
  - Anomaly detection (find outliers)
  - determine features relevant to distinguishing clusters (principal components)
- Examples: Intrusion detection, Exploratory analysis, Knowledge discovery, Resolving lexical ambiguity, Pre-processing data to apply other ML methods

### Reinforcement Learning

- Input: way to measure the success of performing an __action__ from a given __state__
  + make a move in a game
  + move a robot in an environment
- Model attempts to learn how to behave (what action to take) in any given state
  + Parameters of the model (probability to select an action) are adjusted based on the success/failure of previous attempts
  + Model should be improving through experience
- Goal: learning a sequence of actions leading to a long-term reward

## Error Analysis

### Precision / Recall

![Precision/Recall](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Precisionrecall.svg/800px-Precisionrecall.svg.png){ height=95% }

### Under-fitting / Over-fitting 

- Under-fitting: model is to simple to be able to learn actual relation
- Over-fitting: too much learning (also learns the noise)

![Under-Fitting/Over-fitting](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20190523171258/overfitting_2.png)


## Why not deep learning for everything

### Why not deep learning for everything

Deep Learning is very cool and with tremendous potential impact

#### However

- Doesn't work so well with small data
  + for best results (hundreds of thousands, millions of labeled data samples)

- Building customized solutions is hard and expensive

- Black box
  + We don't have a good understanding of the models


### Images on the slides


- Machine Learning Process
  + [https://www.simplilearn.com/tutorials/machine-learning-tutorial/what-is-machine-learning](https://www.simplilearn.com/tutorials/machine-learning-tutorial/what-is-machine-learning)

- Supervised/Unsupervised Learning
  + [https://www.researchgate.net/figure/Supervised-learning-and-unsupervised-learning-Supervised-learning-uses-annotation_fig1_329533120](https://www.researchgate.net/figure/Supervised-learning-and-unsupervised-learning-Supervised-learning-uses-annotation_fig1_329533120)

- Precision/Recall
  + [https://en.wikipedia.org/wiki/Precision_and_recall](https://en.wikipedia.org/wiki/Precision_and_recall)

- Under-Fitting/Over-Fitting
  + [https://www.geeksforgeeks.org/underfitting-and-overfitting-in-machine-learning/](https://www.geeksforgeeks.org/underfitting-and-overfitting-in-machine-learning/)