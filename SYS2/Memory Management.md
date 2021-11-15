---
date created: 2021-11-15 14:00

---

# Memory Management

> CPU can only access main memory and registers

- Register access can be done in one CPU clock
- Memory access may take more than one CPU clock
  - Cache sits between to mitigate stall issue

## Operations

- **Read** request & address _(load rc 0x102)_
- **Write** request & data & address _(store ra 0x343)_

## [[Address Space]]

## Memory Management Unit

> Hardware device that at runtime maps logical addresses to physical addresses

## Single User Contiguous Memory

> All memory assigned to a single job

- Easy address resolution
- Physical address = issued address
- Process unused during I/O operations

## Memory Partitioning

### xcvbxfhfgvjdfjhfygStatic partitioning

> Divided into number of static partitions at system generation time
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