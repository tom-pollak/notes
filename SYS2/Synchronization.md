---
date created: 2021-11-01 13:54

---

# Synchronization

## Concurrency

- Allowing more than one process to make progress at a time
- Basic requirement: enforce **mutual exclusion**

## Race Condition

> Multiple [[Processes]]/ [[Threads]] read and write data so that the final result depends on the order of execution of instructions in the multiple processes

- Two processes are creating child processes using fork()
- Race condition on kernel variable _next_available_pid_
- Mechanism needed to prevent $P_0$ and $P_1$ from accessing variable as same PID could be assigned to two different processes

## Critical Section

- System of $n$ processes
- Each of the processes has critical section segment of code
- When one process in critical section, no other may be in critical section
<br>
- Each process must ask permission to enter critical section in **entry section**, may follow critical section with **exit section**, then **remainder section**


### Requirements

- **Mutual Exclusion**: If process $P_i$ is executing critical, no other process may execute critical
- **Progress**: If no process is executing in its critical section and there exist some processes that wish to enter critical, then the selection of the process that will enter next cannot be postponed indefinitely
- **Bounded Waiting**: A bound must exist on no of times that other processes are allowed to enter their critical section and before that request is granted
	- Assume process is executing at nonzero speed
	- No assumption concering relative speed
	- Stops *starvation*: at some point $P_i$ must enter CS

## Mutual Exclusion

### Implementation