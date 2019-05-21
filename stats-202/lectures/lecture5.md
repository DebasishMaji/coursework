# Linear Regression

   Model
    
    yi = β0 + β1xi + εi
   
    εi ∼ N (0, σ)
   
   The estimates βˆ0 and βˆ1 are chosen to minimize the residual sum of squares (RSS): 
        
        RSS = summation over i belongs to (1, n) (yi − yˆi)**2
        
            = summation over i belongs to (1, n) (yi − β0 − β1xi)**2
        
   #### Estimates βˆ0 and βˆ1
   
   A little calculus shows that the minimizers of the RSS are:
   
        βˆ1 = (summation over i belongs to (1, n) (xi − x')(yi − y)) / (summation over i belongs (1, n) (xi − x)**2)
        
        βˆ0 = y − βˆ

  #### Assesing the accuracy of βˆ0 and βˆ1
  
  The Standard Errors for the parameters are:
    
        SE(βˆ0)**2 = σ**2[1/n + x'**2/(summation over i belongs to (1, n)(xi - x')**2)
        
        SE(βˆ1)**2 = σ**2 / (summation over i belongs to (1, n) (xi − x)**2)

 The 95% confidence intervals:
    
    βˆ0 ± 2 · SE(βˆ0)

    βˆ1 ± 2 · SE(βˆ1)
    
  Calculations depend on the model

    
  #### Hypothesis test

   H0 : there is no relationship between X and Y
   Ha : There is some relationship between X and Y
   
       H0: β1 = 0
       Ha: β1 != 0
    
   Test statistic:
   
   t = (βˆ1−0) / SE(βˆ1)

   Under the null hypothesis (special case of the model), this has a t-distribution
with n − 2 degrees of freedom.

  #### Interpreting the hypothesis test
  
   * If we reject the null hypothesis, can we assume there is an
exact linear relationship?

         No. A quadratic relationship may be a better fit, for example.
There is evidence of linear association.

   * If we don’t reject the null hypothesis, can we assume there is
no relationship between X and Y ?
    
         No. This test is only powerful against certain monotone alternatives. There could be more complex non-linear relationships.
         
   #### Multiple linear regression
   
   
        Y = β0 + β1X1 + · · · + βpXp + ε    where ε ∼ N (0, σ) 
        
        or, in matrix notation:
        
        Ey = Xβ, where y = (y1, . . . , yn)T, β = (β0, . . . , βp)T and X is our usual data matrix with an extra column of ones on the left to account for the intercept.
        
  #### Multiple linear regression can answer several
  
  * Is at least one of the variables Xi useful for predicting the
outcome Y ?

   * Which subset of the predictors is most important?
   
   * How good is a linear model for these data?
   
   * Given a set of predictor values, what is a likely value for Y , and how accurate is this prediction?
   
   
   #### The estimates βˆ
   
   Our goal again is to minimize the RSS:
   
        RSS = summation over i belongs to (1, n) (yi − yˆi)**2
        
            = summation over i belongs to (1, n) (yi − β0 − β1xi,1 − · · · − βpxi,p)**2
    
   One can show that this is minimized by the vector βˆ:
      
        βˆ = (XT X)−1XTy
        
   We also write RSS for the minimized sum of squares.
   
  #### Which variables are important?
  
  Consider the hypothesis:
  
    H0 : The last q predictors have no relation with Y 
    
    H0 : βp−q+1 = βp−q+2 = · · · = βp = 0
    
   Let RSS0 be the residual sum of squares for the model which
excludes these variables.

    The F-statistic is defined by:
    
            F = ((RSS0 − RSS)/q)/(RSS/(n − p − 1))
      
   Under the null hypothesis, this has an F-distribution
   
   Example: If q = p, we test whether any of the variables is important
   
   The t-statistic associated to the ith predictor is the square root of the F-statistic for the null hypothesis which sets only βi = 0
   
   A low p-value indicates that the predictor is important (it adds something to the model not explained by other variables)
   
   P-hacking warning: If there are many predictors, even under the null hypothesis, some of the t-tests will have low p-values
   
   #### How many variables are important?
   
   When we select a subset of the predictors, we have 2**p choices
   
   A way to simplify the choice is to define a range of models with an increasing number of variables, then select the best
   
   *  Forward selection: Starting from a null model, include variables one at a time, minimizing the RSS at each step
   
   * Backward selection: Starting from the full model, eliminate variables one at a time, choosing the one with the largest p-value at each step
   
   * Mixed selection: Starting from a null model, include variables one at a time, minimizing the RSS at each step. If the p-value for some variable goes beyond a threshold, eliminate that variable
   
   Choosing model this way is a form of tuning. P-hacking: hypothesis tests, confidence intervals not valid after selection! 
   
   #### How good is the fit?
   
   To assess the fit, we focus on the residuals
   
   * The RSS always decreases as we add more variables
   
   * The residual standard error (RSE) corrects this
   
         RSE = sqrt(RSS/(n − p − 1))
         
   * Visualizing the residuals can reveal phenomena that are not accounted for by the model
   
   
   #### Dealing with categorical or qualitative predictors
   
   Example: Credit dataset
   
   * gender: male, female
   * student: student or not
   * status: married, single, divorced
   * ethnicity: African, American, Asian, Caucasia
   
   For each qualitative predictor, e.g. ethnicity:
   
   * Choose a baseline category, e.g. African American
   
   * For every other category, define a new predictor:
    
        * XAsian is 1 if the person is Asian and 0 otherwise
        * XCaucasian is 1 if the person is Caucasian and 0 otherwise
        
   The model will be: 
   
    Y = β0 + β1X1 + · · ·+ β7X7 + βAsian XAsian + βCaucasian XCaucasian + ε.
    
    
   βAsian is the relative effect on balance for being Asian compared to the baseline category
   
   * The model fit and predictions are independent of the choice of the baseline category

   * However, hypothesis tests derived from these variables are affected by the choice
    
        * Solution: To check whether ethnicity is important, use an F-test for the hypothesis βAsian = βCaucasian = 0. This does not depend on the coding
   
   * Other ways to encode qualitative predictors produce the same fit ˆf, but the coefficients have different interpretations
   
   #### How good is the fit?
   
   To assess the fit, we focus on the residuals.
   
   * R2 = Corr(Y, Yˆ ), always increases as we add more variables
   
   * The residual standard error (RSE) does not always improve with more predictors
   
         RSE = sqrt(RSS/(n − p − 1))

   * Visualizing the residuals can reveal phenomena that are not accounted for by the model
   
   #### Potential issues in linear regression
   
   * Interactions between predictors
   * Non-linear relationships
   * Correlation of error terms
   * Non-constant variance of error (heteroskedasticity)
   * Outliers
   * High leverage points
   * Co-linearity
   
   #### Interactions between predictors
   
   Linear regression has an additive assumption:
   
     sales = β0 + β1 × tv + β2 × radio + ε
     
   i.e. An increase of $100 dollars in TV ads causes a fixed increase in sales, regardless of how much you spend on radio ads
   
   If we visualize the residuals, it is clear that this is false
   
   One way to deal with this is to include multiplicative variables in the model:
   
    sales = β0 + β1 × tv + β2 × radio + β3 × (tv · radio) + ε
    
   The interaction variable is high when both tv and radio are high.
   
   * Non-linearities
   
   A scatter plot between a predictor and the response may reveal a non-linear relationship.
   
   * Solution: include polynomial terms in the model.
   
         MPG = β0 + β1 × horsepower + ε
         
         MPG = β0 + β1 × horsepower + β2 × horsepower2 + ε
         
         MPG = β0 + β1 × horsepower + β2 × horsepower2 + β3 × horsepower3 + ε
         
         MPG = β0 + β1 × horsepower + β2 × horsepower2 + β3 × horsepower3 + . . . + ε
         
   In 2 or 3 dimensions, this is easy to visualize. What do we do when we have too many predictors?
   
   Plot the residuals against the response and look for a pattern
   
   #### Correlation of error terms
   
   We assumed that the errors for each sample are independent:
   
        yi = f(xi) + εi; εi ∼ N (0, σ) 
        
   ##### What if this breaks down?
   
   The main effect is that this invalidates any assertions about Standard Errors, confidence intervals, and hypothesis tests
   
   Example: Suppose that by accident, we double the data (we use each sample twice). Then, the standard errors would be artificially smaller by a factor of √2
   
   When could this happen in real life:
   
   * Time series: Each sample corresponds to a different point in time. The errors for samples that are close in time are correlated.
   
   * Spatial data: Each sample corresponds to a different location in space
   
   * Study on predicting height from weight at birth. Suppose some of the subjects in the study are in the same family, their shared environment could make them deviate from f(x) in similar ways
   
   #### Non-constant variance of error (heteroskedasticity)
   
   The variance of the error depends on the input.
   
   To diagnose this, we can plot residuals vs. fitted values:
   
   * Solution: If the trend in variance is relatively simple, we can
transform the response using a logarithm, for example

   #### Outliers
   
   Outliers are points with very high errors.
   
   While they may not affect the fit, they might affect our assessment of model quality
   
   Possible solutions:
   
   * If we believe an outlier is due to an error in data collection, we can remove it

   * An outlier might be evidence of a missing predictor, or the need to specify a more complex model
   
  #### High leverage points
  
  Some samples with extreme inputs have an out sized effect on βˆ.
  
  This can be measured with the leverage statistic or self influence
  
        hii = ∂yˆi/∂yi = (X(XT X)−1XT)i,i ∈ [1/n, 1].
        
  #### Studentized residuals
  
  * The residual ˆi = yi − yˆi is an estimate for the noise i
  
  * The standard error of εˆi is σ √(1 − hii)
  
  * A studentized residual is εˆi divided by its standard error
  
  * When model is correct, it follows a Student-t distribution with n − p − 2 degrees of freedom
  
  #### Collinearity
  
  Two predictors are collinear if one explains the other well:
  
    limit = a × rating + b
    
  i.e. they contain the same information
  
  Problem: The coefficients become unidentifiable. Consider the extreme case of using two identical predictors limit:
  
      balance = β0 + β1 × limit + β2 × limit
      
      balance = β0 + β1 × limit + β2 × limit = β0 + (β1 + 100) × limit + (β2 − 100) × limit
  
  The fit (βˆ0, βˆ1, βˆ2) is just as good as (βˆ0, βˆ1 + 100, βˆ2 − 100)
  
  If 2 variables are collinear, we can easily diagnose this using their correlation
  
  A group of q variables is multi linear if these variables “contain less information” than q independent variables. Pairwise correlations may not reveal multi linear variables
  
  The Variance Inflation Factor (VIF) measures how necessary a variable is, or how predictable it is given the other variables:
  
    V IF(βˆj ) = 1/ (1 − R2Xj |X−j)
    
   where R2Xj |X−j is the R2 statistic for Multiple Linear regression of the predictor Xj onto the remaining predictors
   
   #### Comparing Linear Regression to K-nearest neighbors
   
   Linear regression: prototypical parametric method. Inference
   
   KNN regression: prototypical nonparametric method. Inference?
   
        fˆ(x) = 1/K (summation over i ∈ NK(x) yi)
        
   Long story short:
   
   * KNN is only better when the function f is not linear
   
   * When n is not much larger than p, even if f is nonlinear, Linear Regression can outperform KNN
   
   #### When there are more predictors than observations, Linear Regression dominates

   When p  n, each sample has no nearest neighbors, this is known as the curse of dimensionality
   
   The variance of KNN regression is very large