# Scheduling

## First Come First Serve
> ###### Convoy effect: When one CPU intensive [[Processes | process]] blocks the CPU, a number of I/O intensive processes can get backed up behind it, leaving the I/O devices idle.

- When CPU burst ends, I/O processes pass through CPU quickly leaving CPU idle for while everyone queues up for I/O
- Cycle repeats every time CPU intensive process
- Not an effective use of CPU

## Shortest Job First
> ##### Each process with length of its next CPU burst
- SJF is optimal — minimum avg waiting time for a given set of processes
- How to estimate CPU burst time

## Shortest Remaining Time First
- Add varying arrival times and pre-emption to analysis

## Round Robin
> ##### CPU bursts assigned with limits — time quantum
> - Can be implemented as FCFS or SJF

- If a process takes longer than time quantum, it is moved to the back of the queue
- Maintained as a circular queue
- q should be large compared to context switch time
- q usually 10ms — 100ms
- Slightly higher avg time than SJF, but has better response time

## Priority

- More general case than SJF
- Each job assigned a priority
- Can suffer from **indefinite blocking**, or **starvation** where low-priority task can wait forever because there are always other jobs around with higher priority
	- Either run when load lightens or gets lost when system shuts down or crashes
- Solution is **ageing**: priority of jobs increase the longer they wait
	- Eventually get priority high enough that they run

### Round Robin Implementation
- Processes with same priority run round robin

## Inter-process communication
