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
   
