---
tags:
  - classnotes
  - datamining
Chapter: 4
Course: Data Mining
---
# Basic Concepts
- Frequent patterns
- Item Set
- k-item set
- Frequent Itemsets - those item sets that relatively popular in the dataset
- support count of *X*
	- frequent if *X*'s support is no less than a minimum support threshold
## Frequent pattern mining
- looking for recurring relationships
- Attempts to discover interesting associations and correlations between itemsets in a transactional and relational database
- pattern analysis in spatiotemporal, multimedia and time-series data
- sequential. structural patterns
- Classification
- Cluster analysis
- data warehousing
- semantic data compression
## Pattern mining approaches
### Support (aka Probability)
- the name of the measurement that is used to quantify
*Probability(A=>B) = P(A U B)*

### Confidence
- quantify the percentage of transactions that contain a specific itemset
### Lift (importance)
- simple correlation measure
- when <1 the occurrence of A is negatively correlated with occurrence with B
- when >1 the occurrence of A is positively correlated with occurrence with B
- when =1 the occurrence of the there is no correlation between the variables and they are said to be *independent*

### Coverage
- how frequent the antecedent appears in the dataset
## Association Rules
- used to underline groups that typically occur together in the dataset
- find all rules where X => Y with a minimum support and confidence 
	- support, *s*, probability that a transition contains X U Y
	- confidence , *c*, conditional probability that a transaction having X also contains Y
### Applications
- Market basket analysis
	- measure the association between products purchased by a customer
	- - A transaction means a single visit to a retailer, for which the list of purchases is recorded
- Web Click-stream analysis
	- measure the associations between pages viewed sequentially by a website visitor
	- A transaction means a web session, for which the list of all visited web pages is recorded
## Algorithms
### Apriori
- Bottlenecks
	- Breadth-first search
	- Candidate generation and test
	- Often generates a huge number of candidates
### Frequent pattern growth approach
- Depth first search
- avoid explicit candidate generation
- major philosophy: Grow long a
- builds a tree based on the support count
- the tree gives us a conditional pattern base

### Vertical Data format
- Column-store indexes are the standard for storing and querying large data warehousing fact tables
- numerical aggregations on the column values are stored in the index for faster retrieval
- up to 10X better performance and than trad row-oriented storage
- up to 10X the data compression over the uncompressed data size
- same principles of the Apriori algorithm apply