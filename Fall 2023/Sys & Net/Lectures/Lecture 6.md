---
tags:
  - classnotes
  - sysnet
Chapter: 4
Course: Systems and Networks
---

# Background
Allowing the process to continue without checking on it


# Threads
- A lightweight process, representing a single unit of program execution within a process
	- shares code, data & file descriptor table
	- has individual stack, registers & thread control block (TCB) within the PCB
- A process may run multiple threads concurrently
