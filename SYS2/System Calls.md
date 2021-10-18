---
date created: 2021-10-18 13:55

---

# System Calls

> ##### Programming interfaces to services provided by OS
>
> - Accessed by [[API]]s rather than direct sys call use
> - OS monitors sys calls

## User Space

> ###### Does not have direct access to hardware uses System Calls
>
> - CPU in user mode when executing user mode calls
> - Request of a kernel service

## Kernel Mode

> ###### Complete unrestricted access to hardware

```mermaid
graph BT
B(open application)
A(SC Interface)
C(Implemention of open system call)
subgraph User mode
B --> A --> B
end
subgraph Kernel mode
A --> C --> A
end
```
