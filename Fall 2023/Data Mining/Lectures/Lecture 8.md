---
tags:
  - classnotes
  - datamining
Chapter: 3
Course: Data Mining
---
# [[Data Warehouses]]
## 3 -tier architecture
1. Front end tools
2. OLAP
3. Data warehouse server

## High level data warehouse/business intelligence system architecture model
### [[Source systems]]
### Back Room
Extract Transform and / Load System (ETL)
- extract
- clean
- conform
- deliver
- ETL Management Services
- ETL Data stores
Presentation server
### Front room
Presentation server
- atomic business process dimensional models with aggregate nav
- conformed dimensions/facts 
- data cube
- Business Intelligence applications
- - queries
- standard reports
- analysis app
- dash
- operational BU
- datamining models
- BI portal
BI Management Services
BI Data Store

# [[Data Lake]]

## Three DW models
1. Enterprise warehouse
	1. collects all of the information about subjects spanning the entire organization
	2. can be time consuming to construct
	3. build from the bottom up (Ralph Kimball)
		1. start with a small portion and allow the client to ask for more
		2. quicker
	4. build from the top down(Bill Inmon)
		1. build all processes first
		2. time consuming
2. Data Mart
	1. a subset of corporate-wide data that is of value to a specific group of users
3. Virtual warehouse
	1. a set of views over operational databases
	2. some of the possible summary views may be materialized
	3. more cost effective

## [[Data Cube]]
#### Typical OLAP operations
- Dicing a cube
	- Creating a smaller cube from the original
	- 