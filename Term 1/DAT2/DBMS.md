---
date created: 2021-10-18 14:48

---

# Database Management System

> - Define, create & maintain database
> - Provide controlled access to [[Relational Databases | DB]]
> - Store, modify & extract data

## DB Abstraction

### External level

- Users' view of DB
- Describes part of DB relevant to user

### Conceptual level

- Whole model as seen by DB admin
- Describes what data stored in DB
- Describes relationships among data

### Internal level

- Physical representation on computer
- Describes how data stored in DB

## Functions of DBMS

- Data storage, retrieval & update
- Concurrency control services
- Recovery
- Security: Protection of DB from unauthorized access
- Transaction support
  - **Transactions:** actions carried out by user that access or changes DB in some way
  - Ensures updates are undone if transaction fails to complete

### Advantages

- Control of data redundancy
- Data consistency
- Sharing of data
- Data integrity
- Data independence: DB & applications are independent of DBMS middlemen

### Disadvantages

- Complexity
- Cost of hardware & software
- Cost of data conversion
- Performance: bespoke may be faster
- Higher impact of failure
