---
date created: 2021-11-23 14:45
date updated: 2021-11-23 14:57

---

# I/O

**Categories:**

- **Human readable**
  - Printers, terminal
  - Display, keyboard
- **Machine-readable**
  - Disk drives
  - USB
  - Controllers
- **Communication:** Communicating with remote devices
  - NIC
  - Digital line drivers

**Differences:**

- Data rate: bits to gigabits
- Application
- Complexity of control
- Unit of transfer: byte stream or blocks
- Data representation: encoding schemes
- Error conditions: nature, reporting mechanism, consequences, response

## Operations

- **Programmed:** Processor issues I/O for [[Processes | process]]; process then busy waits for operation to complete
- **Interrupt-driven:** Processor issues I/O for process.
  - If I/O instruction is **non-blocking**, processor continues to execute instructions from the process that issued I/O command
  - If I/O is **blocking**, next instruction will be from OS, which will put current process in a blocked state and schedule another process
- **Direct memory access (DMA):** Processor sends request for transfer of block of data to DMA module, interrupted after entire block has been transferred

## Scheduling

- **Blocking:** I/O scheduler maintains a wait queue of requests for each device. When a process issues a blocking I/O call, a request placed on the queue for that device.
  - Scheduler rearranges order of queue to improve efficiency
- **Non-Blocking** Must be able to keep track of many requests at the same time
  - Attach wait queue to device-status table.
  - [[Kernel]] manages table, contains entry for each I/O device.

## Buffering

> Buffer: Memory area that stores data transferred between two devices

- Used for data rate mismatch between producer and consumer
- Provide adaptions for devices that have different data-transfer sizes
- Support copy semantics for application I/O

> Buffering: Can perform input transfers in advance of request being made and output transfers some time after request is made

![[types-of-buffering.png]]

## Caching

> Buffer: hold existing copy of data item
> Cache: holds faster storage copy of item residing elsewhere

## Spooling

> Buffer that holds output for a device that cannot accept interleaved data streams

- E.g. printer can only print one job at a time, but several applications may wish to print
- OS copies queued spool files one at a time to device

## Error Handling

- Transient: Network overloaded
  - OS can compensate for this type of errors e.g:
    - read() failure results in read() retry
    - send() then resend()
- Permanent: Disk controller becomes defective
  - OS unlikely to recover

<br>

- I/O system call will return one bit of information about system call: pass or fail
- Unix: Additional integer var named **errno** used to return error code

### Protection

- User may attempt to disrupt normal operation of system by issuing illegal I/O instructions
  - Define all I/O to be privelidged instrucitons
  - Users cannot issue I/O directly - must go through OS

## Kernel Data Structures

> Needs to keep state information about use of I/O.

- Open-file table structure, open-network status records etc

## I/O Lifecycle

![[io-lifecycle.png]]
