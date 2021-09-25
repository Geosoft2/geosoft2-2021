- Start Date: 2021.09.25
- Author: xcomagent95
#  Cross-validation

## Introduction

A large section of statistics deals with the creation, adjustment and verification of models derived from actual observations. To evaluate a model we need to know how "accurate" phenomenon is captured by the model and how suitable the model is to extrapolate the phenomenon into the future. To indicate the goodness of fit we employ different key figures which describe how well a model fits a set of observations. The goodness of fit of a simple liniar regression can for example be expressed with the coefficient of determination (R^2).
Another procedure which can provide us with key figures for the goodness of fit for a model is the cross-validation.

## Prequesits

In order to perform a cross validation we need a datset containing the observatiosn and a model.

## Concept

The basic concept can be explained with three steps:

1. Splitting the observations into disjointed sets
2. Using some sets to train the model and unsing the remaining ones to test the model
3. Calculating a mean error over the sets 

There are diffrent methods to perform a cross validation. Some well-known ones are explained in the following section.

### Hold-Out Method

The hold-out method cross-validation is the simplest approach emntioned here (it is sometime called simple validation). The observations are simply split randomly into two  disjointed sets.
One set is used to train the model and the other to test the trained model. Typical ratios for splitting the observations are 60:40 or 80:20 
whereby the larger set should be used for training and the smaller for testing. A serious limitation of this method is that the error found can be highly dependend on the observation included in the training or testing set (selection bias). It is also not possible to use the entire datset for training or testing purposes and valuable information can be lost.

### K-Fold Method

### Leave-One-Out Method

## Advantages & Disadvantages
