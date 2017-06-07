# Database Outline

### Explicit Join vs. Implicit Join
- Expicit Join
	- e.g select * from a INNER JOIN b on a.a_id = b.b_id
- Implicit Join
	- e.g. select * from a, b where a.a_id = b.b_id

### Denormalized vs. Normalized Databases
- normalized databases
	- designed to minimize redundency
	- drawback: many common queries will require expensive join
- denormalized databases are designed to optimize real time
	- designed to optimize real time
	- by storing redundent data
	- is commonly used when designing a large, scalable database, when joins are generally very slow

### Database Design Workflow
1. Handle Ambiguity
2. Define the core objects, each of these core objects typically translate into a table
3. Analyze relationship, store relationships using foreign keys/separate tables.
4. Investigate actions, each of thse actions requires new tables and columns. 

### SQL Statements / Query