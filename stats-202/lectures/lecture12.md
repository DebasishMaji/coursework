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