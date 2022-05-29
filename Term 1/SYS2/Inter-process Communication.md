---
date created: 2021-11-16 13:27
date updated: 2021-11-16 13:49

---

# Inter-process Communication

> [[Processes]] may be independent or cooperating process can affect each other
>
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

## Direct Communication

[[Processes]] must name each other explicitly:

- `send(P, message)`
- `recieve(Q, message)`

Properties:

- Links established automatically
- One link between a pair
- Can be unidirectional or bidirectional

## Indirect Communication

> Messages directed and received from mailboxes (or ports)

- Each mailbox has unique ID
- Processes can only communicate if they share a mailbox (create a link)
- Many to many processes to links

**Operations:**

- Create a new mailbox (port)
- Send and receive through mailbox
- Delete mailbox

### Mailbox sharing

How to decide who receives the message:

- Allow a link to only be associated with at most two processes
- Allow only one process at a time to execute a receive operation
- Allow the system to arbitrarily select the receiver
  - Sender notified who receiver was

### Message Synchronization

> Message passing may be either blocking or non-blocking. Blocking considered synchronous.

- **Blocking Send:** Sender blocked until message received
- **Blocking receive:** Receiver blocked until a message available

<br>
- **Non-blocking send:** Sender sends message and continue
- **Non-blocking receive:** Receiver receives valid message or null message

If both send and receive are blocking, we have a **rendezvous**.

## Pipes

> Conduit allowing two processes to communicate

- Half duplex: only one process can send at a time
- Full duplex: both processes can send at the same time


### Ordinary Pipe

> Cannot be accessed from outside the process that created it.

- A parent process creates a pipe and uses it to communicate with a child process
- Standard producer-consumer style
  - Unidirectional

### Named Pipe

> Can be accessed without parent-child relationship

- Bidirectional
- Multiple processes can use the same pipe
