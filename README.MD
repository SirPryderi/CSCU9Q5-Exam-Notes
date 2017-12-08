# Table of Contents
* [The Relational Model](#the-relational-model)
  * [Terminology](#terminology)
  * [Properties of Relation](#properties-of-relation)
  * [Keys](#keys)
    * [Superkeys](#superkeys)
    * [Candidate Keys](#candidate-keys)
    * [Foreign Key](#foreign-key)
* [Entity Relationship Modelling](#entity-relationship-modelling)
* [SQL](#sql)
* [Relational Algebra](#relational-algebra)
* [Normalisation](#normalisation)
* [Java and MySQL](#java-and-mysql)
* [SQL3 Data Types](#sql3-data-types)
* [ANSI-SPARC](#ansisparc)
* [Backup](#backup)
* [Concurrency](#concurrency)
* [Recovery](#recovery)
* [Administering Databases](#administering-databases)

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
# Relational Algebra
# Normalisation
# Java and MySQL
# SQL3 Data Types
# ANSI-SPARC
# Backup
# Concurrency
# Recovery
# Administering Databases
