saving everything in the process control block, loading the next process' PCB, and allocating all space on the stack

When process P<sub>i</sub> is removed from CPU
- Register values stored in the PCB<sub>i</sub>
- PC stored in PCB<sub>i</sub>
- PCB<sub>i</sub> state changed to ready, terminated, waiting
- Kernel schedules next process
	- May be the same process over again
		- e.g. Mouse moving
	- Still follows same rules
- When Process P<sub>j</sub> is returned to the cpu
	- register values restored from PCB<sub>j</sub>
	- PCB<sub>j</sub> state changed to *running*
	- CPU mode changed to User-mode
	- PC copied from PCB<sub>j</sub> to CPU
		- j back to process
		**- Last thing to happen**
