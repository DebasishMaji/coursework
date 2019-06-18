# Dimensionality reduction


   #### Shrinkage methods:
   
        minβ RSS(β) + λΣβj**2
        
   #### The Lasso:
   
        minβ RSS(β) + λΣ|βj|
        
   As we increase λ we increase bias, but reduce variance.
   
   #### Lasso and Ridge coefficients as a function of λ
   
   Special case X = I. Each coefficient βˆRj, βˆLj depends only on yj
   
   #### Bayesian interpretations
   
   * Ridge: βˆR is the posterior mean, with a Normal prior on β.
   * Lasso: βˆL is the posterior mode, with a Laplace prior on β.    
   
   #### Regularization methods
   
   * Variable selection:
        
        * Best subset selection
        
        * Forward and backward stepwise selection
        
   * Shrinkage
   
        * Ridge regression
        
        * The Lasso (a form of variable selection)
        
   * Dimensionality reduction:
    
        * Idea: Define a small set of M predictors which summarize the information in all p predictors
        
   #### Principal Components Regression
   
   Recall: The loadings φ11, . . . , φp1 for the first principal component define the directions of greatest variance in the space of variables
   
   
    Variable UrbanPop     Murder    Assault     Rape
    Loading  φ11 = 0.28  φ21 = 0.54 φ31 = 0.59 φ41 = 0.54

   Interpretation: The first principal component measures the overall rate of crime.
   
   Recall: The scores z11, . . . , zn1 for the first principal component define the deviation of the samples along this direction.

        zi1 = Σφj1xij
        
        Sample  Alabama     Alaska ... Wyoming
        Score   z11 = 172 z21 = 196 ... zn1 = 122
        
        
   Interpretation: The scores for the first principal component measure the overall rate of crime in each state.
   
   
   Idea:

   * Replace the original predictors, X1, X2, . . . , Xp, with the first M score vectors Z1, Z2, . . . , ZM.
   * Perform least squares regression, to obtain coefficients θ0, θ1, . . . , θM.
   
    The model is:
        
        yi = θ0 + θ1zi1 + θ2zi2 + · · · + θMziM
        
           = θ0 + θ1Σφj1xij + θ2Σφj2xij + · · · + θMΣφjMxij where j belongs to (1, p)
           
           = θ0 + Σθmφ1m xi1 + ... + Σθmφpm xip where m belongs to (1, M)
           
           
   Equivalent to a linear regression onto X1, . . . , Xp, with coefficients:
    
        βj = Σθmφjm where m belongs to (1, M)