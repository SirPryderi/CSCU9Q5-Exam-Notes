# Table of Contents
* [The Relational Model](#the-relational-model)
  * [Terminology](#terminology)
  * [Properties of Relation](#properties-of-relation)
  * [Keys](#keys)
    * [Superkeys](#superkeys)
    * [Candidate Keys](#candidate-keys)
    * [Primary Key](#primary-key)
    * [Foreign Key](#foreign-key)
  * [Relational Database Schema](#relational-database-schema)
  * [Nulls](#nulls)
  * [Entity Rules](#entity-rules)
    * [Entity Integrity Rule](#entity-integrity-rule)
    * [Referential Integrity Rule](#referential-integrity-rule)
* [Entity Relationship Modelling](#entity-relationship-modelling)
* [SQL](#sql)
  * [SQL Syntax](#sql-syntax)
    * [SQL Data Types](#sql-data-types)
      * [Numeric Data Types](#numeric-data-types)
      * [String Types](#string-types)
      * [Dates](#dates)
      * [Misc Types](#misc-types)
    * [Create Table](#create-table)
    * [Alter Table](#alter-table)
    * [Drop a table](#drop-a-table)
    * [Truncate a table](#truncate-a-table)
    * [Insert in a table](#insert-in-a-table)
    * [Updating a table](#updating-a-table)
    * [Joins](#joins)
    * [Groups](#groups)
* [Relational Algebra](#relational-algebra)
  * [SQL Equivalents](#sql-equivalents)
  * [Operators](#operators)
    * [Restriction](#restriction)
    * [Projection](#projection)
    * [Product](#product)
    * [Joins](#joins)
      * [Natural Join](#natural-join)
    * [Union](#union)
    * [Difference](#difference)
* [Normalisation](#normalisation)
  * [Anomalies](#anomalies)
  * [Functional Dependency](#functional-dependency)
  * [First Normal Form](#first-normal-form)
  * [Second Normal Form](#second-normal-form)
  * [Third Normal Form](#third-normal-form)
* [ANSI-SPARC](#ansisparc)
* [Concurrency](#concurrency)
  * [Transactions](#transactions)
  * [Locks](#locks)
* [Backup](#backup)
* [Recovery](#recovery)
* [Administering Databases](#administering-databases)
  * [Data Dictionary](#data-dictionary)
  * [Data Administrator](#data-administrator)
  * [Database Administrator](#database-administrator)
  * [Distributed Databases](#distributed-databases)

# The Relational Model
The relational model was proposed by the mathematician Edward Codd in 1970.
This model has a strong theoretical and mathematical foundation to back its functioning.

## Terminology
- **Relation** ─ A two-dimensional table. AKA File.
- **Row** ─ An individual row of the table. AKA Record, Tuple.
- **Attribute** ─ A named column of a relation. AKA Field.
- **Cardinality** ─ Number of rows.
- **Degree** ─ Number of columns.
- **Domain** ─ A set of allowed values of a specific attribute.

## Properties of Relation
- The name of the relation is unique.
- The names of an attribute in unique only within its relation.
- The values of an attribute are all from the same domain.
- The order of attributes within a relation has no significance.
- The order of rows within a relation has no significance.
- The records within a relation should all be distinct.
- Each cell of a relation should contain at most _one value_.

## Keys
Keys are attributes used to uniquely identify one a row.

### Superkeys
A **superkey** is any attribute (or set of attributes) that uniquely identifies a row.

### Candidate Keys
A **candidate key** is a minimal _super key_, i.e. does not have any superfluous attribute.
More specifically, A _superkey_ is minimal if removing any attributes would mean that it no
longer provides unique identification.

A table often has more than one candidate key.

A candidate key has the following properties:
- **Uniqueness** ─ No two rows of the table can have the same value of the candidate key.
- **Irreducibility** ─ No subset of the candidate key has the _uniqueness_ property.

### Primary Key
A **primary key** is a candidate key that has been chosen to be the default way of identifying a row.
If there is no natural attribute suitable as primary key, a **surrogate key** can be generated.

### Foreign Key
A foreign key is an attribute (or set of attributes) in one table,
that uniquely identifies a row of another table or the same table.

## Relational Database Schema
To represent the conceptual schema for a relational database,
the following notation can be used to describe a table:

  ```
  relational_name(_attribute1_, attribute2, ..., attributeN)
  ```

Note: those underscores are an attempt at showing an underline, to identify the primary key.

## Nulls
`null` is a value that can be assigned to a cell to specify that its content has not been assigned.
This differs significantly to setting it to `0` or `""` (empty string).

## Entity Rules
### Entity Integrity Rule
In a relation, no attribute of a primary key can be `null`.

### Referential Integrity Rule
If a relation contains a foreign key, either the foreign key value must
match the value of a primary key of a record in the home relation,
or the foreign key must be `null`.

Now for humans, and other semi-intelligent species: no foreign key referencing to something that is not there.

# Entity Relationship Modelling
# SQL
- **SQL** (Structured Query Language) is a declarative language for manipulating a relational database.
- **MySQL** is a particular dialect of the SQL language.

## SQL Syntax
Although not mandatory, it is good practice to write reserved words UPPERCASE in SQL, and wrap database elements name between backwards quotes (\`).

Example of fussily written SQL query:

```SQL
SELECT `morty_id` FROM `standard_finite_curve_table` WHERE `id` = 'C-137';
```

### SQL Data Types
Some of the most used data types in SQL.

| Type    | Description                 |
| :-------| :---------------------------|
| VARCHAR | String of variable length   |
| INT     | Integer numbers             |
| DECIMAL | Numbers with decimal places |
| DATE    | A full date                 |
| TEXT    | A long string of text       |
| BOOLEAN | Single binary value         |

More data Types
#### Numeric Data Types
**Integers**

| Type      | Size    |
| :---------| :-------|
| TINYINT   | 1 byte  |
| SMALLINT  | 2 bytes |
| MEDIUMINT | 3 bytes |
| INT       | 4 bytes |
| BIGINT    | 8 bytes |


**Floating Point**

| Type   | Size    |
| :------| :-------|
| FLOAT  | 4 bytes |
| DOUBLE | 8 bytes |


**Fixed Point**

| Type               | Size                           |
| :------------------| :------------------------------|
| NUMERIC or DECIMAL | depends on precision and scale |

**Boolean** is implemented as a _tinyint_.

#### String Types
- CHAR (length)
- VARCHAR (length)

#### Dates
- DATETIME
- DATE
- TIME
- YEAR

#### Misc Types
- ENUMERATIONS
- SETS
- BLOB
- TEXT

### Create Table
The following syntax can be used to create a new table in the database.

```SQL
CREATE TABLE `Staff` (
  `id`          INT,
  `name`        VARCHAR(20),
  `length`      INT,
  `damage`      FLOAT,
  `wooden`      BOOLEAN
);
```

### Alter Table
The following syntax can be used to edit the structure of a table
already in the database.

```SQL
  ALTER TABLE `Staff` ADD (
    `has_nails` BOOLEAN
  );

  ALTER TABLE `Staff` MODIFY (
    `length` FLOAT
  );
```

### Drop a table
**Dropping** a table means deleting its data and structure. You have been warned.

```SQL
DROP TABLE tablename;
```

### Truncate a table
**Truncating** a table means deleting its data only. You have been warned anyway.

```SQL
TRUNCATE TABLE tablename;
```

### Insert in a table
INSERT can be used to populate the table with some data.

This syntax follows the order of the attributes.
```SQL
INSERT INTO `Staff` VALUES (
    1,
    "Mighty Fire Staff",
    2,
    50.4
)
```

### Updating a table
Tables can be updated with the following syntax.

```SQL
UPDATE `Staff` SET `name`="My Mighty Fire Staff" WHERE `id` = 1;
```

### Joins
When selecting you can join the result from two or more tables using a JOIN.

```SQL
SELECT Staff.name Element.name FROM Staff
  INNER JOIN Element ON Staff.element_id = Element.id;

```

### Groups
Yeah, you can group stuff. I can't teach you everything, read a book or something.

# Relational Algebra
Relational algebra provides a theoretical foundation for relational databases,
particularly for query languages, such as SQL.

The main five operators in Relational Algebra are:
- **Restriction**
- **Projection**
- **Union**
- **Difference**
- (Cartesian) **Product**

From which are derived the remaining three:
- **Join**
- **Intersection**
- **Division**

## SQL Equivalents
This table has the only aim of saving your life,
so you better say `thanks` to it.

| Relational algebra | SQL                   | UGLY Math Symbol |
| :------------------| :---------------------| :----------------|
| RESTRICT           | WHERE                 | σ                |
| PROJECT            | SELECT DISTINCT       | π                |
| UNION              | UNION                 | ∪ _or_  +        |
| DIFFERENCE         | NOT IN (SELECT ...)   | −                |
| PRODUCT            | SELECT table1, table2 | ×                |
| JOIN               | JOIN                  | ⋈                |
| INTERSECTION       | IN (SELECT ...)       | ∩                |
| DIVISION           | -                     | ÷                |

## Operators
![Relational Algebra Operators][RelationalAlgebraOperators]

### Restriction
The restriction operator works on a single relation _R_
and defines a new relation that contains only those rows
of R that satisfy some specified condition _C_.

In other words, makes a subset of _R_ that satisfy the condition _C_.

```
RESTRICT R TO C
```

### Projection
The projection operator works on a single relation _R_ and defines a relation
that contains a subset of the columns of _R_.

In other words, you just select one or more column.

```
PROJECT ColumnsList FROM R
```

### Product
The product operator produces a table with the concatenation of every row of _R_ with every row of _S_.

```
R × S
```

Combining a **Product** and a **Restriction** you get a **Join**! Just like Minecraft.

### Joins
Joins are used to concatenate tables given a particular condition.
There are various types of joins, like Natural Join, Equi-join, Outer Join, Semi-join.

#### Natural Join
It is usually used to join a foreign key with the values of its referencing rows.
For example, if you get the department name, when you are selecting a table of employees that contains a foreign key towards the department table.

```
R ⋈ S
```

### Union
The union operator of two relations _R_ and _S_ is obtained by pooling
their rows into one relation.

```
R ∪ S
```

### Difference
The difference operator defines a relation consisting of all rows that are in
the relation _R_, but not in the relation _S_.

```
R ─ S
```

# Normalisation

## Anomalies
Anomalies are inconvenient or error-prone situation arising when we process the tables. There are three types of anomalies:

- **Update Anomalies** ─ when one or more instances of duplicated data is updated, but not all.
- **Delete Anomalies** ─ when certain attributes are lost because of the deletion of other attributes.
- **Insert Anomalies** ─ when certain attributes cannot be inserted into the database without the presence of other attributes.

In order to address these issues, the only and true Codd gave us normalisation rules.

> For Codd so loved the world, that he gave his Normalisation Rules,
> that whoever believes in him should not perish in redundancy and anomalies,
> but have eternal consistency.
>
> ─ John 3:16

## Functional Dependency
In any relation a column (or set of columns) Y is _functionally dependant_
on a column (or set of columns) X if at any one time exactly one Y value is associated with any X value. Note that a functional dependency only goes one way.

A functional dependency is expressed with the notation `X → Y`;

Example: `UserId → UserName`

## First Normal Form
A relation is in 1NF if no entry consists of more than one value
(i.e. does not have repeating groups)

## Second Normal Form
A relation is in 2NF if:
  - it is in 1NF
  - every non-key column is fully functional-dependent on the primary key

## Third Normal Form
A relation is in 3NF if:
  - it is in 2NF
  - every non-key column is non-transitively
    fully functional-dependant on the primary key

# ANSI-SPARC
Maybe one day I'll read those slides. BUT IT IS NOT THIS DAY!

# Concurrency

##  Transactions
A **transaction** is an action or series of actions, carried out by a single
user or application program, which accesses or changes the content of
the database.

A transaction should always transform the database towards a
consistent state.

If a transaction completes successfully, it is made persistent, this process
is called a _commit_.
If a transaction fails, it is reverted, and this is called
_roll-back_.
This way, the database is always consistent at the end of a transaction, regardless
of its success.

Transaction should be ACID, meaning with a pH lower than `7`.
No, seriously ACID stands for:

- **Atomicity** ─ A transaction is an indivisible unit that is either performed
in its entirety, or not performed at all.
- **Consistency** ─ A transaction transforms the database from one consistent state to another.
- **Independence** ─ The transactions execute Independently from one another. In other words the effects of an incomplete transaction are invisible to the others.
- **Durability** ─ The effect of a committed transaction are permanent and must not be loss because of a failure.

## Locks

In order to prevent issues with concurrent transactions, a lock can be used to
prevent two transaction to access/write the same data at the same time.
There are two types of lock:
- **Read Lock** ─ _Shared_ lock that prevents other transaction to write.
- **Write Lock** ─ _Exclusive_ lock that prevents other transaction to read and write.

As usual, every time you fix one thing, you break another, and locks can conduce
to a **dead lock**, or a loop of transaction blocking each other to access a
resource. To overcome this issue, transactions should request all the locks
at the beginning (**growing phase**), and release all the locks at the of the
transaction. I heard that in case of dead-lock, pull the plug might be a good
option, but don't take my word for it.

# Backup

# Recovery

# Administering Databases
## Data Dictionary
- A DBMS must provide facilities to allow users to find out the properties
of the stored items (metadata).
- These facilities may also be used by components of the DBMS itself.
- The Data Dictionary must hold information about the tables, view, forms, queries and reports stored in the database.

## Data Administrator
Within any organisation using a shared DBMS, we will expect to find a Database Administrator (DBA).
At the very minimum, the DBA will be responsible for the orderly running of the program.
For instance, an instance of oracle runs at all the time.
However, in most organisations, many users will be sharing data, and the shared database will be crucial to the core business.

The data may be divided into different systems ─ for example the University has:
- Finance
- Student records
- Recruitment and Admissions

Under these circumstances managerial role of the IS professional would be very important.

## Database Administrator
There is often a distinction between the roles of the Database Administrator
and the Data Administrator, both of which have specific responsibilities that complement each other.
The Data Administrator has more strategic and managerial role.
The Database Administrator has more technical role.

## Distributed Databases

- **Distributed Database**
  - A logically interrelated collection of shared data, physically distributed over a computer network.
  - Could be across two computers in the same room or across the world.
  - Under the control of more than one CPU.
- **Distributed Database Management System**
  - Software system that permits the management of the distributed database and makes the distribution transparent to users.


[RelationalAlgebraOperators]: https://www.safaribooksonline.com/library/view/relational-theory-for/9781449365431/httpatomoreillycomsourceoreillyimages1665827.png.jpg
