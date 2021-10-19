# A* Search
> ##### Only optimal when an admissible heuristic is used

Uninformed search works based on structure of tree and cumulative path cost
Informed search looks at states within the node to make a more informed choice

### Uniform-cost search (UCS)
Like breadth first but nodes stored in priority queue ordered by increasing path cost

## Informed search
- Predict goal state can expand nodes more likely to reach goal sooner
- Evaluation function $f(n)$ is used to provide this signal allowing extra information to be used
- Common approach to defining $f(n)$ is to use a heuristic function $h(n)$
	- Typically fast to compute and provide domain specific information to search algorithm
	- e.g. Good heuristic in computing journey time is straight line distance to destination

