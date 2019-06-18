# Counting


    
  Counting is important in the world of computer science for a few reasons. In order to understand
probability on a fundamental level, it is useful to first understand counting.


   #### Sum Rule:
   
   If the outcome of an experiment can either be one of m outcomes or one of n outcomes, where
none of the outcomes in the set of m outcomes is the same as the any of the outcomes in the set
of n outcomes, then there are m + n possible outcomes of the experiment

    If the outcomes of an experiment can either be drawn from set A or set B, where |A| = m and |B| = n, and A ∩ B = ∅, then the number of outcomes of the experiment is |A| + |B| = m + n.
    
   ##### EXAMPLE
   
   * Problem:
   
    You are running an on-line social networking application which has its distributed servers housed in two different data centers, one in San Francisco and the other in Boston. The San Francisco data center has 100 servers in it and the Boston data center has 50 servers in it. If a server request is sent to the application, how large is the set of servers it may get routed to?
    
   * Solution:
   
    Since the request can be sent to either of the two data centers and none of the machines in either data center are the same, the Sum Rule of Counting applies. Using this rule, we know that the request could potentially be routed to any of the 150 (= 100 + 50) servers.
    
   #### Product Rule:
   
   If an experiment has two parts, where the first part can result in one of m outcomes and the
second part can result in one of n outcomes regardless of the outcome of the first part, then the
total number of outcomes for the experiment is m · n.

     If an experiment with two parts has an outcome from set A in the first part, where |A| = m, and an outcome from set B in the second part (regardless of the outcome of the first part), where |B| = n, then the total number of outcomes of the experiment is |A||B| = mn
     
   ##### Example
   
   * Problem:
   
    Two 6-sided dice, with faces numbered 1 through 6, are rolled. How many possible outcomes of the roll are there?
    
   * Solution:
   
    Note that we are not concerned with the total value of the two dice, but rather the set of all explicit outcomes of the rolls. Since the first die1 can come up with 6 possible values and the second die similarly can have 6 possible values (regardless of what appeared on the first die), the total number of potential outcomes is 36 (= 6 * 6). These possible outcomes are explicitly listed below as a series of pairs, denoting the values rolled on the pair of dice:
    
    (1, 1) (1, 2) (1, 3) (1, 4) (1, 5) (1, 6)
    (2, 1) (2, 2) (2, 3) (2, 4) (2, 5) (2, 6)
    (3, 1) (3, 2) (3, 3) (3, 4) (3, 5) (3, 6)
    (4, 1) (4, 2) (4, 3) (4, 4) (4, 5) (4, 6)
    (5, 1) (5, 2) (5, 3) (5, 4) (5, 5) (5, 6)
    (6, 1) (6, 2) (6, 3) (6, 4) (6, 5) (6, 6)
    
    
   * Problem:
           
    Consider a hash table with 100 buckets. Two arbitrary strings are independently hashed and added to the table. How many possible ways are there for the strings to be stored in the table?
    
   * Solution:
   
    Each string can be hashed to one of 100 buckets. Since the results of hashing the first string do not impact the hash of the second, there are 100 * 100 = 10,000 ways that the two strings may be stored in the hash table