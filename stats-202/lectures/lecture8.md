# Classification Examples

   #### Example : Predicting default
      
      
  Used LDA to predict credit card default in a dataset of 10K people. Predicted “yes” if P(default = yes|X) > 0.5
  
 * The error rate among people who do not default (false positive rate) is very low
  
  * However, the rate of false negatives is 76%
  
  * It is possible that false negatives are a bigger source of concern!
  
  * One possible solution: Change the threshold
  
  #### Example. The ROC curve
  
  * Displays the performance of the method for any choice of threshold
  
  * The area under the curve (AUC) measures the quality of the classifier:
  
       * 0.5 is the AUC for a random classifier
       
       * The closer AUC is to 1, the better