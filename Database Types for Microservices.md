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
* [Document (NoSQL)](#document-nosql)
* [Graph](#graph)
* [Key/Value](#key-value)
* [Time series](#time-series)
* [Search](#search)
* [Object (blob)](#object-blob)
* [Event sourcing](#event-sourcing)
* [Column store](#column-store)
* [Hybrid / Multi-Model](#hybrid-multi-model)

# Relational (SQL)
* Rows & Columns
* One big server
* Tables of consistent rows & columns
* ACID compliance
* SQL queris

```bash
        Pros                             Cons        
─────────────────────────────────────────────────────
 * Strong schema             * Optimized for storage
 * Table joins                 size (3rd normal form)
 * Very optimized engine     * Not designed to scale
 * Compatible, familiar        horizonally
   syntax                    * Vertical scaling gets
                               expensive
                             * Best with an ORM
                             * Need to migrate schema
```
