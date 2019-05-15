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
   
   #### Hierarchical Clustering
   
   * Most algorithms for hierarchical clustering are agglomerative.
   
   * The output of the algorithm is a dendogram. We must be careful about how we interpret the dendogram.
   
  #### Notion of distance between clusters
  
   * At each step, we link the 2 clusters that are “closest” to each other.
   
   * Hierarchical clustering algorithms are classified according to the notion of distance between clusters.
   
  ##### Complete linkage:
   
    The distance between 2 clusters is the maximum distance between any pair of samples, one in each cluster.
    
  ##### Single linkage:
    
    The distance between 2 clusters is the minimum distance between any pair of samples, one in each cluster.
  
  ##### Average linkage:
    
    The distance between 2 clusters is the average of all pairwise distances.
  
  #### Clustering is riddled with questions and choices
  
  * Is clustering appropriate? i.e. Could a sample belong to more than one cluster?
        
       * Mixture models, soft clustering, topic models
       
  * How many clusters are appropriate?
  
       * Choose subjectively — depends on the inference sought.
       
       * There are formal methods based on gap statistics, mixture models, etc.

  * Are the clusters robust?
        
       *  Run the clustering on different random subsets of the data. Is the structure preserved?

       * Try different clustering algorithms. Are the conclusions consistent?
    
       * Most important: temper your conclusions
       
   * Should we scale the variables before doing the clustering
   
       * Variables with larger variance have a larger effect on the Euclidean distance between two samples.

   * Does Euclidean distance capture dissimilarity between samples?
   
   #### Correlation distance
   
   Suppose that we want to cluster customers at a store for market segmentation.
        
   * I Samples are customers
   
   * Each variable corresponds to a specific product and measures the number of items bought by the customer during a year.

   * Euclidean distance would cluster all customers who purchase few things 

   * Perhaps we want to cluster customers who purchase similar things 
    
   * Then, the correlation distance may be a more appropriate measure of dissimilarity between samples.