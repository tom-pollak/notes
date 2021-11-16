---
date created: 2021-11-01 13:54
date updated: 2021-11-16 12:32

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
  - Stops _starvation_: at some point $P_i$ must enter CS

## Mutual Exclusion

### Implementation

1. Leave responsibility to processes that wish to execute concurrently
   - Would be required to coordinate with each other
2. Special purpose machine instructions
3. Support within the OS or programming language

### Hardware Support

**Atomic Operation:** Function implemented as a sequence of instructions that appears to be indivisible.

- No other process can see an intermediate state or interrupt the operation
  - Must execute as a group or not at all
- Guarantees isolation from concurrent processes

**Interrupt Disabling:** Uniprocessor system, concurrent processes cannot have overlapped execution, only _interleaved_

- The process will continue to run until it invokes an OS service or is interrupted

#### Special Machine Instructions

- Multiple processors share access to common main memory
- At a hardware level, access to a memory location excludes any other access to that memory location

##### Compare & Swap Instruction — LOOK UP

- Checks \*word is still what the system thinks it is (_testval_), so no process has changed it

```c
int compare_and_swap(int *word, int testval, int newval)
{
	int oldval;
	oldval = *word;
	if (oldval == testval) *word = newval;
	return oldval
}
```


##### Exchange Instruction

```c
void exchange(int *register, int *memory)
{
	int temp;
	temp = *memory;
	*memory = *register;
	*register = temp;
}
```

### Peterson's algorithm

> #### What is the while(true) for??

```c
boolean flag[2] = {false, false}; /* Sets process as active (progress) */
int turn; /* Decides whos turn (mutal exlusion) */
void P0()
{
	while (true) { /* What is this for?*/
		flag[0] = true; 
		turn = 1; /* Set other processes turn first to check if there are any other active processes first */
		while (flag[1] && turn == 1) /* Do nothing */
		/* Critical Section*/
		flag[0] = false;
		/* remainder */
	}
}

void P1()
{
	while (true) {
		flag[1] = true;
		turn = 0;
		while (flag[0] && turn == 0) /* Do nothing */
		/* Critical Section*/
		flag[1] = false;
		/* remainder */
	}
}

void main()
{
	parbegin(P0, P1);
}
```
