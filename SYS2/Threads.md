
# Threads

## Process Model
- Each thread has its own user & kernel stack
- Multi-threads share PCB and User address space

## Implementation
- User level threads: Provides API with no kernel support: local function call (no sys call)
- Implements kernel library supported directly by the [[Operating System]]
	- requires a system call



## User-Level Threads (ULT)
> ##### ULTs are mapped to a single kernel thread, whilst kernel threads are mapped as individual threads on a kernel level

- [[Kernel]] not aware of thread activity but still managing process activity
- When thread makes system call, whole process will be blocked except the thread who made the call
	- **thread states independent from running states**
- Thread library provides schedulers for a thread to the kernel scheduler



### Thread process model
- For a multi-tthread, kernel stack are shared as system calls block other threads

## Kernel level threads (KLT)
### Advantages
- Kernel can simultaneously schedule many threads of the same [[Processes]] on many processors
- Blocking is done on a thread level
- Kernel routines can be multi-threaded

### Disadvantages
- Thread switching within the same process involves kernel — so more overhead

