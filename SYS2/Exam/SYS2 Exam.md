---
date created: 2022-01-11 12:53
date updated: 2022-01-11 20:11

---

# Exam

_Y3891128_

## 1.

### 1.i

A process can use a system call as an API to access hardware. They can use this API to access functionality not available in the user space. A process can change its own state with a system call such `exit`, where a process can terminate its own execution, therefore changing the state.

### 1.ii

I would use a micro kernel approach, where you design it as such to move as many components from the kernel to the user space as possible. This can be easier to extend than a monolithic or layered kernel as new or changed functionality can be implemented as a module in the user space.

The micro kernel is also more reliable and secure as much of the code is in the less privelidged user space. However there is a overhead when the user space interacts with the kernel space.

## 2.

### 2.i

The process will have a total of 3 program counters and user stacks, private to each thread (main thread and the two newly created threads).  Each thread shares the same common heap from the process. A process will have a private heap from other processes.

### 2.ii

2 processes are created, the values of the return id are the id of the forked process and 0. The value of i is 15 in both processes.

# show ur working

## 3.

### 3.i

![[sheduling-gantt.png]]

### 3.ii

| Process | Turnaround Time |
| ------- | --------------- |
| P1      | 6               |
| P2      | 20              |
| P3      | 1               |
| P4      | 8               |
| P5      | 13              |
| P6      | 14              |

### 3.iii

| Process | Waiting Time |
| ------- | ------------ |
| P1      | 1            |
| P2      | 17           |
| P3      | 0            |
| P4      | 1            |
| P5      | 9            |
| P6      | 11           |

## 4.

# TODO

Using shared memory would be convient for sharing chunks of data, however would be insecure if the other computer was not trustable. This is because the computer could change the data on the memory to run malicious code on your computer.


Shared memory
- Area of shared memory among process that wish to communicate
- Under control of processes not OS
- Issue: provide mechanism allow the user processes to synchronize actions when they access shared memory
	- Race conditions

Message passing
- Communicate without resorting to shared variables
	- No sync issues
- operations: send(message) recieve(message)
- Bidirectional or unidirecitonal
- Synchronous or async
- Direct: must name each other explicitly
	- Link associated with exactly one pair of processes
	- Link established automatically
- Indirect: messages are directed and recieved from ports
	- processes can communicate if they share a port
	- each pair of proccesses may share several communication links


## 5.

### 5.i

If both processes are ran at the same time, neither would wait for $Sem1$ or $Sem2$ as the setting of the variable is after the critical section, therefore they would both try to set the variable $z$ at the same time, causing a deadlock.

### 5.ii

If one of the processes terminates while waiting, the other process will be indefinitely postponed when it reaches the wait section, as it will be waiting for a signal to $Sem$ that will never be sent as the other process has exited

### 5.iii

# TODO petersons algo?

```c
void increment() {
	Signal(Sem1); // (= 1)
	while(Sem2) {
		Signal(Sem1); // (= 0)
		/* delay*/
		Signal(Sem1); // (= 1)
	}
	z++;
	Signal(Sem1);a // (= 0)
}

void decrement() {
	Signal(Sem2); // (= 1)
	while(Sem1) {
		Signal(Sem2); (// = 0)
		/* delay*/
		Signal(Sem2); (// = 1)
	}
	z--;
	Signal(Sem2); // (= 0)
}
```

## 6.

### 6.i

**(a)**

| 7   | 2      | 3           | 1           | 2           | 5           | 3           | 4           | 6           | 7           | 7           | 1           | 0           | 5           | 4           | 6           | 2           | 3           | 0           | 1           |
| --- | ------ | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| 7   | 7<br>2 | 7<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>5 | 3<br>2<br>5 | 3<br>4<br>5 | 3<br>4<br>6 | 7<br>4<br>6 | 7<br>4<br>6 | 7<br>1<br>6 | 7<br>1<br>0 | 5<br>1<br>0 | 5<br>4<br>0 | 5<br>4<br>6 | 2<br>4<br>6 | 2<br>3<br>6 | 2<br>3<br>0 | 1<br>3<br>0 |
| F   | F      | F           | F           |             | F           | F           | F           | F           | F           |             | F           | F           | F           | F           | F           | F           | F           | F           | F           |


18 page faults, assuming populating the frames originally count as page faults

**(b)**

| 7   | 2      | 3           | 1           | 2           | 5           | 3           | 4           | 6           | 7           | 7           | 1           | 0           | 5           | 4           | 6           | 2           | 3           | 0           | 1           |
| --- | ------ | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| 7   | 7<br>2 | 7<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>3 | 1<br>5<br>3 | 1<br>5<br>3 | 1<br>5<br>4 | 6<br>5<br>4 | 6<br>7<br>4 | 6<br>7<br>4 | 6<br>7<br>1 | 0<br>7<br>1 | 0<br>5<br>1 | 0<br>5<br>4 | 6<br>5<br>4 | 6<br>2<br>4 | 6<br>2<br>3 | 0<br>2<br>3 | 0<br>1<br>3 |
| F   | F      | F           | F           |             | F           |             | F           | F           | F           |             | F           | F           | F           | F           | F           | F           | F           | F           | F           | F

18 page faults, assuming populating the frames originally count as page faults

### 6.ii

**(a)** The maximum number of frames and pages available can be calculated by dividing the size of the memory by the size of the page. The memory is 256 MB (256,000 KB) and the page size is 4 KB. This gives a total of **64000** pages or frames.

**(b)** The virtual address is 32 bits long or 4 bytes. The page table can take up a single virtual address minus the space taken up by the control bits (1 byte). Therefore, the maximum size of the page table is **3 bytes**.