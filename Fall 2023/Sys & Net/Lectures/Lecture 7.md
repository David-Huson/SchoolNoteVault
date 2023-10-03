# Threading
## Two Types of Threads
- user level
- kernel level

Thread creation similar to process creation except:
- processes begin execution at main()
- Thread begins execution at specified function
- Creating call identifies initial function
## Multithreaded programing
- multiple threads may be executed simultaneously in a single process
- threads share **code, global data, and open files**
- the **stacks are different** from other threads
- on creation the TCP is updated, but PCB is not
- need to setup stack and TCP for each new thread within a single process
- if a memory error or interrupt is sent to a thread, the whole process is terminated
	- In Java we just throw and catch an exception
- TCB is in the kernel
## Processes vs Threads
- Threads share process resources
- Processes share computer resources
- Operating system maintains per thread
	- PC
	- stack
	- state
	- reg
- Operating system maintains per process
	- address space
	- list of open files
	- child processes
	- signals and signal handlers
	- accounting
- states that pertain to process only
	- Start
	- Terminate
## Benefits of MT programming
- Threads are more responsive than processes
- Threads share resources
- Threads are more economical than processes
## Multithreading Models
- Many to one model: many user level threads map to one kernel thread
	- if a single thread makes a blocking call, all threads are blocked
	- each thread is created in user-space
	- used in earlier systems due to the limitations to the number of kernel threads available
- One to one model: a user level thread maps to a single kernel thread
	- provides  more concurrency
	- more overhead to create a new user thread
	- can only create as many user level threads as there are kernel threads available
- Many to many: many user level threads to many kernel threads
	- combines advantages of one to one and one to many models

## Creating a Thread in C
- Define a function for the thread
	- the AR for function pushed onto the thread stack
	- thread terminates when function returns
## Timeline
- t<sub>a</sub> = arrival time
	- process arrives at fork
- t<sub>e</sub> = execution time
- t<sub>d</sub> = departure time
- response time = t<sub>e</sub> - t<sub>a</sub>
	- fastest possible user-observable reaction
- turnaround time = t<sub>d</sub> - t<sub>a</sub>
	- press enter until prompt returns
	- enter system until exit system