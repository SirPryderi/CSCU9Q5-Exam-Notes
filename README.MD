# Table of Contents
* [The Relational Model](#the-relational-model)
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

### Foreign Key
A foreign key is an attribute (or set of attributes) in one table,
that uniquely identifies a row of another table or the same table.



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
