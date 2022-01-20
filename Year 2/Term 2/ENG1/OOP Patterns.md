---
date created: 2022-01-18 18:09

---

# OOP Patterns

## Listener

- Allows multiple clients to “listen” to events
- Implement auto save or sync when a note is added, we just need to add another listener

## Command Stack

- Changes made stored in a command stack
- Support multiple undos and redo

## Factory

- Abstract creation logic in the factory
- Offers command methods with extra knowledge

## Facade

- Modular and extensible architectures can be complex
- Sometimes desirable to hide complexity
- Simplified interface, easier to use and understand
	- Delegates existing class behind the scenes

## Callback

- A method takes long to return, and we don't want the rest of the application to freeze while the method is running
	- Want to recieve a notification when the method has completed/ failed
	- e.g. sync() method that synchronises remote notes


## Singleton

- Object to be unique and easily accessible from all parts of the application

Solution
- Create class X
- Make its constructor private (so clients cannot create instances of it)
- Add a private static field of type X that holds a reference to a unique instance
- Add a public static X getInstance() method that creates the unique reference and (lazily) returns it

