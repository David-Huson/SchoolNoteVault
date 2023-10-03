---
tags:
  - classnotes
  - dsa
Course: Data Structures and Algorithms 2
Chapter: 10
---
- Used to solve problems by trying out various options and undoing choices when they don't lead to a solution (dead-end)
- When a solution can be build incrementally and where you need to explore multiple paths to find the correct one
- When a dead end is reached, the algorithm backtracks and explores other paths

# Turnpike Reconstruction Problem
- Constructing the set of points from a given set of distances
	- Suppose we are given N points, located on the x-axis *x*
	- Let us further assume that x<sub>i</sub> = 0, and the points are given left to right
	- These N nodes determine N(N-1)/2 (not necessariy unique) distances 