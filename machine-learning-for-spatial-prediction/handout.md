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

#### Simple example of supervised learning using k-nn algorithm: ![Text](/machine-learning-for-spatial-prediction/pictures/handoutbild.png)

## Most common methods


### Classification vs Regression

we only applied the algorithms on classification examples, because it easier to understand at first

  
  

### Supervised algorithms in remote sensing
-------

#### Decision Tree

* classification and regression method

###### How it works?
* split up the data into two or more disjoint and homogeneous sets

The binary tree is the simplest version of a decision tree (splits the data into exactly two sets in every step)

Example Decision Tree in Remote Sensing:

![Decision Tree example](/machine-learning-for-spatial-prediction/pictures/DecisionTree.png)
----------


#### Random Forest

The Random Forest is a supervised machine learning algorithm that is used for classification and regression. It operates by constructing multiple Decision Trees during training phase (machine learning process).

Each decision tree gives a "vote" (makes a decision).

The decision of the majority of the trees is chosen as the final decision of the random forest.

##### Use cases of Random Forest

* Remote Sensing – used in ETM (Enhanced Thematic Mapper) devices to acquire images of the earth’s surface
* Object Detection – multiclass object detection
* Kinect – used in game console camera to track body movements and recreate them in a game
* banking, stock market and e-commerce
* medicine etc.

> We focus on the remote sensing use case


##### Benefits of Random Forests

* No overfitting – use of multiple trees reduce the risk of overfitting
* Less training time
* High accuracy – runs efficiently on large databases and produces highly accurate predictions
* Estimates missing data – can maintain accuracy even a large proportion of data is missing

##### How does Random Forst work?

![Random forest example](/machine-learning-for-spatial-prediction/pictures/RandomForest.png)
---------

#### SVM - Support Vector Machine

* Classification method
* Each data item gets plotted in n-dimensional space (where n is number of features you have)
* The points are called support vectors
* The value of each feature is the value of a particular coordinate
* Find a line that splits the data between the two differently classified groups of data
    * The closest point of each group must be farthest away from the line/classifier (see below)

![Support Vector Machine example](/machine-learning-for-spatial-prediction/pictures/SupportVectorMachine.png)
---------


#### kNN (k-nearest neighbors)

* Classification and regression method
* New cases get classified by the majority vote of its k-nearest neighbors
* Distance function can be Euclidean, Manhattan, Minkowski and Hamming distance.
* kNN is computationally expensive

![kNN example](/machine-learning-for-spatial-prediction/pictures/kNN.png)