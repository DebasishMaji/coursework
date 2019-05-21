# Classification

   Supervised learning with a qualitative or categorical response.

   Just as common, if not more common than regression:
    
   * Medical diagnosis: Given the symptoms a patient shows, predict which of 3 conditions they are attributed to
    
   * Online banking: Determine whether a transaction is fraudulent or not, on the basis of the IP address, client’s history, etc
   
   * Web searching: Based on a user’s history, location, and the string of a web search, predict which link a person is likely to click
   
   * Online advertising: Predict whether a user will click on an ad or not
   
   #### Review: Bayes classifier
   
   Suppose P(Y | X) is known. Then, given an input x0, we predict the response
   
    yˆ0 = argmax y P(Y = y | X = x0)
    
   The Bayes classifier minimizes the expected 0-1 loss:
   
        E[1/m (summation over i ∈ (1, m) (ˆyi != yi))]
        
   This minimum 0-1 loss (the best we can hope for) is the Bayes error rate
   
   #### Strategy: estimate P(Y | X)
   
   If we have a good estimate for the conditional probability Pˆ(Y | X), we can use the classifier
   
    yˆ0 = argmax y Pˆ(Y = y | X = x0)
    
   Suppose Y is a binary variable. Could we use a linear model?
   
    P(Y = 1|X) = β0 + β1X1 + · · · + β1Xp
    
   Problems:
   
   * This would allow probabilities <0 and >1
   
   * Difficult to extend to more than 2 categories
   
   #### Logistic regression
   
   We model the joint probability as:
   
    P(Y = 1 | X) = (eβ0+β1X1+···+βpXp)/(1 + eβ0+β1X1+···+βpXp)
    
    P(Y = 0 | X) = 1/(1 + β0+β1X1+···+βpXp)
    
   This is the same as using a linear model for the log odds:
   
        log[P(Y = 1 | X)/P(Y = 0 | X)] = β0 + β1X1 + · · · + βpXp
        
   #### Fitting logistic regression
   
   The training data is a list of pairs (y1, x1),(y2, x2), . . . ,(yn, xn). In the linear model
   
    log[P(Y = 1 | X)/P(Y = 0 | X)] = β0 + β1X1 + · · · + βpXp
    
   we don’t observe the left hand side.

   We cannot use a least squares fit.
   
   Solution:
   
   The likelihood is the probability of the training data, for a fixed set of coefficients β0, . . . , βp:
       
        Product over i ∈ (1, n) P(Y = yi| X = xi)   
        
   * Choose estimates βˆ0, . . . , βˆp which maximize the likelihood

   * Solved with numerical methods (e.g. Newton’s algorithm)
   
   #### Example: Predicting credit card default
   
   Predictors:
   * student: 1 if student, 0 otherwise.
   * balance: credit card balance.
   * income: person’s income.

   In this dataset, there is confounding, but little collinearity.
   
   * Students tend to have higher balances. So, balance is explained by student, but not very well
   * People with a high balance are more likely to default
   * Among people with a given balance, students are less likely to default
   
   #### Extending logistic regression to more than 2 categories
   
   Multinomial logistic regression:
   
   Suppose Y takes values in {1, 2, . . . , K}, then we use a linear model for the log odds against a baseline category (e.g. 1):
   
      log[P(Y = 2 | X)/P(Y = 1 | X)] = β0,2 + β1,2X1 + · · · + βp,2Xp,
      
      ...
      
      log[P(Y = K | X)/P(Y = 1 | X)] = β0,K + β1,KX1 + · · · + βp,KXp.
      
   #### Some issues with logistic regression
   
   * The coefficients become unstable when there is collinearity. Furthermore, this affects the convergence of the fitting algorithm
   
   * When the classes are well separated, the coefficients become unstable. This is always the case when p ≥ n − 1
   
  #### Linear Discriminant Analysis (LDA)
  
  Strategy: Instead of estimating P(Y | X), we will estimate:
  
  1. Pˆ(X | Y ): Given the response, what is the distribution of the inputs.
  2. Pˆ(Y ): How likely are each of the categories
  
  Then, we use Bayes rule to obtain the estimate:
  
        Pˆ(Y = k | X = x) = (Pˆ(X = x | Y = k)Pˆ(Y = k))/Pˆ(X = x)
        
        Pˆ(Y = k | X = x) = (Pˆ(X = x | Y = k)Pˆ(Y = k))/summation over j Pˆ(X = x | Y = j)Pˆ(Y = j)
  
  
  1. We model Pˆ(X = x | Y = k) = ˆfk(x) as a Multivariate Normal Distribution
  2. Pˆ(Y = k) = ˆπk is estimated by the fraction of training samples of class k