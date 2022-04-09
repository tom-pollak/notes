# Page Replacement

PR completes separation between logical and physical memory
Full physical memory
Page frames all occupied
- Which pages to replace?
- Need algorithm which will minimize number of page faults
	- Same page may be brought into memory several times
- Use modify (dirty) bit to reduce overhead of data transfer.
	- Every time a process writes to page, set to 1
	- If frame is dirty, must be written back to memory, else it can just be discarded.
- Must also update page table to invalid to cause a page fault on victim page to be replaced.

## Policies
reference string: string of pages referenced

- FIFO
	- Increasing number of frames can sometimes **increase** number of page faults for specific reference strings - Belady's Anomaly
	- V counter-intuitive
	- Not used in practice

![[beladys-anomaly.png | 300]]

- Optimal (OPT): Given complete reference string, we can look into the future
	- Replace page not used for longest period of time
	- Only theoretical, used mainly as upper-bound comparative evaluation 
	
- LRU: least recently used

Approximation algorithms

Similar to LRU, without complex timestamping

Reference bit
- Each page associate a hardware provided bit (default 0)
- When page referenced associated bit set to 1
- Replace any bit with 0, if one exists
- We do not know order


Second-chance algorithm
- FIFO, plus hardware
- Reference bit = 0, replace
- = 1
	- Set reference bit to 0, leave page in memory
	- Continue to next page
	- So victim is skipped, whole pointer moves past
	- Needs a pointer

## Page & frame locking

- OS may wish some pages to remain in physical memory frames
	- OS itself
	- IO buffers
- Requires lock bit with each frame

## Frame allocation

- Determines how many frames given to each process
- And which frames to replace
- Each process needs **minimum** number
	- E.g. instruction 6 bytes, might span 2 pages
	
Global replacement – process selects a replacement frame from set of all frames
- In priority allocation, this could allow a high priority process to take frames from a lower priority process
- Page fault behaviour becomes dependent on behaviour of other processes
- Greater overall throughput, so more common (Linux)

Local replacement
- More consistent per-process performance
- If process does not have a sufficient number of frames allocated, the process will suffer many page faults (thrashing)
- Possibly underutilized memory

## Thrashing

> Process does not have “enough” pages, page-fault rate very high
> - Busy just swapping pages in and out

- No free frames (otherwise would have been allocated) hence have to swap out a frame from another (active) process
- Page swapped out needed again, no free frames, repeat

Leads to
- Low CPU utilization
- OS thinking needs to increase degree of multiprogramming
	- More processes run, making it even worse where they do not have enough pages

![[thrashing.png | 500]]

## Working set model