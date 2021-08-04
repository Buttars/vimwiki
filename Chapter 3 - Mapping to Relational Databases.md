# Mapping to Relational Databases

[##](##) Architectural Patterns

One class per database table

This is a __Database Gateway__

__Row Data Gateway__ is when you have a class for each row returned for a query.

__Record Set__ a generic data structure of tables and rows that mimics tabular databases.

__Tabular Data Gateway__ allows you to query the DB and returns a Record Set

When using __Domain Model__ there will be one domain class per table.

__Active Record__ is when you have an object per table that contains moderately complex business logic.

Another way of thinking about Active Record is starting with Row Data Gateway and adding business logic.

__Data Mapper__ is responsible for mapping data between the database and domain layers.

## The Behavioral Problem

__Unit of Work__ introduces a commit style flow to saving data to the DB. It keeps track of all the objects read and updated and stores them all in one place. A programmer would then tell the Unit of Work to commit the changes to the DB.

Without an explicitly defined __Unit of Work__ the __Domain Layer__ acts as the controller deciding when to read and write to the DB.

A Unit of Work results from factoring the database mapping controller behavior (the read/write logic) into it's own object.

An __Identity Map__ keeps a reference to each row loaded into memory preventing duplicate loading/updating. If data is already loaded into memory the Identity Map will return a reference to it ensuring updates are properly coordinated.

Identity Map doubles as a DB cache.

Identity Map's main purpose is to maintain correctness not boost performance so a cache may still be required.

__Lazy Loading__ objects is when there's placeholder reference on an object instead of the object itself. Only if you try to follow the reference does the data load.

## Reading in Data

Prefer single queries that return more than enough data but be careful to not lock up too many rows while doing so.

## Structural Mapping Patterns
