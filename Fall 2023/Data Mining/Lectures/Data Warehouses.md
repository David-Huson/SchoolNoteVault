not rigorously defined
- A decision support db that is maintained separately from the organization's operational database
- Support info processing by providing a solid platform of consolidated, historical data for analysis
- A subject-oriented, integrated, time-variant, and nonvolatile collection of data i support of management's decision making process
### Subject oriented
- Organized around major objects such as a customer, product, sales (entities)
- Focusing on the modeling and analysis of data for decision maker, not on daily ops or transaction processing
- provide a simple and concise view around particular subject issues by excluding data that are not useful in the decision support process
### Integrated
- constricted by integrating multiple, heterogenous data sources
- data cleaning and data integration techs are applied
	- ensure consistency in naming conventions, encoding structures, attribute measures, etc
### Time variant
- The time horizon for the data warehouse is significantly longer than that of operational systems
	- operational database: current value data
	- Data warehouse: provide historical data
- every key structure in the data warehouse
	- contains an element of time (explicitly or implicitly)
	- but the key of operational data may or may not contain "time element"
### Nonvolatile
- a physically separate source of data transformed from the operational environment
- operational update of data does not occur in the data warehouse environment