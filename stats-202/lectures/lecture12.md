# Shrinkage


   The idea is to perform a linear regression, while regularizing or shrinking the coefficients βˆ toward 0
   
   Why would shrunk coefficient be better ?
   
   * This introduces bias, but ay significantly decrease the variance of the estimates. If the latter effect is larger, this would decrease the test error
   
   * There are Bayesian motivations to do this: the prior tends to shrink the parameters
   
  #### Ridge Regression
  
  * Ridge regression solves the following optimization:
  
        minβ Σ(yi − β0 −Σβjxi,j)**2+ λΣβj**2
        
  The parameter λ is a tuning parameter. It modulates the importance of fit vs. shrinkage
   
   We find an estimate βˆRλ for many values of λ and then choose it by cross-validation
   
   
   #### Bias-variance tradeof
   
   In a simulation study, we compute bias, variance, and test error as a function of λ
   
   #### Ridge regression
   
   In least-squares linear regression, scaling the variables has no effect on the fit of the model:
   
    Y = β0 + β1X1 + β2X2 + · · · + βpXp
    
   Multiplying X1 by c can be compensated by dividing βˆ1 by c, ie. after doing this we have the same RSS
   
   In ridge regression, this is not true.
   
   In practice, what do we do?
   
   * Scale each variable such that it has sample variance 1 before running the regression
   
   * This prevents penalizing some coefficients more than others
   
   #### Example. Ridge regression
   
   Ridge regression of default in the Credit dataset.
   
   #### The Lasso
   
   Lasso regression solves the following optimization:
   
        minβ Σ(yi − β0 −Σβjxi,j)**2+ λΣ|βj|
   
   Why would we use the Lasso instead of Ridge regression?
   
   * Ridge regression shrinks all the coefficients to a non-zero value
   
   * The Lasso shrinks some of the coefficients all the way to zero. Alternative convex to best subset selection or stepwise selection!
   
   
   #### Example. Ridge regression
   
   Ridge regression of default in the Credit dataset.
   
   A lot of pesky small coefficients throughout the regularization path.
   
   
   #### Example. The Lasso
   
   Lasso regression of default in the Credit dataset.
   
   Those coefficients are shrunk to zero.
   
   #### When is the Lasso better than Ridge?
   
   Example 1. Most of the coefficients are non-zero
   
   * Plot the Bias, Variance, MSE
   * The bias is about the same for both methods
   * The variance of Ridge regression is smaller, so is the MSE
   
   Example 2. Only 2 coefficients are non-zero
   
   * Plot Bias, Variance, MSE
   * The bias, variance, and MSE are lower for the Lasso
   
   #### Choosing λ by cross-validation
   
   A very special case
   
   Suppose n = p and our matrix of predictors is X = I.
   
   Then, the objective function in Ridge regression can be simplified:
   
        Σ(yj − βj )**2 + λΣβj**2
       
   and we can minimize the terms that involve each βj separately:
   
        (yj − βj )**2 + λβj**2
        
   It is easy to show that
   
        βˆRj = yj / (1 + λ)
        
   Similar story for the Lasso; the objective function is:
   
        Σ(yj − βj )**2 + λΣ|βj|
        
   and we can minimize the terms that involve each βj separately:
   
        (yj − βj)**2 + λ|βj|
   
   It is easy to show that
   
        βˆLj = yj − λ/2 if yj > λ/2
             = yj + λ/2 if yj < −λ/2
             = 0 if |yj | < λ/2
             
   #### Bayesian interpretations
   
   * Ridge: βˆR is the posterior mean, with a Normal prior on β.
   
   * Lasso: βˆL is the posterior mode, with a Laplace prior on β.
   
   
   
   