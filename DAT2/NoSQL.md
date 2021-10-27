# NoSQL

> Non-relational [[DBMS]]


## Types

### Column

> Stores in **columns** instead of rows

- Time efficiency
- Easy to perform mathematical operations

e.g:
- Row: 
	- **101**,JS,**29**,supervisor,**28000**;
	- **102**,KJ,**35**,manager,**38000**;
	- **103**,LM, **28**,supervisor,**29000**
- Column:
	-  101,102,103;
	-  JS,KJ,LM;
	-  29,35,28;
	-  supervisor,manager,supervisor;
	-  28000,38000,29000

### Key-Value

- Key must be unique

Operations:
- put(key, value)
- get(key)
- delete(key)

e.g.:
**Table:PK:Attribute = value**
Book:b102:Title = "Java for dummies"
Book:b102:Price = 45

### Document

> Uses key value pair and follows format of JSON or XML

{"bookID": "b102", "ISBN": 111-998-25675-22, "Author": "John C. and David P."} 

{"ISBN": "111-998-25675-2", "Price": 34}

- Rows don't have the same schema in each document

### Graph

> Each node represents an entity, each edge represents a relationship

Compared to other [[Relational Databases | DBs]] that use JOINS to compute relationship, graph DB stores connects alongside data in the model

## Uses

### Advantages

- Handles Big Data
- Data models: no predefined schema
- Handles unstructured data
- Uses horizontal scaling
- Cheaper to manage

### Disadvantages

- No constraints
- No joins
- No complex transactions

### When to use

- Huge amounts of data
- Unstructured
- Structure is changing with time
- No data constraints or joins needed
- Develop prototypes