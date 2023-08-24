#Textbook #Reading

# Chapter 1
- [[Operating System]] - a system that manages a computer's hardware
	- provides a basis for application programs and acts as an intermediary between the **user** and the [[#Hardware]]
	- allocates resources to programs

## Topics to be discussed in later chapters
[[data structures]]
[[computing environments]]
[[open-source and free operating systems]]

## Objectives
- Describe the general organization of a computer system and the role of interrupts
- Describe the components in a modern multiprocessor computer system
- Illustrate the transition from user mode to kernel mode
- Discuss how operating systems are used in various computing environments 
- Provide examples of free and open-source operating systems 
## What do operating systems do
- a computer system can be divided into roughly four components:
	- [[#Hardware]]
	- [[#operating system]]
	- [[#Application Programs]]
	- [[#User View|user]]

### Hardware
provides basic computing resources for the system
Examples:
- CPU (central processing unit)
- memory
- IO devices
### Application Programs
- word processors
- spreadsheets
- compilers
- web browsers
define ways in which these resources are used to solve the [[#User View|user]]'s computing problems

The operating system controls the hardware and coordinates its use among the various application programs for the various users.

The computer system can also be divided into the [[#Hardware]], [[#Software]], and [[#data]].  It simply provides an **environment** within which other programs can do useful work.

## User View
The user's view of the computer varies according to the interface being used. In the case of the average user and their pc, the goal is to maximize the work (or play) they can perform, so the operating system is designed mostly for [[ease of use]], with some attention paid to performance and security and none paid to [[resource allocation]] -- how various hardware and software resources are shared.

![[Pasted image 20230816180443.png]]

Mobile devices are beginning to replace laptops and desktops for some users. These devices are typically connected to networks through cellular or other wireless technologies. The UI for mobile computers generally features a **touch screen** instead of a physical keyboard and mouse. 

Some computers have little to know user view, such as [[embedded computers]] in home devices and automobiles, which may have numeric keypads or indicator lights, but they and their operating systems are designed primarily to run without user interaction.
## System View

An operating system is both a **resource allocator** and a **control program**.
A control program manages the execution of user programs to present errors and improper use of the computer, especially IO devices.

## Defining operating systems

There is no universally accepted definition of what is part of the operating system.\
The more common definition and one we normally follow is:

> the operating system is the one program running at all times on the computer -- usually called the **kernel**

Along with the kernel there are two other types of programs: **system programs**, which are associated with the operating system but are not necessarily part of the kernel, and **application programs**, which include all programs not associated with the operating system.

#### Operating system monopolies
in 1998 the US DOJ filed a suit against Microsoft claiming it was including too much functionality in its operating system which limited competition from application program vendors. They were found guilty.

Now we see a similar circumstance happening with mobile device operating systems. These systems often include not only a core kernel, but also **middleware** -- a set of software frameworks that provide additional services to application developers. 

For example: each of the two most prominent mobile operating systems -- Apple's iOS and Google's Android -- features a core kernel along with a middleware that supports databases, multimedia, and graphics (to only name a few).


### Summary
The operating system includes the always running kernel, middleware frameworks that ease application development and provide features, and system programs that aid in managing the system while it is running.

## Computer-System Organization

A modern general-purpose computer system consists of one or more CPUs and a number of device controllers connected through a common **bus** that provides access between components and shared memory ([[Figure 1.2.excalidraw|Figure 1.2]]).Depending on the controller, more than one device may be attached, a single USB port can connect to a USB hub with multiple device connections. A device controller maintains some local buffer storage and a set of special-purpose registers. The controller is responsible for moving the data between the peripheral devices it controls and its local storage buffer.

Typically operating systems have a **device driver** for each device controller. This driver understands the device controller and provides the rest of the operating system with a uniform interface to the device. 

The CPU and device controllers compete for memory cycles. To ensure orderly access to the shared memory, a memory controller synchronizes access to memory.

## Interrupts

The controller informs the device it has finished an operation via an **interrupt**.
### Overview

Hardware may trigger an interrupt at any time by sending a signal to the CPU, usually by way of the **system bus** (the main line of communication between the CPU and the major components).

When the CPU is interrupted, it stops what it is doing an immediately transfers execution to a fixed location, this location typically contains a starting address where the service routine for the interrupt is located. The interrupt service routine executes; on completion, the CPU resumes the interrupted computation. A timeline of this operation is shown below.

![[Pasted image 20230817202530.png]]

- Each computer design has its own interrupt mechanism, but several functions are common.
- This mechanism must transfer control to the appropriate interrupt service routine. 

- Interrupts mush be handled quickly, so a table of pointers to interrupt routines can be used to provide expedient.
- This table is typically stored as an array of addresses in low memory, and is known as the **interrupt vector**.
	- This array is indexed by a unique number, given with the interrupt request, to provide the address of the interrupt service routine for the interrupting device.
- The interrupt architecture must also save the state information of whatever was interrupted in order to restore this information after servicing the interrupt.
	- This responsibility is left to the interrupt routine, which must explicitly save the current state and then restore it before returning
- After the interrupt is serviced, the saved return address is loaded into the program counter, and the interrupted computation resumes as though the interrupt had not occurred

### Implementation

- The CPU hardware has a wire called the **interrupt request line** that the CPU senses after executing every instruction
- When the CPU detects a signal on the interrupt request line, it reads the interrupt number and jumps to the **interrupt-handler routine** indexed by that number on the interrupt vector
- The device controller *raises* an interrupt by asserting a signal on the interrupt request line
- the CPU *catches* the interrupt and *dispatches* it to the interrupt handler
- the handler *clears* the interrupt by servicing the device
![[Pasted image 20230818130543.png]]
This mechanism enables the CPU to respond to an async event, however, we need more sophisticated interrupt handling features in modern operating systems
1. We need the ability to defer interrupt handling during critical processing
2. We need an efficient way to dispatch to the proper interrupt handler for a device
3. We need multilevel interrupts, so that the operating system can distinguish between high- and low-priority interrupts and can respond with the appropriate degree of urgency

These features are provided by the CPU and the **interrupt-controller hardware** in modern computer hardware.

Two interrupt request lines:
- **non-maskable interrupt**: reserved for events such as unrecoverable memory errors
- **maskable**: it can be turned off by the CPU before the execution of critical instruction sequences that must not be interrupted
	- used by device controllers to request service

We use **interrupt chaining** to address the issue of there being more devices and interrupt handlers than address elements available for the interrupt vector to index.

**Index Chaining**: each element in the interrupt vector points to the head of a list of interrupt handlers.

When an interrupt is raised, the handlers on the corresponding list are called one by one.

The interrupt mechanism also implements a system of **interrupt priority levels** which allow the CPU to defer the handling of low-priority interrupts without masking all interrupts and makes it possible for high-priority interrupts to preempt the execution of a low-priority interrupt.

### Storage Structure

The CPU can only load instructions from memory, so programs must be loaded into memory to run