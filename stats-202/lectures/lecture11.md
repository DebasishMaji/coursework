# Model selection and regularization



   #### What do we know so far
   
   * In linear regression, adding predictors will always decreases the training error or RSS
   
   * However, adding predictors does not necessarily improve the test error
   
   * Selecting significant predictors is hard when n is not much larger than p
   
   * When n < p, there is no least square solution:
   
            βˆ = (XT X)−1XTy where XT X - Singular
            
         So, we must find a way to select fewer predictors.
       
       
   #### Best subset selection
   
   * Simple Idea: let's compare all models with k predictors
   
   * There are (p k) = p!/[k! (p-k)!] possible models
   
   * Choose the model with the smallest RSS. Do this for every possible k
   
   * Naturally, the RSS and R2 improve as we increase k
   
   To optimize k, we want to minimize the test error, not the training error
   
   We could use cross-validation or alternative estimates of test error:
   
   * Akaike Information Criterion (AIC)
   
            1/nσˆ2(RSS + 2kσˆ2)
            
            where σˆ2 is the estimate of the irrucible error
        
   * Bayesian Information Criterion (BIC)
   
            1/n(RSS + log(n)kσˆ2)
            
   * Adjusted R2
   
            R2 = 1 − (RSS/TSS)
            
            R2adj = 1 − (RSS/(n − k − 1))/(TSS/(n − 1))
            
   #### How do they compare to cross validation;
   
   * They are much less expensive to compute
   
   * They are motivated by asymptotic arguments and rely on model assumptions (e.g. normality of the errors)
   
   * Equivalent concepts of other models (e.g. logistic regression)
   
   #### Example
   
   * Best subset selection for credit dataset
   
   #### Stepwise selection methods
   
   Best subset selection has two problems:
   
   * It is often very expensive computationally. We have to fit 2ˆp models
   
   * If for a fixed k, there are too many possibilities, we increase the chance of overfitting.
    
            The model selected has high variance
           
   In order to mitigate these problems, we can restrict our search space for the best model
   
   This reduce the variance of the selected model at the expense of an increase in bias
   
   #### Forward selection
   
   Algorithm:
    
   1. Let M0 demote the null model, which contains no predictors
   
   2. For k = 0, 1, 2, ..., p-1
   
        I. Consider all p-k models that augment the predictors in Mk with one additional predictor
        
        II. Choose the best among these p-k models, and call it Mk+1. Here best is defined as having smallest RSS or highest Rˆ2
        
        III. Select a single best model from among M0, M1, ... Mp using cross-validated prediction error, Cp (AIC), BIC, or adjusted Rˆ2
        
   #### Backward Selection
   
   Algorithm:
   
   1. Let Mp denote the full model, which contains all p predictors
   
   2. For k = p, p-1, ..., 1:
        
        I. Consider all k models that contains all but one of the predictors in Mk, for a total of k-1 predictors
        
        II. Choose the best among these k models and call it Mk-1. Here best is defined as having smallest RSS or highest Rˆ2
        
   3. Select a single best model from among M0, ...,Mp using cross validated prediction error, Cp (AIC), BIC, of adjusted Rˆ2
   
   
   #### Forward vs Backward selection
   
   * You cannot apply backward selection when p > n
   
   * Although it seems like they should, they need not produce the same sequence of models
   
   Example:
   
   * X1, X2 ∼ N (0, σ) independent
        
            X3 = X1 + 3X2
            
            Y = X1 + 2X2 + ε
            
            Regress Y onto X1, X2, X3.
            
   * Forward: {X3} → {X3, X2} → {X3, X2, X1}
   
   * Backward: {X1, X2, X3} → {X1, X2} → {X2}
   
        
   #### Other stepwise selection strategies
   
   * Mixed stepwise selection: Do forward selection, but at every step, remove any variables that are no longer “necessary”.
   
   #### Shrinkage methods
   
   * A mainstay of modern statistics
   
         The idea is to perform a linear regression, while regularizing or shrinking the coefficients βˆ toward 0
         
   #### Why would shrunk coefficients be better?
   
   * This introduces bias, but may significantly decrease the variance of the estimates. If the latter effect is larger, this would decrease the test error
       
   * Extreme example: set βˆ to 0 – variance is 0!
   
   * There are Bayesian motivations to do this: the prior tends to shrink the parameters
   
   #### Ridge regression
   
   Ridge regression solves the following optimization:
   
        minβ Σ (yi − β0 −Σβjxi,j)ˆ2 + λ Σβjˆ2 where i ∈ (1, n) anf j ∈ (1, p)
        
       first part, we have the RSS of the model.     
        
       second part, we have the squared `2 norm of β, or kβk
       
        The parameter λ is a tuning parameter. It modulates the importance of fit vs. shrinkage    
        We find an estimate βˆRλ for many values of λ and then choose it by cross-validation
   
        Fortunately, this is no more expensive than running a least-squares regression
        
   In least-squares linear regression, scaling the variables has no effect on the fit of the model:
   
    Y = X0 + β1X1 + β2X2 + · · · + βpXp.
    
   Multiplying X1 by c can be compensated by dividing βˆ1 by c, ie. after doing this we have the same RSS
   
   In ridge regression, this is not true.
   
   #### In practice, what do we do?
   
   * Scale each variable such that it has sample variance 1 before running the regression
   
   * This prevents penalizing some coefficients more than others
   
   #### Bias-variance trade-off
   
   * In a simulation study, we compute bias, variance, and test error as a function of λ.
   
   * Cross validation would yield an estimate of the test error.
   