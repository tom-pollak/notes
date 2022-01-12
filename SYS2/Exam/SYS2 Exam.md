---
date created: 2022-01-11 12:53
date updated: 2022-01-12 00:45

---

# Exam

_Y3891128_

## 1.

### 1.i

A process can use a system call as an API to access hardware and functionality is not available in the user space. A process can change its own state with a system call such as **exit**, where a process can terminate its own execution, therefore changing the state.

### 1.ii

I would use a micro kernel approach, where you design the kernel to move as many components to the user space as possible. This can be easier to extend than a monolithic or layered kernel, as new or changed functionality can be implemented as a module in the user space.

The micro kernel is also more reliable and secure, as much of the code is in a less privileged user space. However, there is an overhead when the user space interacts with the kernel space.

## 2.

### 2.i

The process will have a total of 3 program counters and user stacks, private to each thread (the main thread and the two newly created threads).  Each thread shares the same common heap from the process. A process will have a private heap from other processes.

### 2.ii

Two processes are created, the original main process and the child process created from the **fork()** system call.

The values of the return ID from the child process is 0, as the fork will return to the main process, which has an ID of 0. The return ID of the parent process will be the ID of the running process given to it by the OS.

The value of $i$ is 15 in both processes. This is because both the child and parent execute the same instruction to add 5 to the variable $i$ which is defined as 10 before the fork.

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

Sharing memory between computers can allow processes to share chunks of data. However, a problem with this method is that it is hard to synchronize each computer's actions with the other when they access the shared memory, and this can lead to race conditions. This would be exemplified with the high latency, as the two processes are on different computers. This could also be insecure to let another computer write directly to your computer's memory if the other computer was not trustable.

Memory passing is a much better use case for this situation as it does not share variables, so does not suffer from the synchronization issues that were the big disadvantage of memory sharing. The link between the computers can either be direct, in which the processes on each computer targets the other directly, or indirect, in which the two computers can send and receive data from a predetermined port.

Message passing does require an overhead in processing the message, which is not the case with shared memory, where the programs can directly expose their state. The messages may be either synchronous or asynchronous and bidirectional or unidirectional, allowing more flexibility in the implementation of the communication. This is a much better method of communicating and is the current standard in modern communication technology.

## 5.

### 5.i

If both processes are run at the same time, $increment$ would acquire $Sem1$, and $decrement$ would acquire $Sem2$. The $increment$ would then request the $Sem2$ resource, currently held by $decrement$ and $decrement$ would request the $Sem1$ resource, held by $increment$. As both processes need both $Sem1$ and $Sem2$ to enter the critical section and are holding onto their current resource while they wait for the next resource, they have created a circular wait, and are in deadlock.

### 5.ii

If one of the processes terminates while waiting, the other process will be indefinitely postponed when it reaches the wait section, as it will be waiting for a signal to $Sem1$ or $Sem2$ that will never be sent as the other process has exited

### 5.iii

```c
int turn;
int Sem1 = 0;
int Sem2 = 0;

void Signal(Sem) {
	if (Sem == 0) {
		Sem = 1;
	} else {
		Sem = 0;
	}
}

void increment() {
	while (true) {
		Signal(Sem1); // (= 1)
		turn = 1;
		while(Sem2 && turn == 1) {
			z++;
			Signal(Sem1); // (= 0)
		}
	}
}

void decrement() {
	while (true) {
		Signal(Sem2); // (= 1)
		turn = 0;
		while(Sem1 && turn == 0) {
			z--;
			Signal(Sem2); // (= 0)
		}
	}
}
```

## 6.

### 6.i

**(a)**

