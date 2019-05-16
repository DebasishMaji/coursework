# Linear Regression

   Model
    
    yi = β0 + β1xi + εi
   
    εi ∼ N (0, σ)
   
   The estimates βˆ0 and βˆ1 are chosen to minimize the residual sum of squares (RSS): 
        
        RSS = summation over i belongs to (1, n) (yi − yˆi)**2
        
            = summation over i belongs to (1, n) (yi − β0 − β1xi)**2
        
   #### Estimates βˆ0 and βˆ1
   
   A little calculus shows that the minimizers of the RSS are:
   
        βˆ1 = (summation over i belongs to (1, n) (xi − x')(yi − y)) / (summation over i belongs (1, n) (xi − x)**2)
        
        βˆ0 = y − βˆ

