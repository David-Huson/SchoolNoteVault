---
tags:
  - datamining
  - classnotes
Course: Data Mining
Chapter: 2
---
# Similarity and Dissimilarity 
## Similarity
- Value is higher when objects are more alike
- Cosine similarity
	- measures the similarity between two vectors of an inner product space
	- is measured by the cosine of the angle between the two vectors and determines if the vectors are pointing in the same direction
## Dissimilarity
-Value is lower when objects are more dissimilar

## Proximity
- can take 2 or more states
### Measurement methods
- Method 1
	- simple matching
	- use a large number of binary attributes creating a new binary attribute for M states
- contingency tables for binary data
	- confusion matrix in machine learning
- Jaccard coefficient
- We can discard fields where no information is gained (values are all the same across the attribute)
- Dissimilarity matrix
	- can use simple measure of the euclidian distance
		- further the distance, more dissimilarly the data points are
		- Minkowski distance
			- manhattan distance and euclidian distance are special cases of the Minkowski

# Data Quality, Cleaning
## Dirty Data
- incomplete
	- lacking attribute values, attributes, or only contains aggregate data
- noisy
	- contains noise, error, or outliers
- inconsistent
	- contains discrepancies in codes or name
	- discrepancies between duplicate records
- intentional
	- disguised missing data
### How to handle missing data
1. Ignore the tuple
	1. usually done when the class label is missing
2. Fill it in
3. A global constant
4. A measure of central tendency
5. the attribute mean for all samples belonging to the same class: smarter
6. the most probable value: inference-based such a sBayesian formula or decision tree

## Noisy Data
- how to handle it
	- Binning
	- Regressing
	- Clustering
	- Combined computer and human inspection


## Data Integration
Schema integration



