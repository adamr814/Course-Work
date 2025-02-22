## The Relational Algebra and Relational Calculus ##

**Objectives**
- formal foundations of SQL
	- relational algebra and its importance
	- the difference between procedural and declarative languages
	- the basic algebra operators
	- examples of how they can be used to write complex queries?
	- relational and domain calculus, and how they can be used to write queries

**Relational Algebra**
- Relational algebra?
	- one of the two formal query languages associated with the relational model
	- queries in algebra are composed of a collection of operators
		- e.g. Unary and Binary operators
- Why is it important?
	- provides a formal foundation for a relational model query operation
	- used as a basis for implementing and optimizing queries in RDBMS
		- Algebra is used as an execution plan for evaluating a query using a query tree
- Relational algebra
	- a collection of operations used to manipulate relations
- E.g., Select tuples from individual relations or combine related tuples from various relations

**Relational Algebra: Operations**
- core operations:
	- relational database operations
		- select, project and join
	- set-theoretic operations:
		- union, intersection, difference, and cartesian product
	- other operations:
		- aggregate functions
		- variation of union and join operations

**Relational Calculus**
- Relational Calculus
	- declarative language
	- based on a first-order predicate logic (FOPL)
	- used to specify the desired result (query-by-example (QBE))
- Why is it important?
	- provides a higher-level declarative notation
	- used to specify relational queries
	- has a solid foundation in mathematical logic (predicate calculus)
		- if it works with tuples, then it is called tuples calculus
		- if it works with columns, then it is called domain calculus

**The Select Operation**
- used to select a subset of tuples (rows) in a relation that satisfies select conditions
- general format:
	- σ {selection condition} ({relation name}) where
		- σ is select operator
		- the selection condition is a boolean expression
- boolean expressions?
	- a > 5, a >= b (a > b AND c = d)

**Some examples**
- select the subset of EMPLOYEE tuples working in dept 4 (i.e. DNO = 4)
`σDNO=4 (EMPLOYEE)`
- select the employees whose salary is greater then $30,000
`σSALARY>30000 (EMPLOYEE)`
- select all employees who either work in dept 4 and make over $25,000 per year, OR work in dept 5 and make over $30,000
`σ(DNO=4 AND SALARY > 25000) OR (DNO=5 AND SALARY > 30000 (EMPLOYEE)`

**The select operation: Properties**
- the operation is a unary operation
- the degree of a relation resulting from the select operations is the same
- Selectivity?
	- refers to the fraction of tuples selected by select condition
- Select operation is cumulative
`σ<c1>(σ<c2>(R)) = σ<c2>(σ<c1>(R))`

**The project operation (π)**
- selects certain columns (vertical partition) from the tables
- general format:
	- π{attribute list}({relation name})
- e.g. list each employee's first name, last name and salary
`πLNAME, FNAME, SALARY (EMPLOYEE)`

**The project operation: Properties
- degree of the relation is the number of attributes in the attribute list
- the cardinality of the result relation:
	- number of tuples <= |R(r)|

**More on Project**
- the resulting relation is the relation having the same number of attributes and the same order as specified in the attributes list
- does not hold commutatively property
	- π{list1}(π{list2}(R)) != π{list2}(π{list1}(R))
- duplicate tuples are removed
- e.g. `π sex, salary (EMPLOYEE)`
	- Fig 8.1.c
	 ![[Pasted image 20240220120039.png]]

**Sequence of Operations**
- relational operations can be applied in various ways:
	- using an in-line expression (a single complex expression)
	- using a sequence of simple expression
- E.g., retrieve the first name, last name and salary of all employees who work in dept 5
`π LNAME, FNAME, SALARY (σDNO=5 (EMPLOYEE))`
![[Pasted image 20240220120449.png]]

**Sequencing: Procedural approach**
- an alternative approach using sequencing and temporary tables

**Renaming (assigning)**
- rename the attributes