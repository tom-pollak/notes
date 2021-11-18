---
date created: 2021-11-18 12:24
date updated: 2021-11-18 12:29

---

# Deadlocks

## Possibility of Deadlock

- **Mutual Exclusion:** Only one process at a time can use a resource

- **Hold and wait:** Process holding at least one resource is waiting to acquire additional resources held by other processes

- **No pre-emption:** A resource can be released only voluntarily by the process holding it, after the process completed the task

- **Guaranteed existence** — **Circular wait:** There exists a set of waiting processes such that a process waiting for a resource which is held by another process waiting in that same queue

## Deadlock handling strategies

- **Deadlock prevention:** Disallow one of the three conditions for deadlock occurrence, or prevent the circular wait condition from happening

- **Deadlock avoidance:** Do not grant resource request if may lead to deadlock

- **Deadlock detection:** Grant resource requests if possible, but periodically check for the presence of a deadlock and take action to recover

## Deadlock Prevention

- **Mutual exclusion:** not required for sharable resources (e.g. read-only), must hold for non-shareable resources

- **Hold and wait:** must guarantee that whenever a process requests a resource, it does not hold any other resources
  - Or can require a process to request and be allocated before it starts executing. **(Hold everything needed or hold nothing)**
  - Low resource utilization, starvation possible

- **No preemption:** If a process that is holding some resources requests another resource that cannot be immediately allocated to it (_preempt_)
	- Preempted resources added to the list of resources for which the process is waiting
	- Process will only be restarted when it can regain its old resources plus new ones requesting

- **Circular Wait:** Impose a total ordering of resource types, and require that each process requests resources in an increasing order of enumeration
	- Declare each resource a number, and impose increasing ordering


## Safe State

> If the system can allocate resources to each thread in some order and still avoid deadlock

> System must decide if immediate allocation of a resource to process leaves system in a safe state

System in safe state iff there exists a sequence $<T_1, T_2, ..., T_n>$ of **all** processes in systems such that for each $T_i$, resources of $T_i$ can still request and be satisfied by currently available resources & resources held by all $T_j$ with $j < i$
- Can use resources from processes earlier in sequence as they will have already finished

## Avoidance algorithms

### Resource-Allocation Graph

> Single instance of a resource type

1. Claim edge $T_j > R_j$ that process $T_j$ may request $R_j$ at some time in future — dashed line
2. Converts to request edge when process requests resource
3. Request edge converts to assignment edge once resource assigned to process
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
