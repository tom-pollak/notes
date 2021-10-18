
# Threads
> #### Stream of executions sequentially — lightweight process (LWP)
> - Processes may have many threads

## Process Model
- Each thread has its own user & kernel stack
- Multi-threads share [[Processes#Process Control Block | PCB]] and User address space

### Thread Control Block
> - Contains information similar to [[Processes#Process Control Block | PCB]]
> - Also contains: Thread ID, priority and parent process ID


## Single & Multi-threaded [[Processes]]
> #### Shared [[Processes#Process Control Block | PCB]] and [[User Address Space]]

## Threads Implementation
> - Thread library provided by [[API]]
> - Entirely in user space — no kernel support
> - Kernel level library implemented by [[Operating System | OS]] — exists in kernel space

## User-Level Threads
> ##### ULTs are mapped to a single kernel thread, whilst kernel threads are mapped as individual threads on a kernel level
>  - [[Kernel]] not aware of thread activity but still managing process activity
> - When a thread makes a system call, the whole process will be blocked except the thread who made the call
>	- **Thread states independent of running states**
>	- Thread switching does not require kernel mode privileges

- Provides API with no kernel support: local function call (no sys call)
- Implements kernel library supported directly by the [[Operating System]]
	- Requires a system call
- Thread library provides schedulers for a thread to the kernel scheduler

> Kernel can only assign processes to processors - two threads within the same process cannot run simultaneously on two processors

### Thread process model
- For a multi-tthread, kernel stack are shared as system calls block other threads

## Kernel level threads
> No thread libary but an API (system calls)
> 
### Advantages
- Kernel can simultaneously schedule many threads of the same [[Processes]] on many processors
- Blocking is done on a thread level
- Kernel routines can be multi-threaded

### Disadvantages
- Thread switching within the same process involves kernel — so more overhead
