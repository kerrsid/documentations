# Introduction

We know that each microservice owns its data. A microservice owns its own data that micro database is exclusivelt owned by that serrvice and if the service no longer needs it the that micro database is obsolete and can ve removed.

What's really interesting is each of these micro databases can be optimized for the task at hand. They don't all need to be same type of database vendor or database type. 


* Characteristics
* Pros
* Cons
* Best use-cases
* Examples

# Contents
* [Relational (SQL)](#relational-sql)
* [Document Databases (NoSQL)](#document-databases-nosql)
* [Graph](#graph)
* [Key/Value](#key-value)
* [Time series](#time-series)
* [Search](#search)
* [Object (blob)](#object-blob)
* [Event sourcing](#event-sourcing)
* [Column store](#column-store)
* [Hybrid / Multi-Model](#hybrid-multi-model)

# Relational (SQL)
```
                Pros                             Cons        
────────────────────────────────────────────────────────────────────────      Characteristics
   ● Strong schema                 ● Optimized for storage size (3rd          ● Rows & Columns     
   ● Table joins                     normal form)                             ● One big server
   ● Very optimized engine         ● Not designed to scale horizonally        ● Tables of consistent rows & columns
   ● Compatible, familiar          ● Vertical scaling gets expensive          ● ACID compliance
     syntax                        ● Best with an ORM                         ● SQL queris
                                   ● Need to migrate schema
                                   
Best use-case: Most everything
Examples: SQL Server, Oracle, PostgreSQL
```
# Document Databases (NoSQL)
```
                Pros                             Cons        
────────────────────────────────────────────────────────────────────────      Characteristics
   ● Distributed                        ● Denormalized means data             ● JSON documents 
   ● No schema:                           duplication                         ● Distributed (many machines)
      ■ Different documents have        ● SDKs for each language              ● Optimized for reads  
        different fields                ● Query language is weird             ● Eventual consistency
   ● Denormalized means faster          ● No transactions
     reads                              ● No joins
                                        ● No schema:
                                           ■ App assumes a schema
                                           ■ Query missing nested field
                                           
Best use-case: Need to render exactly one very fast
    ● product catalog
    ● news site
    ● CMS
Examples: MongoDB, Firebase
```
