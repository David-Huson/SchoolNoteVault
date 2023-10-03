---
Course: Data Structures and Algorithms 2
tags: classnotes, dsa
---

Reviewed math from the [[Chapter 1#Maths review|math review]]
The base of the logarithm does not matter in algorithm analysis, similar to how O(2n) => O(n). We ignore the base. O(log(n)) == O(log_2(n))


Performance eval is divided into 2 approaches
- priori estimates (O(n) estimation)
- posteriori testing
	- empirical observation, machine dependent


# Amortized Complexity
- a worst case operation can alter the state of a data structures such that the worst case cannot occur again for a long time, thus we can "amortize" the cost of the worst case operation over many less expensive operations
- Techs
	- Aggregate analysis
		- Add up the total cost on _n_ operations
		- Divide by the number of operations _n_
	- potential method
		- determine a cost function C that can be applied to each op
			- fast ops are "overcharged" 
			- slow operations are undercharged
			- the cost function mush overcharge the fast ops enough to pay for the expensive ones
		- potential - reserves available from over charging the fast operations
		- an accounting device to help us keep track of the state of the competition as part of determining the amortized cost
	$$
	T_{amortized} = T_{actual} + \Delta Potential
	$$
