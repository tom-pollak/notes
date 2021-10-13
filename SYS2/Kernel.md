# Types of Kernel

## Monolithic
- Each component contained in kernel
- Can communicate directly with any other component with unlimited access

## Layered
- Layers of modularity, each uses functions and services of lower layers

## Micro kernel
- Components moved from kernel to user space
- Communication between user modules using message passing

#### Advantages
- Easier to extend
- Easier to put onto new architectures
- Reliable
- Secure

#### Disadvantages
- Performance overhead 
	- User space --> kernel communication

## Hybrid
- Combines kernel types