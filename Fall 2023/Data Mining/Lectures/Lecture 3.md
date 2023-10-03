---
Course: data mining
Chapter: 2
tags: classnotes, datamining
---
# Chapter 2: Data, Measurements, and Data Processing

## The 7 V's of data

### Volume
- The amount of data **in bytes**
- has increased exponentially over the past few years
- increases in volume are due to the Internet and mobile device revolutions (IoT)
	- Online commerce
	- social medial
	- sensore data
### Velocity
- The speed at which the data is created, processed, stored and analyzed
- Batch processing at regular intervals was the norm
- Increasing data velocity is requiring the need for more real-time processing
	- Real-timesSentiment analysis
### Variety
- The differing data formats
	- Structured
	- Unstructured
### Variability
- Data who's meaning is constantly changing
- Used in sentiment analysis of social media
- Need to understand the context of the data
### Veracity
- Accuracy of the data, conformity to facts, truth
> The "I" in data C.I.A.
- Financial transactions are usually the **most accurate**
- Sensor data is some of the **most inaccurate**
	- prone to noise and errors
	- prone to failure
- Decision support systems need accurate data
	- Important in [[Data Warehouses]]
### Value
- What is the worth of the information in the data?
- Data is valuable for 
	- Decision making
	- cost management
	- Targeted marketing 
	- Criminal Activity
	- Espionage
- Good data can save money
- Bad data can cost money
- Data alone has little value without comprehensive analysis
### Visualization
- displaying the data in an informative manner
	- concise
	- accurate
	- easy to understand
- Need to display multidimensional data in a two-dimensional space

## Data Visualization
Why visualization?
- Gain insight into an information space by mapping data onto graphical primitives (lines, points, shapes, etc.)
- Provide qualitative  overview of large data sets
- search for patterns, trends, structure, irregularities, relationships
- help find interesting regions and suitable parameters for further quantitative analysis
- provide a visual proof of computer representations derived
- Cardinality = the number of unique values
	- low cardinality is desired to increase performance of analysis

## Data Types
- Relational records
- files
- data matrix
- document data
	- text documents
	- term-frequency vector
- transaction data
- Graph and network data
- Ordered
	- video data
	- temporal data
	- sequential data
	- genetic sequence
- Spatial, image, multimedia
### Data Objects
- Data sets are made of up data objects
- a data object represents and **entity**
- also called samples, examples, instances, data points, objects, and tuples
- examples:
	- **sales database**: customers, store items, sales
	- **medical database**: patients, treatments
- are described by **attributes**
- rows -> objects
- cols -> attributes
- Attributes, dimensions, features, variables: a data field, representing a characteristic or feature of a data obj
	- customer_id, name, address, gender, marital status, etc.

### Nominal
- categories, states, or "names of things"
- Hair_color = {auburn, black, blond, brown, grey, red, white}
- marital status, occupation, ID numbers, zip codes, gender
- Numbers can be nominal when we do not use them for mathematical calculations
- **Preferred GUI objects**: Drop down list or radio button
	- Text boxes can introduce errors
### Binary
- nominal attribute with only 2 states (0 or 1)
- could be called boolean, or bit
- Symmetric data: both values equally important or populated
- Asymmetric binary: values are not equally important or populated
	- medical test (positive vs. negative); convention: assign 1 to most important outcome (e.g. HIV positive, Zika positive, malignant tumor)
- 
### Numeric/quantitative
#### Interval-scaled
#### Ratio-scaled

