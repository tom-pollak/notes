# Cache Optimization
$$\text{Average memory access time} = \text{Hit time} + (\text{Miss rate} \times \text{Miss penalty})$$
[[Cache Memory#Fundamentals]]

- Reduce average AMAT

## Larger block sizes

> Reduce miss rate

### Advantages
- Utilize spatial locality
- Reduce compulsory misses

### Disadvantages

- Increases miss penalty
	- Takes more time to fetch a block to cache
		- Can only bring one word at a time
		- Bus width issue
- Increases conflict misses
	- More number of blocks mapped to same location
	- May bring useless data and evict useful data (pollution)