---
date created: 2021-11-16 15:51
date updated: 2021-11-16 16:20

---

# Concurrency

> Two or more processes can cooperate, a process can be forced to stop until it receives a signal

## Semaphore

> An integer value used for signalling among processes

Operations:

- Initialize
- Decrement: May result in blocking a process (entry [[Synchronization#Critical Section | critical section]] call)
- Increment: May result in unblocking process (exit CS call)

> Value must be > 0

### Binary Semaphore

> Initialized at 0 or 1

semWaitB

- value = 0: process blocked, adds to queue
- value = 1: value = 0 and process continues execution

semSignalB

- Checks if any other process blocked by semaphore
  - Unblocks process
  - Adds to queue
- If no processes blocked, value = 1

## Mutex

> Process that locks the mutex must be the one to unlock it

## Monitor Variables

- Local data variables accessible only by the monitors procedures
- Process enters the monitor by invoking one of its procedures
- Only one process may be executing in the monitor at a time

### Condition Variables

- Special data type in monitors

- cwait(c): Suspend execution of calling process on condition c
  - Monitor available for use by another process

- csignal(c): Resume execution of some process blocked after a cwait on condition
  - If multiple processes, choose one of them, if none, do nothing
