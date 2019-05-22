#  Classification, LDA

   Find an estimate Pˆ(Y | X). Then, given an input x0, we predict the response as in a Bayes classifier:
   
        yˆ0 = argmax y Pˆ(Y = y | X = x0)
    
   #### Linear Discriminant Analysis (LDA)
   
   Strategy: Instead of estimating P(Y | X), we will estimate:
  
  1. Pˆ(X | Y ): Given the response, what is the distribution of the inputs.
  2. Pˆ(Y ): How likely are each of the categories
  
  Then, we use Bayes rule to obtain the estimate:
  
        Pˆ(Y = k | X = x) = (Pˆ(X = x | Y = k)Pˆ(Y = k))/Pˆ(X = x)
        
        Pˆ(Y = k | X = x) = (Pˆ(X = x | Y = k)Pˆ(Y = k))/summation over j Pˆ(X = x | Y = j)Pˆ(Y = j)
  
  
  1. We model Pˆ(X = x | Y = k) = ˆfk(x) as a Multivariate Normal Distribution
  2. Pˆ(Y = k) = ˆπk is estimated by the fraction of training samples of class k
  
  #### LDA has linear decision boundaries
  
  Suppose that:
  
  * We know P(Y = k) = πk exactly
  
  * P(X = x|Y = k) is Multivariate Normal with density
  
        fk(x) = (e− 1/2 (x−µk)T Σ−1(x−µk))/((2π)p/2|Σ|1/2)
        
        µk : Mean of the inputs for category k
        
        Σ : Covariance matrix (common to all categories)
        
  Then, what is the Bayes classifier?
  
  By Bayes rule, the probability of category k, given the input x is:
  
        P(Y = k | X = x) = fk(x)πk / P(X = x)
    
  The denominator does not depend on the response k, so we can write it as a constant:
  
        P(Y = k | X = x) = C × fk(x)πk
        
  Now, expanding fk(x):
  
        P(Y = k | X = x) = Cπk * e− 1/2 (x−µk)T Σ−1(x−µk))/ ((2π)p/2|Σ|1/2)

  Now, let us absorb everything that does not depend on k into a constant C':
  
        P(Y = k | X = x) = C'πke− 1/2(x−µk)T Σ−1(x−µk)
  
  and take the logarithm of both sides:
  
        log P(Y = k | X = x) = logC' + logπke− 1/2(x−µk)T Σ−1(x−µk)
  
  This is the same for every category, k
  
  So we want to find the maximum of this over k
  
  Goal, maximize the following over k:
  
        log πk −1/2(x − µk)T Σ−1(x − µk)
  
        = log πk −1/2(xT Σ−1x + µTk Σ−1µk + xT Σ−1µk
        
        = C'' + log πk −1/2µTk Σ−1µk + xT Σ−1µk
  
  We define the objective:
  
    δk(x) = log πk −1/2µTk Σ−1µk + xT Σ−1µk
    
  At an input x, we predict the response with the highest δk(x)
  
  What is the decision boundary? It is the set of points in which 2 classes do just as well:
  
        δk(x) = δl(x)
        
        log πk −1/2µTk Σ−1µk + xT Σ−1µk = log πl −1/2µTl Σ−1µl + xT Σ−1µl
        
  This is a linear equation in x
  
  
  #### Estimating πk
  
    πˆk = #{i ; yi = k} / n
    
  In English, the fraction of training samples of class k
  
  #### Estimating the parameters of fk(x)
  
  Estimate the center of each class µk:
  
        µˆk =1/#{i ; yi = k} Σ xi where i ; yi=k
        
  Estimate the common covariance matrix Σ:
  
  * One predictor (p = 1):
  
        σˆ2 = ΣΣ(xi − µˆk)2 / (n -K) where i ; yi=k and k ∈ (1, K)
  
  * Many predictors (p > 1): Compute the vectors of deviations (x1 − µˆy1),(x2 − µˆy2), . . . ,(xn − µˆyn) and use an unbiased estimate of its covariance matrix, Σ
  
  #### LDA prediction
  
  For an input x, predict the class with the largest:
  
    δk(x) = log ˆπk − 1/2 µˆTk Σˆ −1µˆk + xT Σˆ −1µˆk
    
  The decision boundaries are defined by:
  
    log ˆπk − 1/2 µˆTk Σˆ −1µˆk + xT Σˆ −1µˆk = log ˆπl − 1/2 µˆTl Σˆ −1µˆl + xT Σˆ −1µˆl
    
  #### Quadratic discriminant analysis (QDA)
  
  The assumption that the inputs of every class have the same covariance Σ can be quite restrictive
  
  In quadratic discriminant analysis we estimate a mean µˆk and a covariance matrix Σˆk for each class separately
  
  Given an input, it is easy to derive an objective function:
  
        δk(x) = log πk −1/2(xT Σ−1x + µTk Σ−1µk + xT Σ−1µk - 1/2 xT Σ−1kx - 1/2 log |Σk|
        
  This objective is now quadratic in x and so are the decision boundaries
  
  #### Evaluating a classification method
  
  0-1 loss:
  
        1/m Σ 1(yi != ˆyi) where i ∈ (1, m)
        
  It is possible to make the wrong prediction for some classes more often than others. The 0-1 loss doesn’t tell you anything about this
  
  