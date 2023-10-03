---
tags:
  - project
  - sysnet
Course: Systems and Networks
---
- Multi-threaded collatz conjecture stopping time computation
- Think about how to reuse threads when they are done with their task
- Each thread grabs a number and increments the counter (possible race condition)
- the number of iterations it takes to reduce the number to 1 minus 1 is the "stopping time". i.e. 7 for a<sub>1</sub> = 3
- counter can be less than 500, maybe even smaller
- will need to get creative about the data type for the intermediate values because they can easily be greater than INT_MAX
- use the crono library to measure computation time
- lets generate a csv for the problem size and computation time to graph the results for the report as a histogram (R studio?? 👀)


