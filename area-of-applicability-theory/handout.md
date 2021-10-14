Authors: [@GitLiliana](https://github.com/GitLiliana) [@Jan9669](https://github.com/Jan9669)

Issue: [#5](https://github.com/Geosoft2/geosoft2-2021/issues/5)

# Area of Applicability - Theory

This handout aims to summarise the preprint paper 'Predicting into unkown space? Estimating the area of applicability of spatial prediction models' by [Meyer and Pebesma (2020)](https://arxiv.org/abs/2005.07939) with focus on motivation and methodology.

## Motivation

Spatial mapping of environmental variables is important to reveal spatial patterns and changes of the environment. A common method in this context is the predictive modelling using machine learning algorithms as the relationships between environmental variables are complex. On the basis of field data statistical models are trained to make predictions for the entire area of interest which is quite often on a global scale. The field data normally is not evenly distributed and does not cover the entire study area. Nevertheless predictions are often made for areas which lack training data. This is especially problematic for heterogenous landscapes which might differ considerably in its properties from what has been observed in the training data. It might lead to areas for which the model does not give reliable predictions because it has no knowledge about them. This arises the following questions:
1. What is the model's area of applicability (AOA)?
2. How can the area of applicability be estimated?
 

## Methodology

### Basic Idea

1. **Calculate dissimilarity index (DI):** As differences between areas play an important role in the applicability of a model, an index which describes the dissimilarity between data points is calculated. This is the so called 'dissimilarity index'. It is based on the minimum distance to the training data within the multidimensional predictor space using weighed predictor variables.
2. **Estimating the AOA by applying threshold of the DI:** The threshold of the DI is derived from comparison between the prediction error within the AOA and the cross-validation error of the model.

### Calculating the Dissimilarity Index (DI)

1. **Standardization of predictor variables:** To ensure that all variables are treated equally they are scaled by the following formula.

   <img src="./images/scaledVar_new.png" width=50%>

2. **Weighing of variables:** To reflect the variable importance the scaled variables are multiplied with an importance estimate w<sub>j</sub> which is provided by most machine learning models.

   <img src="./images/weighedVar.png" width=12%>

3. **Distance calculation:** The distance between two points a and b in the predictor variable space is calculated using the Euclidean distance.

   <img src="./images/euclideanDist.png" width=25%>

4. **Minimum distance for a prediction point:** For a new prediction point k, the distance to the nearest training data point is determined by the following formula.

   <img src="./images/minDist.png" width=17%>

5. **Obtain dissimilarity index:** Standardize the minimum distances by dividing d<sub>k</sub> by the average of pairwise distances in the training data.

   <img src="./images/DI.png" width=11%>

### Estimating the Area of Applicability

- **Taking cross validation into account:** The AOA is defined as the area where the prediction error is comparable to the model's cross-validation error. Using cross-validation means that the training data is split into folds. This has to be taken into account for calculating the DI. When calculating the distance to the nearest training data point, it is important to only use points that are not in the same fold. This is illustrated in Figure (b) where the folds are shown in different colours. The example point belongs to fold 3 and the minimum distance of 90,28 relates to a point of fold 1 eventhough there is a point of fold 3 which is closer.

   <img src="./images/Figure_Folds_sub.png" width=30%>
   
   *(Meyer and Pebesma 2021, p. 1624)*
   
- **Simulate a response variable for testing purposes:** To choose a reasonable threshold for the DI varying thresholds were tested for nearly 1000 prediction tasks where true values were known. Based on bioclimatic predictor variables a spatially continuous response variable was simulated. This simulated response variable was then used for the prediction tasks mentioned before.
- **Compare prediction error and cross-validation error for varying quantiles of DI:** Based on the simulations the prediction error was computed by substracting predicted values from true values. Then the prediction error was compared to the cross-validation error for varying quantiles of the DI.
- **Choosing a threshold for DI:** The comparison above showed that the difference between the errors is close to zero for the .95 quantile. Hence, the .95 quantile was selected as threshold for the DI.



## Results from Case Study

Finally, the introduced approach for estimating the AOA is illustrated in a case study using a single simulation for the response variable as shown in figure 5. In addtion, 50 sample points were randomly selected as training data (figure 5b).

   <img src="./images/Figure5.png" width=80%>
   
   *(Meyer and Pebesma 2020, p. 8)*

Based on this, model performance estimations were done. The results are summarized in Figure 7 where the areas outside of the AOA are shown in pink in figure 7e. When comparing the true prediction error with the standard deviation of predictions and the DI, it becomes clear that the DI reflects the true error quite well whereas the standard deviation does not. This emphasises the suitability of the decribed method to estimate the AOA.

   <img src="./images/Figure7.png" width=80%>
   
   *(Meyer and Pebesma 2020, p. 9)*

(Notice: The paper discusses a second example.)

## Selected Discussion Questions

- What does the dissimilarity index (DI) describe? Why is it important for estimating the area of applicability (AOA)?
- How can the estimation of the AOA be helpful for future sampling campaigns?
- The presented approach for estimating the AOA is illustrated by a case study, which uses two cross-validation strategies and suggests the .95 quantile of the DI as a good threshold. Is this sufficient to verify the presented approach in general? What does this imply for future research?

## References

[Meyer, H. and Pebesma, E. (2020): Predicting into unkown space? Estimating the area of applicability of spatial prediction models. Preprint](https://arxiv.org/abs/2005.07939)

[Meyer, H. and Pebesma, E. (2021): Predicting into unkown space? Estimating the area of applicability of spatial prediction models. Methods  in Ecology and Evolution 2021; 12: 1620-1633](https://besjournals.onlinelibrary.wiley.com/doi/10.1111/2041-210X.13650)
