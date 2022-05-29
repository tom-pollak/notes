---
date created: 2021-11-21 20:13

---

# Swapping

> Process can be swapped temporarily out of memory to a backing store, then brought back into memory to continue execution
>
> - Total physical memory space of processes can exceed physical memory

- **Backing store:** Fast disk large enough to accommodate binaries of all processes
- Major part of swap time is transfer time, which is directly proportional to the amount of memory
  - Process needs to both be transferred out and back in

## Paging

> Main memory partitioned into equal fixed-sized chunks that are relatively small, and each process divided into chunks of the same size

- **Pages:** Chunks of a process
- **Frames**: Available chunks of memory

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
