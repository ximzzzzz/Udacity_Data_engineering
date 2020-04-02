# lesson 1 : introduction to Data Modeling



## Relational Databases

> This model **organizes data into** one or more tables(of **'relations'**) **of columns and rows with a unique key**
>
> **identifying each row.** Generally, each table represents one 'entity type' (such as customer or product).
>
> A software system used to maintain relational databases is a relational database management system(RDBMS)



- Database/Schema
  - collection of tables
- Tables/ Relation
  - A group of rows sharing the same labeled elements (eg. customers)



## Advantages of using Relational Database

- ease of use -> SQL
- Ability to do JOINS
- Ability to do aggregations and analytics
- Smaller data volumes
- Easier to change business requirements
- Flexibility for queries
- Modeling the data not modeling queries
- Secondary Indexes available (city가 primary key 일때, 속도를 위해 city_code 를 secondary index로 사용할 수 있음)
- ACID Transactions  - data integrity (Atomicity, Consistency, Integrity, Durability)



## When to not use a Relational Database

-  Large amounts of data

- Need to be able to store different data type formats

- Need high throughput -> fast reads (ACID has benefit. but make it slow as well)

- Need a flexible schema (can allow for columns to be added that do not have to be used by every row )

- Need high availability (RDB is not distributed, it takes time if it break down and get back )

  ​	very little downtime of the system, it is always on and functioning

- Need horizontal scalability

  ​	ability to add more server to the system

  

## What is PostgreSQL?



