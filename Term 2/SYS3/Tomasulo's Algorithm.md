# Tomasulo's Algorithm

- Load and store buffers contain data and addresses
- Act like [[Dynamic Scheduling#Reservation stations]]

![[tomasulo-algo.png]]

## Register status indicator

> Latest value of the register is in reg file or being computed

- If currently being computed, it states the execution number
- If not ready it will wait in the RS of the execution unit given by RSI

Fields:
- $Q_{i}$: Number of RS that contains the operation whose result should be stored into this register
	- If $Q_{i} = 0$ the value is in the register contents

## Issue
- Get next instruction from instruction queue (FIFO)
- If RS available, issue instruction to RS with operand values if available
	- If not available, stall instruction

## Execute
- When operand available, store in any RS waiting for it
- When all operands are ready, execute the instruction
- Load and store uses buffers
- No instruction will initiate execution until all branches that precede it in program order have completed

## Write result

- Write result into CDB with name of execution unit that generated the result
- Stores must wait until address and values are received

Number of commits per cycle equal to issue width

Watch spring wk 10 tutorial 2