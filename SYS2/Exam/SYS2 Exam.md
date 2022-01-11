---
date created: 2022-01-11 12:53

---

# Exam

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
Using shared memory would be convient for sharing chunks of data, however would be insecure if the other computer was not trustable. This is because the computer could change the data on the memory to run malicious code on your computer.

Message passing

## 5.

### 5.i

If both processes are ran at the same time, neither would wait for $Sem1$ or $Sem2$ as the setting of the variable is after the critical section, therefore they would both try to set the variable $z$ at the same time, causing a deadlock.

### 5.ii

If one of the processes exits while waiting, the other process will be indefinitely postponed when it reaches the wait section, as it will be waiting for a signal to $Sem$ that will never be sent as the other process has exited

### 5.iii

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

