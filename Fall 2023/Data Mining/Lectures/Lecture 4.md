---
Course: Data Mining
Type: Class Notes
tags: datamining, classnotes
---

Continuing where we left off in [[SchoolNotesVault/Fall 2023/Data Mining/Lectures/Lecture 3|Lecture 3]]

### Graphical Excelence
- Americans with Disabilities Act (ADA) compliance
	- alt text
	- patterns with colors
- Is the visualization repeatable programmatically?
- Is the visualization still excellent when the data values change?
	- Limits on axes' min and max values
	- Limits on number of categories to be displayed
## [[SchoolNotesVault/Fall 2023/Data Mining/Lectures/Lecture 3#Binary|Binary Data]]
- Preferred GUI element: Check box

## Ordinal Attribute Types
- Values have a meaningful order (ranking) but magnitude between them is not known
	- Size
	- Grades
	- Military Rankings
- Preferred GUI Object
	- Dropdown list or Radio button
## Numeric Types
- Quantity
- **Interval Scaled**
	- Measured on a scale of **Equal sized units**
	- values have order
	- no true zero point
	- Preferred GUI object
		- Numeric up/down
	- Date/Time picker
- **Ratio Scaled**
	- Inherent zero point

## Discrete vs. Continuous
### Discrete
- Has a **finite** or **countably infinite** set of values
	- zip codes, professions, ids
- Sometimes represented as integers
- Binary attributes are a special case of discrete attributes

### Continuous
- Real numbers
	- temp, height, weight, price
- Practically, real values can only be measured and represented using a finite number of digits
- Continuous attributes are typically represented as floating-point variables
## Dates
- can be difficult to manage because systems handle and process datas differently
	- Formatting
	- Storage
	- Functions
- can be nominal or interval scaled
- elements can be extracted as numbers then used n calculations
- hierarchical
- Date/Time picker can reduce formatting errors, but not necessarily data entry errors
	- need value checking

# Statistics of Data
- **Motivation**: to better understand the data: central tendency, variation, and spread

#### Measuring the central tendency
- Mean
- Median
- Mode

#### Measuring the dispersion
- Range
- Quantiles
- Percentile(100 quantile)
- Quartile (4 quantile)
- inter quartile range
	- Q3 - Q1

[[Data Mining Concepts and Techniques.pdf|Box plots]]
#### Measuring variation
- standard deviation
- covariance
$$
Cov(A,B)=E(A\cdot{B})-\overline{A}\space\overline{B}
$$
- correlation coefficient
- Chi squared test
	- when chi squared is 0, this means the data is redundant
	- 
#### Measuring spread

