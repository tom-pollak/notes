# Deadlocks

## Possiblility of Deadlock


- Mutal Exclusion
- No preemption
- Hold and wait

**Guaranteed existence**

- Circular wait

## Deadlock Prevention

- Mutual exclusion: not required for sharable resources (e.g. read-only), must hold for non-shareable resources
- Hold and wait: must guarantee that whenever a process requests a resource, it does not hold any other resources
	- Or can require process to request and be allocated before it starts executing
	- Allow processes to request resource when process has none allocated to it
- 

## Safe State

> System must decide if immediate allocation of a resource to process leaves system in a safe state

System in safe state iff there exists a sequence $<T_1, T_2, ..., T_n$ of **all** processes in systems such that for each $T_i$, resources of $T_i$ can still request and be 


## Avoidance algorithms

### Resource-Allocation Graph

> Single instance of a resource type

1. Claim edge $T_j > R_j$ that process $T_j$ may request $R_j$ at some time in future - dashed line
2. Converts to request edge when process requests resource
3. Request edge converts to assignmentedge once resource assigned to process
4. When resource released, edge reconverts to claim edge

### Bankers Algorithm

> Multiple instances of resources
> Each process must priori claim maximum use
> When a process gets all its resources, it must return them in a finite amount of time

Let $n$ be a number of processes and $m$ be a number of resources types

- Available: Vector of length $m$. If $available[j] = k$, there are $k$ instances of resource type $R_j$ available.
- Max: $n \times m$ matrix. If $max[i,j] = k$, process $T_i$ may request at most $k$ instances of resource type $R_j$
- Allocation: If $allocation[i,j] = k$ Then $T_i$ is currently allocated $k$ instances of $R_j$
- Need: $need[i,j] = k$ $T_i$ may need k more instances of $R_j$ to complete its task

> $need[i,j] = max[i,j] - allocation[i,j]$

