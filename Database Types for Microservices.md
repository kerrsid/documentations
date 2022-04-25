# Introduction

A microservice owns its own data that micro database is exclusively owned by that service and if the service no longer needs it that micro database is obsolete and can be removed.

What's really interesting is each of these micro databases can be optimized for the task at hand. They don't all need to be the same type of database vendor or database type. 


* Characteristics
* Pros
* Cons
* Best use-cases
* Examples

# Contents
* [Relational (SQL)](#relational-database-sql)
* [Document (NoSQL)](#document-databases-nosql)
* [Graph](#graph-databases)
* [Key/Value](#keyvalue-databases)
* [Time series](#time-series)
* [Search](#search)
* [Object (blob)](#object-blob)
* [Event sourcing](#event-sourcing)
* [Column store](#column-store)
* [Hybrid / Multi-Model](#hybrid-multi-model)

# Relational Database (SQL)
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
# Graph Databases
```
                Pros                             Cons        
────────────────────────────────────────────────────────────────────────      Characteristics
   ● Fast to join across                 ● Doesn't do other things            ● Focus is on connections
     relationships                         well                               ● Two object types:
    E.g. friends of friends               E.g. cross-table joins are            ■ nodes
                                            really expensive                    ■ relationships
                                            
Best use-case: 
    ● messaging apps
    ● social networks
    ● recommendation engine
Examples: Neo4j
```
# Key/Value Databases
```
                Pros                             Cons        
────────────────────────────────────────────────────────────────────────     Characteristics
 ● Really fast for "by id" queries    ● Can't query by non-key fields:       ● Given a key, read or write a value
 ● Can store different data in          It's just a binary blob              ● Often the data is a JSON object or text blob
   each record (schema-less)                                                 ● Think: a table with two columns:
                                                                                        ■ a primary key
                                                                                        ■ a binary blob
                                                                                        
Best use-case: 
    ● cache
    ● configuration
    ● user session data
Examples: Redis, Memcached
```
