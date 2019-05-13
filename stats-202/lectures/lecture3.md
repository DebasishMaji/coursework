# Principal Components Analysis (PCA)

  This is the most popular unsupervised procedure ever
  
  Invented by Karl Pearson(1901)
  
  Developed by Harold Hotelling (1933)
  
    It provides a way to visualize high dimentional data. summarizing the most important information
      
  #### What is the first principal component?
    
    It is the vector which passes closest to the cloud of sample, in terms of squared Euclidean distance
    
  #### What does it look like in 3 variables?
  
    The first two principal components span a plan which is closest to the data
    
    The projection onto the first principal component is one with the highest varience.
    
  #### Mathematical Interpretation
  
   Let X be a data matrix with n samples and p variables
    
   For each variable we substruct the mean of the column i.e. we center the variables
    
   * To find the first principal component φ1 = (φ11, . . . , φp1), we solve the following optimization
                
            max((summation over i((summation over j (φj1xij) where j belongs to (1, p)) **2) where i belongs to (1,n))/n) over (φ11, . . . , φp1)
     
            subject to  summation (Qj1 **2) over j belongs to (1, p) = 1
     
    Inner summation is the projection of the ith sample onto φ1. Also known as the score zi1  
    
    Outer summation is the variance of the n samples projected onto φ1.
   
   * To find the second principal component φ2 = (φ12, . . . , φp2), we solve the following optimization
        
            max((summation over i((summation over j (φj2xij) where j belongs to (1, p)) **2) where i belongs to (1,n))/n) over (φ12, . . . , φp2)
     
            subject to  summation (Qj2 **2) over j belongs to (1, p) = 1 and 
                        summation (φj1φj2) over j belongs to (1, p) = 0
             
    Last conditon ensures First and second principal components must be orthogonal.
    
    Equivalent to saying that the scores (z11, . . . , zn1) and (z12, . . . , zn2) are uncorrelated.
    
   #### Solving the Optimization
   
   This optimization is fundamental in linear algebra. It is satisfied by either
   
   * The single value decomposition(SVD) of X:
        
          X = UΣΦ^T
          
          where 
          
          the ith column of Q is the ith principal component Qi
          the ith column of UΣ is the ith vector of scores (z1i, . . . , zni)
          
   * The eigendecomposition of X^TX:
   
            X^TX = ΦΣ^2Φ^T
            
            
