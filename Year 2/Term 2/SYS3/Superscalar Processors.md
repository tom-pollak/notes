# Superscalar Processors

> Multiple instructions running in parallel

![[Resource-utilization.png]]


- Increase depth of pipeline – increase clock rate **superpipelining**
	- Subdivide pipeline operations into smaller operations
	- Two operations for fetch, letting you get twice as many instructions
- Fetch more than one instruction at one time – multiple-issue **superscalar**
	- Allows CPI to be less than 1

## Multiple-issue & static scheduling

### Statically scheduled 

- Execute multiple instructions together
- Has to find combination of instructions able to run together

### VLIW

> (very long instruction word) processors

- Package multiple operations into one long instruction (**long word**)
- Must be enough parallelism in code to fill available slots
- Find parallel instructions by [[Compiler Techniques#Loop unrolling scheduling]]

![[vliw.png|300]]

Disadvantages
- Statically find parallelism
- Lack of parallelism – slot waste
- Code size increase due to loop unrolling
- No hazard detection **hardware**

### Extreme optimization

- Modern architectures use [[Dynamic Scheduling]], multiple issue and [[Speculative Execution]]
- Dependency between instructions issued on same clock
- Register read for multiple instructions in parallel
- Complex issue logic to check dependencies and hazards
- Assign reservation stations and ROB entries in a cycle

#### Handling multiple issue

- Assign RS and ROB for every instruction in next issue bundle
- Limit num instructions of a given class in bundle (one FP one load-store etc)
- Stall issue if [[Speculative Execution#Reorder buffer]] (ROB) unavailable
- If dependency exists in bundle, encode in [[Dynamic Scheduling#Reservation stations]] with ROB 
- Multiple completion/commit (wide CDB (common data bus) & ROB)

### Dynamically scheduled 

- Most popular

## Multithreading

- Allows multiple threads to share the functional units of a single processor in an overlapping fashion

![[multithreading.png | 500]]


- Coarse MT: after few clock cycles, switch program
- Fine MT: Switch every clock cycle

## Hyperthreading / SMT

- More than one instruction stream per slot

![[hyperthreading.png | 500]]

- Issue instructions from A and B at the same time
