#datamining
# Introduction
Professor Dissertation: Knowledge Discovery in Fetal Activity Data
Knowledge Discovery == Data Mining

> We are drowning in data, but starving for knowledge

## Data mining
### Process
Source -> Cleaning -> Warehousing -> Selection -> Mining -> Pattern/Knowledge Eval -> Knowledge

## Diversity of data types
[[Structured]] vs. [[Unstructured]]

### Structured Data Mining
Graph mining
Information network analysis
Link mining

[[Stored Data]] vs. [[Streaming Data]]

Data Mining/Analytics Categories
[[Descriptive]]
[[Diagnostic]]
[[Predictive]]
[[Prescriptive]]

### Data mining tasks (functions)
#### Multidimensional data summarization (Generalization)
-  information integration and data warehouse construction
	- data cleaning, transformation, integration and multDim models
-  Data cube technology
	- scalable methods or computing (materializing) multidim aggregates
- OLAP
-  multi dimensional concept describe 
	- Generalize, summarize, and contrast data characterizations
2. Mining frequent patterns associations and correlations
	1. Frequent patterns
		1. What items are frequently purchased together?
			1. mismatches chan be very informative
	2. Association, correlation vs. causality
		1. A typical association rule
			1. Diaper => Beer [0.5%, 75%] (support, confidence)
			2. Generally discarded as uninteresting if the rule does not meet the minimum support and confidence thresholds
		2. How to mine such patterns and rules efficiently in large datasets?
		3. How to use this type of pattern associate in the transformation stage to create new vars, attributes, and cols to feed to the data warehouse?
3. Classifications
	1. Classification and label predictions
		1. Supervised learning, we know the label
		2. Consutruct models 
		3. describe and distinguish classes or concepts for future prediction
			1. classify countries based on climate, or classify cars based on gas milage
	2. Typical methods
		1. Description trees, Naive Baysian classification, support vector machines, rule based classification pattern based classification logistic regression
	3. Figure 1.2 in book
#### Cluster analysis
- Unsupervised Learning
- Group data to form new categories
- Principle: Maximize intra-cluster similarity & minimize inter-cluster similarity
- Many methods and applications
#### Deep learning
- Helps with the selection process, so we select the correct data columns that will yields the best predictions
- Especially helpful when there are hundreds or thousands of cols
#### Outlier analysis
- Outlier: A data object that does not comply with the general behavior of the data
- Noise or exception? - One persons garbage could be another persons treasure
- Methods: by product of clustering or regression analysis
- Useful in fraud detection and event analysis
#### Are all mining results interesting?
##### What makes a pattern/prediction interesting?
- Easily understood by humans
	- Decision trees vs. neural nets
- Valid on a new/test data with some degree of certainty
- Potentially useful
- Novel
- Validates a hypothesis
##### Is all mined knowledge interesting?
- one can mine lots of patterns and knowledge
- Some may fit only a certain dim space
- some may not be representative, may be transient
##### Can a data mining sys generate all of the interesting patterns/predictions?
- Refers to the completeness of data mining algorithms
- We might have too many patterns and predictions, but we don't want to overlook an important one
- need well defined measures and user provided constraints
##### Can a data mining sys generate only the most interesting pattern or prediction
- An optimization problem
- Evaluation of mined knowledge -> directly mine only interesting knowledge
	- Descriptive vs predictive
	- Coverage
	- Typicality vs, novelty 
	- Accuracy
	- Timeliness
##### How can we best visualize our results?

### Confluence of Multiple systems
Fig 1.4 in tb

Why?
- Tremendous amounts of data
	- Algorithms and hardware mush be scalable
- Sophisticated applications
- High dimensionality of data
- High complexity of data

Information C.I.A
Confidentiality
Integrity
Availability