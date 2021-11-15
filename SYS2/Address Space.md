---
date created: 2021-11-15 14:14
date updated: 2021-11-15 14:14

---

# Address Space

> Logical address space: range address OS makes available to process

Endpoints:

- **Base register:** physical address start point
- **Limit register:** size of address

## Address Types

- **Source:** Symbolic, e.g. variable count
- **Compiler:** binds these to relocatable addresses, e.g. 14 bytes from beginning (_logical address_)
- **Linker or loader**: bind relocatable addresses to absolute addresses, e.g. 0x133 (_physical address_)

## Address Binding

- **Compile time:** If memory location known priori, absolute code can be generated
- **Load time:** memory location not known, relocatable code generated
- **Execution time:** Binding delayed until runtime if [[Processes | process]] can be moved during its execution
