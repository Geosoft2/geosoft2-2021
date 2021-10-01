- Start Date: 2021.09.25
- Author: xcomagent95
#  Cross-validation

## Introduction

A large section of statistics deals with the creation, adjustment and verification of models derived from actual observations. To evaluate a model we need to know how "accurate" phenomenon is captured by the model and how suitable the model is to extrapolate the phenomenon into the future. To indicate the goodness of fit we employ different key figures which describe how well a model fits a set of observations. The goodness of fit of a simple liniar regression can for example be expressed with the coefficient of determination (R^2).
Another procedure which can provide us with key figures for the goodness of fit for a model is the cross-validation. 

## Prequesits

In order to perform a cross validation we need a datset containing the observatiosn and a model or multiple models.

## Concept

The basic concept can be explained with three steps:

1. Splitting the observations into disjointed sets
2. Using some sets to train the model and unsing the remaining ones to test the model
3. Calculating a mean error over the testing-sets 

There are diffrent methods to perform a cross validation. Some well-known ones are explained in the following section.

### Hold-Out Method

The hold-out method cross-validation is the simplest approach emntioned here (it is sometime called simple validation). The observations are simply split randomly into two  disjointed sets.
One set is used to train the model and the other to test the trained model. Typical ratios for splitting the observations are 60:40 or 80:20 
whereby the larger set should be used for training and the smaller for testing. A serious limitation of this method is that the error found can be highly dependend on the observation included in the training or testing set (selection bias). It is also not possible to use the entire datset for training or testing purposes and valuable information can be lost.

![alt text](https://github.com/xcomagent95/geosoft2-2021/blob/main/Cross-validation/gfx/hold_out_1.jpg)

There is a special hold-out method for dealing with problems regarding machine learning. In this special case the trainig set is further divided into two disjunct sets. The training set is still used to train the model while the newly created validation set is used to tune the hyper-parameters (parameters whose values are used to control the learning process).
The testing-set is still used to derive and error for the model.

![alt text](https://github.com/xcomagent95/geosoft2-2021/blob/main/Cross-validation/gfx/hold_out_2.jpg)

### K-Fold Method

The k-fold method cross validation is am more complex approach. The observations are split into k, equally sized subsets. K can be choosen arbitrarily (but has to be >= 2). 5-fold or 10-fold cross-validations are commonly used. Each Subset is used once as the testing set and k-1 times as a training set. An error as calculated for each iteration. The overall error is the mean of these errors. This way the entire set of observations is used to train and test the model and no valuable information is lost and the selection bias is reduced significantly. The computation cost however is also higher and depends on the size of the observations-set and the choosen value for k.

![alt text](https://github.com/xcomagent95/geosoft2-2021/blob/main/Cross-validation/gfx/k_fold_1.jpg)

There are three special cases of the k-fold cross-validation. The repeated k-fold cross-validation simply reshuffles the observations-set before the next iteration. This process is repeated n times. Where the simple k-fold cross-validation provides k errors the repeated k-fold cross-validation provides n * k errors. Since differenbt splits will result in different error estimtes the repeated k-fold cross-validation results in a more precise error.

The stratified k-fold cross-validation can deal with problems which are the result of labeled data. In a labeld dataset we can provide each observation with a certain class. The classes can be of equal size or have different sizes. It can happen that the observations are spilt in a way that a vertain class is not part of a training which will result in higher errors if the class is part of the testing set. To avoid this probelm the stratified cross-validation splits the observations into the labeld classes. Each class gets then spilt according to the selected fold (5, 10, etc.). Each now provides one subset for testing and the remaining for training purposes. In doing so each class is represente in training and testing datasets and the ratio between the classes is the same for training and testing sets as well as in the source datasets containing the observations.

### Leave-One-Out Method

The leave-one-out method cross-validation can be seen as a special case of the k-fold method cross-validation. Here k is equal to the total number of observations n-1. The observations are split into a training set containing n-1 entries and a testing set consiting of only 1 entry. This method is extremely computationally expensive but a very precise error can be provided. A further variation ist the leave-p-out cross validation where not one but p entries are left out and used for testing. The leave-p-out cross validation can be employed when computation time should be minimized. 

## Advantages & Disadvantages
