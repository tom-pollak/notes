# Virtual Memory

- Separation of user logical memory from physical memory
- Logical address space can be larger than physical
- More performance and resource efficiency
	- Less I/O needed to load or swap processes
	- More efficient process creation

## Virtual address space

- Logical address space for stack grows “down” while heap grows up
- Libraries can be shared in virtual memory

## Demand paging

- Program permanently stored in backing store and swapped as needed
- Backing store split into blocks, same size as the frame and pages
- Program has a small num of pages loaded into main memory
	- Working set
	- As program coverage is generally small
		- E.g. error handling is rarely used


Allows to run programs which require much more memory than physically available


### Paging

> Pager: a swapper that deals with pages

- Only loads needed pages
	- Page is needed when there is a reference to it
		- Invalid reference → abort
		- Not in memory → bring in to memory

When a process is swapped in, pager predicts which pages will be used before the process is swapped out again

- OS must distinguish between pages in memory and pages on disk

### Page fault

> Page fault: page needed not in memory
> - Needs to detect and load page into memory from storage


![[demand-paging.png | 300]]

- Needs a page table that determines whether a page has been loaded

#### Handling page faults

- Interupt - context switch
- Process state is saved
- OS restarts instruction that causes page fault
	- Will be in same state

OS actions
1. Find free frame
2. Swap page into frame via scheduled I/O
3. Reset tables to indicate page is now in memory
	- validation bit in page table
4. Restart instruction

Can even schedule another instruction while I/O process is happening (2)

![[handling-page-fault.png]]

Extreme case: process started with no pages in memory
- **Pure demand paging**
- A single instruction can access multiple pages and cause multiple page faults
	- fetch decode of instruction which adds 2 numbers and stores back in memory



#### Performance 
- Worst sequence of events

1. Trap to OS kernel
2. Save user registers and process state
3. Determine interrupt is page fault
4. Check page reference legal
5. Determine location on disk
6. Issue read from disk to free frame (space in memory)
	1. Wait in queue for device until IO read request serviced
	2.  Wait for device seek and latency time
	3. Begin transfer of page to free frame
7. While waiting for IO, allocate CPU to some other process
8. Recieve interrupt from disk IO (completed)
9. Save registers and process state from other process
10. Determine interrupt was indeed from disk
11. Correct page table, to show page now in memory
12. Wait for CPU to be allocated to process again
13. Restore user registers, new page table and resume from interrupted instruction

Major activities
- Service interrupt: hundreds of instructions
- Read in the page
- Restart process: hundreds of instructions

> Page fault rate (0-1): 
> - $p = 0$ no  page faults
> - $p = 1$ every instruction is page fault

Effective Access Time (EAT)

$$EAT = (1-p) \text{}$$