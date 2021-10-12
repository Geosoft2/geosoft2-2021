- Author: @SimonMeissner, @fab-scm

  

# Machine learning for spatial prediction

  

## Introduction

  

Today machine learning, which is a subfield of artificial intelligence (AI), is used in many different fields. Generally machine learning describes the idea for machines to learn from given data and understand its structure to predict features of new data.

Machine learning algorithms use statistical analysis to automate decision-making processes based on data inputs.

Here we will focus on use cases with remote sensing data.

  

## Principles

  

Machine learning approaches are divided into three general types, depending on the nature of the "input" provided to the learning system.

  

### Supervised learning

  

* Uses labled data to train a model (or create a function)

* The Machine knows the features of given objects and also its labels associated with the combination of the features. Its often called "training data"

  
  

### Unsupervised learning

  

* Uses unlabled data

* The Machine knows the features of given objects and searches for structure between the objects considering all features

* Can be a goal in itself by discovering hidden patterns in data

  

### Reinforcement learning

  

* Tries to make specific decisions.

* Machine is exposed to an environment where it trains itself continually using trial and error.

* Learns from the past and tries to maximise positive feedback.

  
  

## Most common methods


### Classification vs Regression

we only applied the algorithms on classification examples, because it easier to understand at first

  
  

### Supervised algorithms in remote sensing

  

#### Decision Tree

  

* classification and regression method

###### How it works?
* split up the data into two or more disjoint and homogeneous sets

The binary tree is the simplest version of a decision tree (splits the data into exactly two sets in every step)

Example Decision Tree in Remote Sensing:

![Decision Tree example](/pictures/DecisionTree.png)