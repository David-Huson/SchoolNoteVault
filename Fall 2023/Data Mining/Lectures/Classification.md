---
tags:
  - classnotes
  - datamining
Chapter: 6
Course: Data Mining
---
# Classification: Basic Concepts
- Supervised learning (classification)
	- have the data labels
	- data is classified on the training set
- Unsupervised learning (unsupervised learning)
	- class labels are unknown
	- given a set of measurements, observations, etc. with the aim of establishing the existence of clusters in the data
## Decision Tree Induction
### ID3 algorithm
- greedy algorithm
- Stopping conditions
	- all samples for a node belong to the same class
	- no more remaining attributes for further partitioning
	- no samples remaining
- select the attribute with the highest [[information gain]]
### C4.5 (newer algorithm)
- newer versions of this process use gain ration to overcome the problem of information gain being biased towards attributes with large number of values
	- Gain(A)/SplitInfo(A)
- split on attributes with highest gain ratio
### Gini Index (CART,IGM IntelligentMiner)
- reduction in impurity
- trying to clean up the biases in the dataset
- the attribute that provides the smallest gini index is chosen as the split node
- impurity is the variance of attributes of a specific node in the dataset
- all attributes are assumed to be continuous valued
- may need other tools (clustering, etc.) to get the possible split values
- Can be modified for categorical attributes
### Comparing attribute selection measures
- Information Gain
	- biased towards multi-valued attributes
- Gain ratio
	- tends to prefer unbalanced splits in which one partition is much smaller than the others
- Gini index
	- biased to multivalued attributes
	- has difficulty when # of classes is large
	- tends to favor tests that results in equal-sized partitions and purity in both partitions
### Other algorithms
- CHAID
- C-SEP
- G-statistic
- MDL (Minimal Description Length)
- Multivariate splits
	- CART
- Which attribute selection measure is the best?
	- Most give good results, none is significantly superior than others

### Overfitting and Tree Pruning
- Approaches to avoid overfitting
	- Pre-pruning: *Halt tree construction early* - do not split a node if it would result in the goodness measure falling below a threshold
		- Difficult to choose an appropriate threshold
	- Post-pruning: *Remove branches* from a "fully grown" tree - get a sequence of progressively pruned trees
		- Use a set of data different from the training data to decide which is the "best pruned tree"
### Enhancements
- Allow for continuous-valued attributes
	- Dynamically define new discrete valued attributes that partition the continuous attribute value into a discrete set of intervals
- handle missing attribute values
	- Assign the most common value of the attribute
	- assign probability to each of the possible values
- Attribute construction
	- create new attributes based on existing ones
## Classification in Large Datasets
- Why is decision tree induction popular
	- relatively faster learning speed
	- convertible to simple and easy to understand classification rules
	- can use SQL queries for accessing databases
	- comparable classification accuracy with other methods
- Rainforest (VLDB'98 - Gehrke, Ramakrishnan & Ganti)
	- Builds an AVC-list(attribute, value class label)
## Bayesian Classification
- statistical
- based on Bayes' Theorem
- Naive Bayesian classifier - comparable performance with decision tree and selected neural network classifiers
- Incremental
	- each training example can incrementally increase/decrease the probability of getting a correct hypothesis
- Standard
	- typically ran first

> see page 310 in text for different measures for analyzing the performance of our models (Section 6.6)

ROC -> Receiver operator characteristic curve
- plot the false positive rate vs the true positive rate