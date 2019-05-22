# The Bootstrap


 
   #### Cross-validation vs. the Bootstrap
   
   * Cross-validation: provides estimates of the (test) error
   
   * The Bootstrap: provides the (standard) error of estimates
        
        * One of the most important techniques in all of Statistics
        * Computer intensive method
        * Popularized by Brad Efron, from Stanford
        
   #### Standard errors in linear regression
   
   * Standard error: SD of an estimate from a sample of size n
   
   #### Classical way to compute Standard Errors
   
   Example: Estimate the variance of a sample x1, x2, . . . , xn:
   
            σˆ2 =1/(n − 1) Σ(xi − x)2 ;  i ∈ (1, n)
            
   What is the Standard Error of σˆ?
   
   * Assume that x1, . . . , xn are normally distributed with common mean µ and variance σ2
   
   * Then σˆ2(n − 1) has a χ-squared distribution with n − 1 degrees of freedom
   
   * For large n, σˆ2 is normally distributed around σ2
   
   * The SD of this sampling distribution is the Standard Error
   
   #### Limitations of the classical approach
   
   This approach has served statisticians well for many years; however, what happens if:
   
   * The distributional assumption — for example, x1, . . . , xn being normal — breaks down?
   
   * The estimator does not have a simple form and its sampling distribution cannot be derived analytically?
   
   #### Example. Investing in two assets
   
   * Suppose that X and Y are the returns of two assets.
   
   * These returns are observed every day: (x1, y1), . . . ,(xn, yn)
   
   * We have a fixed amount of money to invest and we will invest a fraction α on X and a fraction (1 − α) on Y. Therefore, our return will be
   
            αX + (1 − α)Y
            
   * Our goal will be to minimize the variance of our return as a function of α. One can show that the optimal α is:
        
            α = (σ2Y − Cov(X, Y )) / (σ2X + σ2Y − 2Cov(X, Y ))      
            
   * Proposal: Use an estimate:
   
            αˆ = (σˆ2Y − Covˆ(X, Y )) / (σˆ2X + σˆ2Y − 2Covˆ(X, Y ))
            
   * Suppose we compute the estimate αˆ = 0.6 using the samples (x1, y1), . . . ,(xn, yn)
   
        * How sure can we be of this value?
        
        * If we re-sampled the observations, would we get a wildly different αˆ?
   
   * In this thought experiment, we know the actual joint distribution P(X, Y ), so we can re-sample the n observations to our hearts’ content
   
   #### Computing the standard error of αˆ
   
   * For each resampling of the data,
        
            (x(1)1, . . . , x(1)n)
            (x(2)1, . . . , x(2)n) 
            
            ...
            
   * we can compute a value of the estimate αˆ(1), αˆ(2), . . . .
   
   * The Standard Error of αˆ is approximated by the standard deviation of these values
   
   #### In reality, we only have n samples
   
   * However, these samples can be used to approximate the joint distribution of X and Y
   
   * The Bootstrap: Resample from the empirical distribution:
   
         Pˆ(X, Y ) = 1/n Σδ(xi, yi) ; i ∈ (1, n)
         
   * Equivalently, resample the data by drawing n samples with replacement from the actual observations      
   