| 7 | 2      | 3           | 1           | 2           | 5           | 3           | 4           | 6           | 7           | 7           | 1           | 0           | 5           | 4           | 6           | 2           | 3           | 0           | 1           |
| - | ------ | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| 7 | 7<br>2 | 7<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>5 | 3<br>2<br>5 | 3<br>4<br>5 | 3<br>4<br>6 | 7<br>4<br>6 | 7<br>4<br>6 | 7<br>1<br>6 | 7<br>1<br>0 | 5<br>1<br>0 | 5<br>4<br>0 | 5<br>4<br>6 | 2<br>4<br>6 | 2<br>3<br>6 | 2<br>3<br>0 | 1<br>3<br>0 |
| F | F      | F           | F           |             | F           | F           | F           | F           | F           |             | F           | F           | F           | F           | F           | F           | F           | F           | F           |

18 page faults, assuming populating the frames originally count as page faults

**(b)**

| 7 | 2      | 3           | 1           | 2           | 5           | 3           | 4           | 6           | 7           | 7           | 1           | 0           | 5           | 4           | 6           | 2           | 3           | 0           | 1           |   |
| - | ------ | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | - |
| 7 | 7<br>2 | 7<br>2<br>3 | 1<br>2<br>3 | 1<br>2<br>3 | 1<br>5<br>3 | 1<br>5<br>3 | 1<br>5<br>4 | 6<br>5<br>4 | 6<br>7<br>4 | 6<br>7<br>4 | 6<br>7<br>1 | 0<br>7<br>1 | 0<br>5<br>1 | 0<br>5<br>4 | 6<br>5<br>4 | 6<br>2<br>4 | 6<br>2<br>3 | 0<br>2<br>3 | 0<br>1<br>3 |   |
| F | F      | F           | F           |             | F           |             | F           | F           | F           |             | F           | F           | F           | F           | F           | F           | F           | F           | F           | F |

18 page faults, assuming populating the frames originally count as page faults

### 6.ii

**(a)** The maximum number of frames and pages available can be calculated by dividing the size of the memory by the size of the page. The memory is 256 MB (256,000 KB) and the page size is 4 KB. This gives a total of **64000** pages or frames.

**(b)** The virtual address is 32 bits long or 4 bytes. The page entry table can take up a single virtual address minus the space taken up by the control bits (1 byte). Therefore, the size of the page table entries address is 3 bytes.

The system has 32-bit long virtual address, therefore the virtual address space is  $2^{32}$. The page size is 4 KB ($2^{12}$ bytes). Therefore, we can store $\large \frac{2^{32}}{2^{12}} = 2^{20}$ pages. Since each entry has an address size of 3 bytes, the maximum size of the page table is $3 \times 2^{20} = 3,145,728$ bytes.

## 7.

### 7.i

I/O instructions are privileged, so must be done through OS system calls. This can prevent users from performing illegal I/O instructions, which can result in I/O failing and causing errors.

The OS must handle errors from the I/O, such as failing disk reads/writes or network send errors. These can be transient, in which case the OS can retry the operation, or permanent, where the OS will have to fail the operation.

Memory-mapping can map a portion of a file on disk to a range of addresses within the application's address space. The application can then access files on disk in the same way it accesses memory. This can increase I/O performance, but the OS must be able to handle I/O errors on the underlying file while processes are accessing its mapped memory. If handled incorrectly, this can cause multiple out of sync versions of the same file. The OS also has to handle concurrency issues where multiple processes are making changes to the file version in memory.

### 7.ii

**1.** I would use contiguous allocation with a first fit policy. As the files are accessed sequentially, we do not need to optimize placement, as the files will be in the order they will are accessed in. The OS will not need to search the entire list to find the file, as they are still in the order they were added.

This method will not suffer from external fragmentation or any extra space overhead as files are deleted from memory in the order they were added, similar to a stack, and as they were added in order, only one growing partition of free space is created.

**2.** For the large number of large files accessed in a random order I would use indexed allocation with best fit, as the files are large, and will use multiple blocks. The overhead of the index block is relatively small in comparison to the number of blocks used to store the file. As all identifying block information is in the index block, it is more reliable than linked allocation, as the entire file will not be lost if one block is corrupted.