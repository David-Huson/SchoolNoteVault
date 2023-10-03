---
tags:
  - classnotes
  - dsa
Chapter: 1
---
# Algorithm Analysis
## Priori Analysis (Asymptotic notation)
- Involves analyzing an algorithm's performance using asymptotic notation.
- Theoretical analysis
- absolute analysis
- approximate answers
- independent of language of compiler and hardware
- same analysis for all systems
- done before the execution of the algorithm
- cheaper than Posteriori Analysis
- Maintenance Phase is not required to tune the algorithm
## Posteriori Analysis 
- The assessment of an algorithm's performance based on its real running time in a real computing environment
- Empirical analysis
- It is dependent on language of compiler and hardware
- exact answer
- does not use asymptotic notations to represent time complexity
- different from system to system
- if the time taken by the program is less, then the credit will go to compiler and hardware
- it is done after execution of an algorithm 
- more costly than priori analysis because of requirement of software and hardware for execution
- Maintenance phase required to tune the algorithm

$$
\begin{flalign}
T(N)=O(f(N)) \Rightarrow \text{Growth of } T(N) \leq \text{ growth of }f(N)&&\\\\
\hline\\
T(N)=\Omega(f(N)) \Rightarrow \text{Growth of } T(N) \geq \text{ growth of }f(N)&&\\\\
\hline\\
T(N)=\Theta(f(N)) \Rightarrow \text{Growth of } T(N) = \text{ growth of }f(N)&&\\\\
\hline\\
T(N)=o(f(N)) \Rightarrow \text{Growth of } T(N) \lt \text{ growth of }f(N)&&\\\\
\hline\\
T(N)=\omega(f(N)) \Rightarrow \text{Growth of } T(N) \gt \text{ growth of }f(N)&&\\\\
\hline\\
\end{flalign}
$$
### Common orders
- Hashing function: O(1)
- Binary search: O(logn)
- Sequential Search: O(n)
- Quicksort: O(nlogn)
- Simple sorts: O(n<sup>2</sup>)
- Towers of Hanoi: O(2<sup>n</sup>)

## Amortized Analysis
> Membership fee of $60 per month, plus $3 every time you use the gym.
> Assume you visit the gym every day
> You pay $150 over 30 days, or an average of $5/month
> you are **amortizing** the monthly fee over the days of the month, spreading it out at $2/day

- Average monthly expense
- in an **amortized analysis** you average the time required to perform a sequence of data-structure operations over all the operations performed
- Assessing runtime:
	- Approach 1: 
		- Worst case for a sequence is the sum of all the worst cases for each individual operation
	- Approach 2:
		- Average complexity is the sum of the average complexity of an individual operation
	- Approach 3
		- Amortized complexity views what has happened so far
### Amortized Complexity
- Basic Idea:
	- a worst-case operation can alter the state of a data structure in such a way that the worst case cannot occur again for a long time
	- thus we can "amortize" the cost of the worst case operation over many less expensive operations
#### Aggregate analysis
- determines the upper bound T(n) on the total cost of a sequence of n operations, then calculates the average cost to be:
	- T(n)/n
- Example: adding an element to a dynamic array
	- Best Case: O(1)
	- Worst Case: O(size(list)) -> O(n)
- Relative frequency of each of these operations is a function of the increment in the vector size upon resize operation
- Assume: *we increase the size of the list by 1* each time it is full and an `add()` operation is needed
![[Pasted image 20230925162344.png]]
- Add up the total cost on *n* operations
	- Writing a value: 1
		- 1+1+1+1...->n
	- Moving a value: 1
		- Resizing operations will move existing elements from one array to another
			- n+n/2+n/4+...+1<=2n
		- Total = n + 2n = 3n
- Divide it by the number of operations *n*
	- 3n / n = 3 => amortized cost (using aggregate analysis) is 3
#### The Potential method
- estimates complexity as that level that keeps potential positive (aggregate charges are never too low)
- Approach: determine a Cost function C that can be applied to each operation
	- fast operations are "overcharged" - allowing the accumulation of credits for slow operations
	- Slow operations are "undercharged" (same cost for all, fast or slow)
	- The cost function must overcharge fast operations enough to pay for the expensive ones
- Potential
	- reserves available from overcharging the fast operations
	- an accounting device to help us keep track of the state of the computation as part of determining the amortized cost
- At each step:
$$
\begin{flalign}
T_{amortized} = T_{actual} + \Delta{Potential}&&
\end{flalign}
$$
- Example: adding an element to a dynamic array
	- Best Case: O(1)
	- Worst Case: O(size(list)) -> O(n)
- Assume: *we increase the size of the list by 1* each time it is full and an `add()` is needed
- Assume: *we double the size of the list each time it is full*
- Possible amortized costs:
	- `amCost(add(x)) = 1`
	- `amCost(add(x)) = 2`
	- `amCost(add(x)) = 3`
- Which is reasonable?
	- 3, because it never under estimates
#### Amortized Complexity
- The worst case cost of a sequence of operations on a data structure, not on any specific operation
- Amortized complexity is applicable if the worst case for an operation id different than the best case and the worst case cannot happen repeatedly
- Amortized bounds are weaker than corresponding worst case bounds
- Amortized bounds are generally stronger than the corresponding average case bounds
