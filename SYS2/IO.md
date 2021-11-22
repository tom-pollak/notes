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