# Virtual Memory

- Separatioin of user logical memory from physical memory
- Logical address space can be larger than physical
- More performance and resource effiecency
	- Less I/O needed to load or swap processes
	- More effiecient process creation

## Demand paging

- Program permanently stored in backing store and swapped as needed
- Backing store split into blocks, same size as the frame and pages
- Program has a small num of pages loaded into main memory
	- Working set
	- As program coverage is generally small
		- E.g. error handling is rarely used


Allows to run programs which require much more memory than physically available


