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

