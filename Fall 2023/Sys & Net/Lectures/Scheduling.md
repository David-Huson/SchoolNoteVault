---
tags:
  - classnotes
  - sysnet
Course: Systems and Networks
Chapter: 5
---
# CPU Scheduling Overview
- Allocate CPU to the next ready process
- Preemptive scheduling

# Scheduling Algorithms
## Goals
- Giving each process a fair share of CPU resources
- Ensuring that all policies are properly enforced
- keep all parts of the system equally busy
- Respond to user requests as quickly as possible
- Meet user expectations as best as possible
	- i.e running and getting feedback from as many programs at the same time as possible
- Real time systems
	- meeting scheduling constraints to ensure timely responsiveness

Always schedule I/O bound tasks first because t is already penalized by read/write times
- I/O scheduled, starts I/O, blocked
- When I/O blocked, schedule compute
- utilize multiple components
- Better average **turnaround time**
 
## Optimization Criteria
Goal: Keep CPU as busy as possible
- Minimize waiting time
	- wait = sum of times process is in ready queue
		- total time in the ready queue
- minimize response time:(t<sub>e</sub>-t<sub>a</sub>)
- minimize turn-around time: (t<sub>d</sub>-t<sub>a</sub>)
- Maximize throughput
	- throughput - # jobs per unit time
	- throughput = a/turnaround time
	- minimize turnaround -> maximize throughput
- Fairness
	- usually a tradeoff
## Classes of Resources
- Preemptive
	- can take resource away at any time
	- control passes back to kernel
	- Internal and external events can cause
		- internal: `yield()`, `exit()`, etc
		- External: Quantum expiration, interrupt
- Non-preemptive
	- Cant take resource from process
	- process voluntarily gives up resource
	- External events not allowed
		- No quantum expired
	- Only internal events can cause
		- System calls: `yield()`, `exit()`
	- CPU: *"Run till done"*

### FIFO
- Non-preemptive
- 1st on CPU, when done, 2nd on CPU
- simple to implement **+**
- Little overhead(no switching)**+**
- short jobs stuck behind long jobs **-**
- Subject to the "**Convoy effect**"
### Round Robin
- Preemptive version of FIFO
- Ready list is queue
- Quantum used to generate interrupts
	- Relatively simple **+**
	- Fair: each job gets quantum **+**
	- Quantum size is tricky to choose **-**
	- more overhead than FIFO **-**
- Assumptions: Quantum = 2, Switch = 1


