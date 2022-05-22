# Cache Memory

Organize memory has hierarchy

- Mulitple levels of memroy with different speeds and sizes

![[cache.png]]


## Access Patterns

Principles of a program:
- **Principle of Locality:** Programs access a relatively small portion of their address space at any instant of time 
- **Temporal Locality:** If an item is referenced, it will tend to be referenced again soon
	- Keep the fetched memory stored in cache
- **Spatial Locality:** If an item is referenced, items whose addresses are close by will tend to be referenced soon
	- Nearby addresses will be requested in the future, so store nearby addresses

![[cache-access-patterns.png]]


## Fundamentals

- **Block/Line:** Minimum unit of information that is present or not present in cache level
	- Either present or not present – cannot have part of a block in cache
- **Hit:** An access where the data requested is in cache
- **Miss:** Not present in cache
- **Hit Time:** Time to access a memory block and return data to processor
- **Hit rate/ Miss rate:** Fraction of memory access _found_/_not found_ in cache
	- 0-1
	- Hit rate + miss rate = 1
- **Miss penalty:** Time to replace a block in cache with corresponding block from next level

![[cache-access-time.png]]

## CPU-Cache Interaction

![[cpu-cache-interaction.png|300]]


- CPU register: 4 4-byte words
- L1 cache: 2 4-word blocks
- Memory Many 4-word blocks

- Transfer between CPU register and cache is 4-byte word
- Transfer between cache and main memory is a 4-word block (16B)

## Cache Organization

> Array of sets


![[organization-of-cache.png]]

- Each set contains 1 or more lines
	- $E$ lines per set
	- e.g. 8-way set associative, $E=8$
- Each line holds a block of data
- 1 valid bit per line
- $t$ tag bits per line
- $B = 2^{b}$ bytes per cache block

$$\text{Cache size: } C = B \times E \times S $$

$$\#Sets = \frac{\text{Cache Size}}{\text{Block size} \times E}$$

## Addressing Caches

> Word address $A$ is in cache if the tag bits in one of the _valid_ lines in set _set index_ match _tag_

- Word contents begin at offset _block offset_ bytes from beginning of block

1. Locate set based on _set index_
2. Locate line in set based on _tag_
3. Check line is _valid_
4. Locate data in line based on _block offset_

### Question

> A cache has 512 KB capacity, 4B word, 64B block size and 8-way set associative. The system is using 32-bit address. Given address 0xABC89984, which set of cache will be searched and specify which word of the selected block will be forwarded if it is a hit in cache?

$\large \# Sets = \frac{2^{19}}{2^{6} \times 2^{3}} =  2^{10} = 1024 \text{ sets}$

1 word = 4B, Hence 64 byte block has 16 words, Tag = 16

lengths: Index = 10, Offset = 6 (4 (word no) + 2 (which byte in word))

0xABC89984 = 1001 1001 10**00 01**_00_ → Set 614, word 1
- Use LSB

Bold: word no
Italic: which byte in word: as 4B word
No formatting: index

## Memory design choices

- **Block placement:** where can block be placed in the cache?
- **Block identification:** How is a block found if it is in the upper level
- **Block replacement:** Which block should be replaced on miss?
- **Write strategy:** What happens on a write?

### Block placement

![[block-placement.png]]

- **Direct mapped:** A unique location for every main memory block
	- Can lead to situations where two memory blocks require the same cache location
	- $\text{Block no \% Num blocks in cache}$
	- Only 1 tag compare required to access
	- $\text{Cache size} = \text{Block size} \times \text{S data bytes}$
	- $E = 1$
- **Set associative:** A block mapped to this location can use any location in the set
	- $\text{Block no \% Num sets}$
	- $E=2$
- **Fully associative:** Block can be placed in any location

### Block identification

#### Accessing direct mapped 

![[accessing-direct-mapped-cache.png]]

#### Accessing set associative cache
- Check tag bits in each cache line
- If one of them matches, then cache hit

#### Accessing fully associative cache
- Must go through every cache line

#### Complexity trying to locate one index

Indexing time depends on decoder size ($s = 2^{s}$)
smaller number of sets, less indexing time

### Block replacement

- Direct mapped is trivial

#### Set associative cache

- Random
	- Needs random number generator
- FIFO
- LIFO
	- Both require queue $Q$ store references
- Least recently used (LRU)
	- $a=2$
		- Add LRU bit
		- Set/ clear on each access
	- for $a>2$ LRU is expensive
		- Record timestamp? How many bits?
		- Must find min timestamp on each eviction
		- Sorted list? re-sort on each access?
		- Shift register implementation
- Pseudo-LRU
	- Use binary tree
- NRU
	- Keep NRU state in 1 bit block
		- reset to 0 when installed/ re-referenced
		- set to 1 when it is not referenced and other block in same set is referenced
			- Evictions favour NRU=1 blocks
			- if all blocks are NRU=0/1 pick by random
- LFU - least frequently used
	- Counter per block, incremented on reference
	- Evictions on lowest count
	- Logic not trivial ($a^{2}$ comparison/sort)
	- Storage overhead
		- 1 bit per block, same as NRU
- Re-Reference Interval Prediction (RRIP)
	Extends NRU to multiple bits
	- Start in middle
	- Promote on hit
	- Demote over time
- Optimal
	- Evict block with the longest reuse distance
	- Requires knowledge of the future!


#### Pseudo LRU
- 0: upper half older lower path newer
- Updates nodes on each reference


![[pseudo-LRU.png | 500]]


### Look-aside cache

> Request from processor goes to cache and main mem in parallel

- Cache & main mem both see bus cycle
1. Cache hit
	1. Processor loaded from cache
	2. Bus cycle terminates
2. Cache miss
	1. Processor & cache loader from main memory in parallel

### Look through cache

> Cache is checked first

cache miss → cache loaded from main memory → processor loaded from cache


## Write Strategy

### Write hits

> Writing a new value to memory

#### Write through

> Information is written to both the block in the cache and to the main memory

- Read misses do not need to write back evicted line contents

#### Write back

> Information is written only to the block in the cache. Modified cache block written to main memory only when it is replaced.

- Have to maintain whether block is clean or dirty.
	- Clean – no update
	- Dirty – cache has been updated, needs to overwrite memory on replacement
- No extra work on repeated writes.
	- Only latest value on eviction gets updated in main memory.

### Write miss

#### Write allocate

> Block loaded into cache on write miss

- Used with write back (dirty)

#### No-write allocate

> Block modified in main memory but **not** in cache!

- Used with write-through cache (simple)

## Type of cache miss

- **Compulsory:** Very first access to block
	- Will occur even on infinite cache
- **Capacity:** Cannot contain all blocks needed
	- Misses in fully associative cache (due to capacity)
- **Conflict:** If too many blocks map to same set
	- Occurs in associative or direct mapped




