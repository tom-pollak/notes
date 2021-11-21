---
date created: 2021-11-21 20:14
date updated: 2021-11-21 20:14

---

# Memory Partitioning

## Static Partitioning

> Divided into number of static partitions at system generation time
>
> - Process loaded into a partition of equal or greater size

- Inefficient use of memory due to **internal fragmentation**
  - Maximum number of active processes fixed

## Dynamic Partitioning

> Partitions created dynamically, each process loaded into partition exactly the same size as process

- More efficient use of memory
- Inefficient use of processor due to need for compaction to counter **external fragmentation**

### Partition allocation problem

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
