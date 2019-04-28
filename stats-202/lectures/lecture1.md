# Lecture 1: Course Logistics

### Prediction challenges:
  The MNIST dataset is a library of handwritten digits.
 
  In a prediction challenge, a training set of images of handwritten digits are given, which are lebeled from 0 to 9.
  
  Also a test set of handwritten digits is given, which are not identified.
  
  Now the task is to assign a digit for each and every images in test set.
  
  
    Netflix popularized prediction challenges by organizing an open and blind contest to improve it's recommendation system.
    
    It's data includes Users vs Movies rating (1 to 5 starts)
    
    Some ranking were hidden in training dataset.
    
    The challenge was to predict those rankings.
    
## Supervised vs. Unsupervised learning
    
  #### In unsupervised learning we start with a data matrix.
  
  The matrix includes samples or units vs varibales or factors 
  
##### Goal:
   * **Find a meaningful relationship between variables and units** - ***Correlation analysis***
   
   * **Find low dimensional representations of the data which make it easy to visualize the variables and units** - ***PCA, ICA, isomap, locally linear embeddings, etc***
   
   * **Find meaningful groupings of the data** - ***Clustering***
   
  #### In supervised learning, there are input variables and output variables.
  
  If the output variable is quantitative, then it is called regression problem.
  
  If the output variable is qualitative, then it is called classification problem.
  
  If X is the vector of inputs for a particular sample. Then output variable is modeled by
  
    Y = f(X) + ε  where ε is Random error
   
   ##### Goal
   To learn the function f, using a set of training samples.
   
   ### Motivations:
   
   * ***Prediction*** : useful when the input variable is readily availbale, but the output variable is not.
       
       Example: Predict stock prices next month using data from last year.
       
   * ***Inference*** : A model for f can help us understand the structure of the data
      
      which variables influence the output and which don't?
      
      What is the relationship between each variable and the output e.g. linear or non-linear?
   
    Example: What is the influence of genetic variations on the incidence of heart disease.
 
### A sample Kaggle Challenge

Help out San Francisco's foremost Baroque ensemble bring in subscriptions!

   * ***Option 1*** : Using Philharmonia's database of subscriptions and single ticket sales, including information about concerts, and patrons, predict who will subscribe for the a particular season.
   
   * ***Option 2*** : Create an interactive visualization of Philharmonia's database using the python Dash package.