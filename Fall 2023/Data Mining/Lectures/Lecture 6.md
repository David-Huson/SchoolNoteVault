---
tags:
  - datamining
  - classnotes
Chapter: 2
Course: Data Mining
---
# Data Reduction Strategies
**Data Reduction** - obtain a reduced representation of the data set that is much smaller in volume but produces the same (or almost the same) analytical results

## Dimensionality reduction
- Avoid the [[curse of dimensionality]]
- help eliminate irrelevant features and reduce noise
- reduce time and space required in data mining
- Allow easier visualization
- 
### Mapping data to a new space
#### Fourier transform
process wave form data
#### Wavelet transform
- decompose a signal into different frequency sub-bands
- Applicable to _n_-dimensional signals
- Data are transformed to preserver relative distance between objects at different levels of resolution
- Allow natural clusters to become more distinguishable
- Used for image compression
- use hat-shape filters
	- emphasize region where points cluster
	- suppress weak info
- remove outliers
- detect arbitrary shaped signal
- most effective at low-dimensional data
##### Discrete
- for linear signal processing
- Method:
	- length must be integer power of 2
	- smoothing and difference functions
	- 

### Principal Component Analysis (PCA)
- m find a projection that captures the largest amount of variation in data
- the original data are projected onto a much smaller space, resulting in dim reduction
- we find the eigenvectors of the covariance matrix, and these define the new space
- only for numeric data
- Given N (2) data vectors, find *k*<=*n*  orthogonal vectors (*principal components*) that can be used to best represent the data
- normalize input data so each attribute calls within the same range
- Each input data (vector) is a linear combination of the k principal component vectors
- compute k orthonormal vectors 
- each data is a linear combination of the k principal component vectors
- the pc are stored in order of decreasing "significance"
- we can eliminate the weak components (low variance) using the strongest principal components, it is possible to reconstruct a good approximation of the original data
### Attribute Subset Selection
- remove redundant and irrelevant attributes
- redundant
- irrelevant data
	- data that is not relevant to the data mining task at hand
	- ex. IDs are not relevant to the task of predicting GPA
		- mode of the IDs is always 1
### Attribute Creation (Feature Generation)
- 
## Numerocity reduction
- Reduce the data vol by choosing a smaller form of data representation
- Parametric methods
- nonParametric methods
#### Regression analysis
- a collective name for techs for the modeling and analysis of numerical data consisting of values of a **dependent variable** (also called a *response variable* or *measurement*)and of one or more *independent variables* (aka *explanatory* or *predictive* variables)
- Linear Regression
- Multiple regression
- Log-linear models
### Histogram analysis
- equal frequency
- equal depth
### Clustering
- partition data set into clusters based on similarity, and store clearest rep only
- can be very effective if data is clustered but not if data is "Smeared"
- can have hierarchical
### Sampling
- obtaining a small sample s to represent the whole data set N
- allow a mining algorithm to run in complexity that is potentially sub-linear to the size of the data
- Key principle: choose a *representative* sample
- **simple random sampling**
	- there is an equal probability of selecting any particular item
- **sampling without replacement**
	- once an object is selected, it is removed from the population
- **sampling with replacement**
	- once an object is selected, it is returned to the population
- **stratified sampling**
	- partition the data set and draw samples from each partition (proportionally, i.e., approximately the same percentage of the data)
	- used in conjunction with skewed data
## Data Compression
### Lossless
### Lossy
- String compression
- Audio/video compression
- Time sequence is not audio
- Dimensionality and numerosity reduction can also be considered data compression
# Data Transformation
- A function that maps the entire set of values of a given attribute to a new set of replacement values st each old value can be identified with one of the new ones
- Very sensitive to outliers
## Min-max normalization
- to [new<sub>min<sub>a</sub></sub>,new<sub>max<sub>a</sub></sub>]
- Ex. Let income range $12,000 to $98,000 normalized to [0.0, 1.0]
$$
v' = \frac{v-min_a}{max_a-min_a})(new_{max_a}-new_{min_a})+new_{min_a}
$$
## Z-Score normalization
$$
v' = \frac{v-\mu_a}{\sigma_a}
$$

## Normalization by Decimal Scaling
$$
v'=\frac{v}{10^j}; \text{where j is the smallest integer such that } Max|v'| < 1
$$
# Discretization
- Divide the range of a continuous attribute into intervals
	- Interval labels can then be used to replace actual data values
	- Reduce data size by discretization
	- reduce cardinality
	- Supervised vs. unsupervised
	- split vs merge
	- can be done recursively
	- prepare for further analysis (classification)

- Equal-width binning
	- divide the range into N intervals of equal size
	- skewed data is not handled well
	- outliers dominate presentation
- Equal depth binning