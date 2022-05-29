---
date created: 2021-11-22 13:34
date updated: 2021-11-22 13:55

---

# Virtual Memory

Process can only execute in main memory: “real memory”

> Virtual memory: All memory allocated on disk

- Storage allocation scheme in which secondary memory can be addressed as though it were part of main memory
- Addresses programs use are distinguished from the memory system used to identify physical storage sites
  - Program generated addresses translated automatically
- Size of virtual storage limited by addressing scheme of computer or amount of secondary memory available
  - **Not** actual number of main storage locations

## Operating System Policies

> Operating system allocates memory and pages
>
> - Process cannot edit own page table

- **Fetch Policy:** When to load page into memory
  - Demand paging
  - Prepaging: OS guesses what will be used next
- **Placement Policy:** Where to put new page in memory
  - OS records frame table: all fra - not needed
- **Replacement Policy**
  - Algorithms
    - Optimal:  Selects replacement for page that time to next reference is the longest
    - Least recently used (LRU)
    - FIFO
    - Clock:
  - Page Buffering:
- **Resident Set Management:**
  - Resident set size: fixed, variable
  - Replacement scope: global local
- **Cleaning Policy:**
  - Demand
  - Precleaning
- **Load Control**

### Page Replacement Policy

- In pure [[Swapping#Segmentation | segmentation]] system, placement policy is more important
- With [[Swapping#Paging | paging]] doesn't matter as much as [[Swapping#Paging Address Translation | address translation]] hardware and main memory access hardware can perform their functions for any page-frame combination with equal efficiency

## Thrashing

> A processor can spends most of its time swapping pieces rather than executing instructions

- Avoidance: OS tries to guess based on recent history which pieces are least likely to be used in future

> **Principle of locality:** Program and data references within a process tend to cluster. Hence, only a few pieces of a process will be needed over a short period of time.
> - Should be able to (guess) which pieces of a process will be needed in the near future

---

[[Memory Management]]
