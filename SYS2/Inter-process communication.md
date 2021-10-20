# Inter-process communication

> [[Processes]] may be independent or cooperating process can affect each other
> - Used in [[Scheduling]]

- Cooperating process used for
  - information sharing
  - computation speed up
  - modularity
  - convenience

## Shared Memory

- Area of memory shared among processes
- Communication controlled by user processes not [[Operating System]]
- Issues providing mechanism that allow user processes to synchronize their actions when they access shared memory
  - Race conditions

## Message Passing

- Communicate without shared variables
  - Provide two operations: send(message), receive(message)

#### Implementation of Communication

Physical:

- Shared memory
- Hardware bus
- Network

Logical:

- Direct or indirect
- Synchronous or async
- Automatic or explicit buffering