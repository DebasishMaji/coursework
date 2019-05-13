# Supervised vs Unsupervised learning, bias-variance trade off

   #### In supervised learning our goal is to:
    
   * ***Correlation Analysis*** 
           
         Find meaningful relationship betwwen the variales or units
    
   * ***PCA, ICA, isomap, locally linear embeddings***
    
         Find low-dimentional representation of the data which make it easy to visualize the variables and units
    
   * ***Clustering***
    
         Find meaningful grouping of data
    
 
   Note: Unsupervised Learning is also known as exploratory data analysis in statistics
 
 #### In Supervised Learning there are input variables and output variables.
 
 Depending on the type of output variables Supervised learning is categorized as classification and regression
 
 If X is the vector of inputs for a particular sample. The output variable is modeled as 
    
         Y = f(X) + ε where ε is a Random error
         
 Here the goal is to learn the function f, using a a set of training samples.
 
 Typically we assume ε is independent of X given f(X) 
 
 i.e.  Y | X ~ N(f(X), σ2) though this is not necessary.
 
 #### Motivations:
   
   * ***Prediction*** : useful when the input variable is readily availbale, but the output variable is not.
       
       Example: Predict stock prices next month using data from last year.
       
   * ***Inference*** : A model for f can help us understand the structure of the data
      
      which variables influence the output and which don't?
      
      What is the relationship between each variable and the output e.g. linear or non-linear?
   
    Example: What is the influence of genetic variations on the incidence of heart disease.
 
 #### Parametric and nonparametric methods:
 
  There are two kinds of supervised learning method:
  
  * ***Parametric Methods*** : We assume that f takes a specific form. For example, a linear form: 
        
        f(X) = X1β1 + · · · + Xpβp
        
       with parameters s β1, . . . , βp. Using the training data we try to fit the parameters.
       
   * ***Non-Parametric Methods*** : We don't make any assumptions on the form of f, but we restrict how "wiggly" or "rough" the function can be.
   
   
   Parametric methods have a limit of fit quality. Non-parametric methods keep improving as we add more data to fit.
   
 #### Prediction Error: 
 
   * ***Training data***: (x1, y1),(x2, y2). . .(xn, yn)
   * ***Prediction function***: f'
   * ***Future data***: (X0, y0) having some distribution
   
   Our goal in supervised learning is to minimize the prediction error.
   
   For regression models, this is typically the Mean Square Error
   
        MSE(f') = E(y0 − f'(x0))^2
   
   Unfortunately, this quantity cannot be computed, because we don't know the joint distribution of (X, Y). We can compute a sample average using the training data; this is known as the training MSE:
    
        MSEtraining(f') = 1/n Σ(yi − f'(xi))^2 where i belongs to (1, n)

   The main challenge of statistical learning is that a low training MSE does not imply a low MSE.
   
   If we have test data {(x'i, y'i); i = 1, . . . , m} which were not used to
fit the model, a better measure of quality for f' is the test MSE:

        MSEtest(f') = 1/m Σ(y'i − f'(x'i))^2 where i belongs to (1, m)

  #### The bias variance decomposition
    
   Let x0 be a fixed test point, y0 = f(x0) + ε0, and f' be estimated from n training examples (x1, y1). . .(xn, yn).
   
   Let E denote the expectation over y0 and the training outputs (y1, . . . , yn). Then the Mean Squared Error at x0 can be decomposed as: 
   
    MSE(x0) = E(yo - f'(x0))^2 = Var(f'(x0)) + [Bias(f'(x0))]^2 + Var(ε0)
    
    
   The squared bias of the estimate of Y : E(yo - f'(x0))^2
   
   This measures the deviation of the average prediction f'(x0) from the truth f(x0)
   
   
  #### Implications of bias variance decomposition
  
   * The MSE is always positive
   
   * Each element on the right hand side is always positive
   
   * Therefore, typically when we decrease the bias beyond some point, we increase the variance, and vice-versa
   
    More flexibility ⇐⇒ Higher variance ⇐⇒ Lower bias
   
   #### Classification Problems
   
   In a classification setting, the output takes values in a discrete set.
   
   For example, if we are predicting the brand of a car based on a number of variables, the function f takes {Ford, Toyota, Mercedes-Benz, . . . }.
   
   The model:
            
     Y = f(X) + ε
    
   becomes insufficient, as X is not necessarily real-valued.
   
  #### Loss function for classification
  
  There are many ways to measure the error of a classification prediction. One of the most common is the 0-1 loss:
  
    E(1(y0 != y'0))
   
  like the MSE, this quantity can be estimated from training and test data by taking a sample average:
  
        1/n Σ 1(yi != y'i) where i belongs to (1, n)
        
  #### Bayes Classifier
  
  In practice, we never know the joint probability P, However, we can assume that it exists
  
  The Bayes Classifier assigns:
    
        y'i = argmax j P(Y = j | X = xi)     
  
  It can be shown that this is the best classifier under the 0-1 loss