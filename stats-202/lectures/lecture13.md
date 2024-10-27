# Dimensionality reduction

##### Regularization methods
- Variable selection:
    - Best subset selection 
    - Forward and backward stepwise selection
- Shrinkage
   - Ridge regression 
   - The Lasso (a form of variable selection)

- Dimensionality reduction:
   - **Idea**: Define a small set of 
 predictors which summarize the information in all 
 predictors.

#### Principal Component Regression
* The loadings 
 for the first principal component define the directions of greatest variance in the space of variables.

        princomp(USArrests, cor=TRUE)$loadings[,1] # cor=TRUE makes sure to scale variables
        Murder0.535899474938155Assault0.58318363490967UrbanPop0.278190874619432Rape0.543432091445682

  Interpretation: The first principal component measures the overall rate of crime.

#### Principal Component Regression
* The scores 
 for the first principal component define the deviation of the samples along this direction.

        princomp(USArrests, cor=TRUE)$scores[,1] # cor=TRUE makes sure to scale variables
