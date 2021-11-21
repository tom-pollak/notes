---
date created: 2021-11-15 14:00
date updated: 2021-11-21 12:06

---

# Memory Management

> CPU can only access main memory and registers

- Register access can be done in one CPU clock
- Memory access may take more than one CPU clock
  - Cache sits between to mitigate stall issue

## Operations

- **Read** request & address _(load rc 0x102)_
- **Write** request & data & address _(store ra 0x343)_

## Address Space

> Logical address space: range address OS makes available to process

Endpoints:

- **Base register:** physical address start point
- **Limit register:** size of address

![[base-limit-harware-protection.png]]

### Address Types

- **Source:** Symbolic, e.g. variable count
- **Compiler:** binds these to relocatable addresses, e.g. 14 bytes from beginning (_logical address_)
- **Linker or loader**: bind relocatable addresses to absolute addresses, e.g. 0x133 (_physical address_)

### Address Binding

- **Compile time:** If memory location known priori, absolute code can be generated
- **Load time:** memory location not known, relocatable code generated
- **Execution time:** Binding delayed until runtime if [[Processes | process]] can be moved during its execution

## Memory Management Unit

> Hardware device that at runtime maps logical addresses to physical addresses

## Single User Contiguous Memory

> All memory assigned to a single job

- Easy address resolution
- Physical address = issued address
- Process unused during I/O operations

## Memory Partitioning

### Static Partitioning

> Divided into number of static partitions at system generation time
>
> - Process loaded into a partition of equal or greater size

- Inefficient use of memory due to **internal fragmentation**
  - Maximum number of active processes fixed

### Dynamic Partitioning

> Partitions created dynamically, each process loaded into partition exactly the same size as process

- More efficient use of memory
- Inefficient use of processor due to need for compaction to counter **external fragmentation**

#### Partition allocation problem

- **First fit:** allocate to first partition that is big enough
- **Best fit:** Allocate the smallest partition that is big enough
  - Must search entire list, unless list ordered by size
  - Produces the smallest leftover partition
- **Worst fit:** allocate the largest partition
  - Search entire list
  - Produces the largest leftover partition

No clear winner: performance depends on request patterns

## Dynamic Contiguous Partitions

> Compaction (de-fragmentation) procedure\

- Requires relocatable partitions
  - Base register needs to be changed
- Compaction algorithm needs spare memory to operate efficiently
- Cannot perform compaction whilst I/O in progress involving memory that is being compacted

![[relocation-hardware-protection.png]]

## Swapping

> Process can be swapped temporarily out of memory to a backing store, then brought back into memory to continue execution
>
> - Total physical memory space of processes can exceed physical memory

- **Backing store:** Fast disk large enough to accommodate binaries of all processes
- Major part of swap time is transfer time, which is directly proportional to the amount of memory
  - Process needs to both be transferred out and back in

## Paging

> Main memory partitioned into equal fixed-sized chunks that are relatively small, and each process divided into chunks of the same size

- **Pages:** Chunks of a process
- **Frames**: available chunks of memory

Advantages:

- Wasted space in memory for each process is due to internal fragmentation of only a fraction of the last page of a process
- No external fragmentation

### Paging Address Translation

![[paging-translating-address.png]]

## Segmentation

> User program & associated data can be subdivided into a number of segments

- Not required to be of the same length
- Is a maximum segment length

![[segmentation.png]]

## Resident Set

### Paging & Segmentation Characteristics

1. All memory references within a process are logical addresses, dynamically translated to physical at runtime
	- Processes may be swapped out and occupy different regions of memory at different times during execution
2. A process may be broken into multiple pieces, and these pieces do not need to be continuously located in memory during execution
	- Dynamic run-time address translation
	- Page & segment table


- If the two characteristics are present, not necessary that all pages/ segments of a process be in main memory during execution

> Resident set: portion of process in main memory

Advantages:

- More processes maintained in main memory
- Process may be larger than all main memory