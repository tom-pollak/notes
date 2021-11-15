---
date created: 2021-11-15 14:00

---

# Memory Management

> CPU can only access main memory and registers

- Register access can be done in one CPU clock
- Memory access may take more than one CPU clock
  - Cache sits between to mitigate stall issue

## Operations

- **Read** request & address _(load rc 0x102)_
- **Write** request & data & address _(store ra 0x343)_

## Address Space

> Logical address space: range address OS makes available to process

Endpoints:

- **Base register:** physical address start point
- **Limit register:** size of address

### Address Types

- **Source:** Symbolic, e.g. variable count
- **Compiler:** binds these to relocatable addresses, e.g. 14 bytes from beginning
- **Linker or loader**: bind relocatable addresses to absolute addresses, e.g. 0x133

### Address Binding

- **Compile time:** If memory location known priori, absolute code can be generated
- **Load time:** memory location not known, relocatable code generated
- **Execution time:** Binding delayed until runtime if process can be moved during its execution

