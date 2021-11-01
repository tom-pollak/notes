---
date created: 2021-10-19 15:16
date updated: 2021-10-20 15:49

---

# Scheduling

> **[[Synchronization#Concurrency | Concurrency]]:** Concurrent system supports more than one task, allowing all tasks to make progress
>
> - Single core splitting tasks — better response time

> **Parallelism:** Parallel system perform more than once task simultaneously
>
> - Multicore async

## Program Execution Pattern

- Cycle of CPU doing computation and waiting for I/O of some kind (read, write file)
- Scheduling system allows one process to use CPU while another waits for I/O
- **Challenge:** make system as 'efficient' and 'fair' as possible
  - Varying and dynamic conditions
- I/O doesn't take CPU time as it only takes secondary controller and memory to write and read files — CPU just tells them where to find the data

| Sequential intructions                              |
| --------------------------------------------------- |
| _load_ store <br> _add_ store <br> _read_ from file |
| **wait for I/O**                                    |
| _store_ increment index <br> _write_ to file        |
| **wait for I/O**                                    |
| _load_ store <br> _add_ store <br> _read_ from file |
| **wait for I/O**                                    |

## Parallelism

### Exploiting parallelism

> Can give each of the independent tasks to different threads
>
> - Quicker than running commands sequentially

#### Amdahl's Law

> Identifies **performance gains from adding additional cores** to an application that has both serial and parallel components

$speedup \leq \dfrac{1}{S+\dfrac{1-S}{N}}$

- $S$: Serial portion
- $N$: Processing cores

<br>
- If application is 75% paraell / 25% serial, moving from 1 to 2 cores results in speedup of 1.6
- as $N \rightarrow\infty$, $speedup \rightarrow 1/S$

## CPU Scheduler

> Selects processes ready in queue, allocates CPU core to one of them

Uses scheduling metrics and optimization criteria:

- **CPU utilization:** Keep CPU as busy as possible
- **Max Throughput:** No of processes that complete their execution per time unit
- **Max Turnaround time:** Amount of time to execute process
- **Waiting time:** Amount of time process has been waiting in ready queue
- **Response time:** Amount of time it takes from when request submitted to first response produced

### Scheduling Categorization

- **Min Preemptive Scheduling:** Scheduler interrupts the task that is running on the CPU during its burst time when the task's allocated CPU time slot is over
  - All modern [[Operating System | Operating Systems]] use min preemptive
- **Non-Preemptive Scheduling:** Scheduler doesn't interrupt the task that is running on CPU during its burst time, task continues running until CPU burst over, or it terminates

## Dispatcher

> Gives control of CPU to process selected by CPU scheduler

- Switching context
- Switching to user mode
- Jumping to proper location in user program to restart that program

**Dispatcher latency:** Time taken for dispatcher to stop one process and start another running

## Algorithms

### First Come First Serve

> ###### Convoy effect: When one CPU intensive [[Processes | process]] blocks the CPU, a number of I/O intensive processes can get backed up behind it, leaving the I/O devices idle.

- When CPU burst ends, I/O processes pass through CPU quickly leaving CPU idle for while everyone queues up for I/O
- Cycle repeats every time CPU intensive process
- Not an effective use of CPU

### Shortest Job First

> ##### Each process with length of its next CPU burst

- SJF is optimal — minimum avg waiting time for a given set of processes
- How to estimate CPU burst time

### Shortest Remaining Time First

- Add varying arrival times and pre-emption to analysis

### Round-Robin

> CPU bursts **assigned with limits** — time quantum
>
> - Can be implemented as FCFS or SJF

- If a process takes longer than time quantum, it is moved to the back of the queue
- Maintained as a circular queue
- q should be large compared to context switch time
- q usually 10ms — 100ms
- Slightly higher avg time than SJF, but has better response time

### Priority

- More general case than SJF
- Each job assigned a priority
- Can suffer from **indefinite blocking**, or **starvation** where low-priority task can wait forever because there are always other jobs around with higher priority
  - Either run when load lightens or gets lost when system shuts down or crashes
- Solution is **ageing**: priority of jobs increase the longer they wait
  - Eventually get priority high enough that they run

#### Round-Robin Implementation

- Processes with same priority run round-robin
