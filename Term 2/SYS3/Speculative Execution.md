# Speculative Execution

> In [[Tomasulo's Algorithm]], no instruction will initiate execution until all branches that precede it in program order have been executed


## Tomasulo's algorithm for loops

- Predict branches that are taken and issue instructions across multiple iterations

## Load-store order conflict

> A load and a store can safely be done out of order, provided they access different addresses.

If a load and store access the same address, then either:
- Load is before the store in program order, interchanging them results in **WAR hazard**
- Store is before the load – **RAW hazard**
- Interchanging two stores to the same address - **WAW hazard**

To allow load and a store interchange:
- Check whether any uncompleted store that precedes the load shares the same data memory address as the load
	- So the data will be equivalent from either place
- Store must wait until no unexecuted loads or stores earlier in the program that share the same data memory address

## Hardware-based speculation

How to overcome [[Control Hazards]] in [[Tomasulo's Algorithm]]?

- Speculate – **Fetch, Issue and Execute** as if branch predictions are always correct: **commit** results only if prediction correct
- **Instruction commit:** Allowing instruction to update register file/memory
	- **Only** when instruction no longer speculative
- **Reorder buffer:** (ROB) Holds result of instruction between completion and commit
- [[Dynamic Scheduling#Reservation stations]] – Operand source now ROB instead of functional unit

### Techniques

- Dynamic branch prediction to choose which instruction to execute
- Speculation to allow execution of instructions before [[Compiler Techniques#Control dependence]] are resolved
	- With the ability to undo
- Dynamic scheduling to deal with the scheduling of different combinations of [[Compiler Techniques#Basic block]]

### Reorder buffer

- Instruction type: branch/store/register
- Destination field: register number/memory address
- Value field: output value
- Ready field: completed execution $\cup$ only issued

#### Operations

##### Issue

- Get an instruction from instruction queue
- Issue instruction if there is empty RS and an empty slot in ROB
	- Pre-book a slot in ROB for when instruction is completed
	- If full then instruction stalled
- Get slot number (tag) from ROB for this instruction
- Send the operands to RS if they are available from either RF or ROB (speculative register read)
- Num ROB entry sent to RS to tag result for when it is placed on CDB

##### Execute

- If not all operands available, monitor CDB
- Execute operation
- Instruction may take multiple clock cycles
	- Load still requires two steps
- Store need to have base register value available at this step for effective address calculation

##### Write result

- Write to CDB with ROB tag
- Data in CDB go into ROB and to RS waiting for result
- If value/address to be stored available, write into ROB
- Else CDB monitored until that value broadcast

##### Commit

###### Normal commit
- Occurs when instruction reaches head of ROB and result is present in buffer
- Updates RF/memory and removes it from ROB

###### Incorrect prediction
- ROB is flushed and execution restarted at correct successor of branch

