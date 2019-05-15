# Clustering

As in classification, we assign a class to each sample in the data matrix. However the class is not a output variable, we only use input variables.

Clustering is a unsupervised algorithm whose goal is to find homogeneous subgroups among the observations.


#### K-means clustering:

   * K is the number of cluster we know in advance
   * The goal of this method is to maximize the similarity of samples within each cluster

   
     min (summation of W(Cl) l belongs to (1, k) ) over C1,...,Ck
     
 
#### Algorithm:

   1. Assign each sample to a cluster fro 1 to K at random
   2. Iterate below two steps until the clustering is constant
   
       * Find the centroid of each cluster l i.e. the average xl' of all the samples in the cluster
       
             xi,j = (summation of xi,j where i belongs to (1, p) and i belongs to Cl)/|Cl|
             
        * Reassign each samples to it's nearest centroid
        
        
   * The algorithm always converge to a local minimum of 
   
            
      min (summation of W(Cl) l belongs to (1, k) ) over C1,...,Ck
   
   * Each initialization could yield a different value
   
   In practice we start from many random initialization 