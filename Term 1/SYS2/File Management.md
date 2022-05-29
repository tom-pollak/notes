---
date created: 2021-11-23 14:57

---

# File Management

## Files

> Named collection of related information that is recorded on secondary storage
> - User perspective: Smallest allotment of logical secondary storage
>     - Data cannot be written to secondary storage unless they are within a file


- **Long-term existence:** Files stored on disk, do not disappear when user logs off
- **Shareable between processes:** Files have names & associated permissions that permit controlled sharing
- **Structure:** Files internal structure
  - Can be organized into hierarchical or other structure to reflect relationships between files

Linux provides **proc** FS that uses it as an interface to provide access to system information

## Attributes

- **Name**
- **Identifier**
- **Type**
- **Location**
- **Size:** bytes, words, or blocks — possibly maximum allowed size include
- **Protection:** Access-control info
- **Timestamps & user identification**


## Safety

We want to keep it safe from:
- Physical damage (reliability)
	- Backups
	- Copy disk files to tape at regular intervals to maintain copy should FS be destroyed
- Improper access (protection)
	- User authentication
	- Encrypting secondary storage
	- Firewall network access

## Access Control

> Read, write, execute, traverse, list, rename, delete

Permissions at three levels:
- Owner
- Group
- Universe

## Memory-Mapped Files

> Mapping a disk block to a page in memory

## Software Architecture

- A storage device must be “mounted” as part of an FS
	- Verifies information on disk is valid FS
- Before a storage device removed, it should be unmounted — checks all files closed and information written to disk (no information cached)

## Directories

> File which holds information of other files

- Provides name space for file names
	- Maps names to files themselves
- File operations may also update directory


> Non tree based directory: aliasing multiple names pointing to same file
> - Symlink?
> - Careful with broken links (deleting/moving)

## File Allocation

> Stored as blocks

### Contiguous

- Each file occupies a set of contiguous blocks on disk
- File handler needs:
	- First block
	- Number of blocks
- Number of disk seeks minimized
- Access to file is easy
- Finding space difficult
	- External memory fragmentation [[Memory Partitioning#Dynamic Partitioning]]
- Allocating file size difficult if file allowed to grow

### Linked

- File linked list of blocks: each block contains block number of next block
- Blocks can be scattered throughout disk
- Directory holds pointer for first & last block
- Access to $i_th$ block requires scanning all blocks from first one
	- Bad support for direct access
		- Possible solution to group blocks (continously) in clusters
- Reliability problem: one block gets damaged, rest of file lost

### Indexed

- First block of file (index) contains list of blocks used by file
	- Similiar to [[Swapping#Paging]]
- Easy direct access
- Index block usually cached
- Wasted space: additional full block used for each file
- Index blocks can be linked for large files — if can't fit in one block