# lesson2

## Relational database 



## importance of Relational Databases

> Key Rule 1 : *The information rule*
>
> ​	all information in a relational database is represented explicitly at the logical level and in exactly one way 
>
> ​	by values in tables

- **Standardization of data model:** Once your data is transformed into the rows and columns format, your data is standardized and you can query it with SQL
- **Flexibility in adding and altering tables:** Relational databases gives you flexibility to add tables, alter tables, add and remove data.
- **Data Integrity:** Data Integrity is the backbone of using a relational database.
- **Structured Query Language (SQL):** A standard language can be used to access the data with a predefined language.
- **Simplicity :** Data is systematically stored and modeled in tabular format.
- **Intuitive Organization:** The spreadsheet format is intuitive but intuitive to data modeling in relational databases.





## What is OLAP vs OLTP?

**Online Analytical Processing (OLAP):**

- Databases optimized for these workloads allow for complex analytical and ad hoc queries, including aggregations. These type of databases are optimized for reads.

**Online Transactional Processing (OLTP):**

- Databases optimized for these workloads allow for less complex queries in large volume. The types of queries for these databases are read, insert, update, and delete.

> The key to remember the difference between OLAP and OLTP is analytics (A) vs transactions (T). If you want to get the -price of a shoe then you are using OLTP (this has very little or no aggregations). If you want to know the total stock of shoes a particular store sold, then this requires using OLAP (since this will require aggregations).
>
> **"OLTP queries will have little aggregations really, if any, while OLAP will heavily focus on aggregations."**



## Normalization, Denormalization

> **normalization**  : To reduce data redundancy and increase data integrity(*feel natural)*
>
> ​	data redundancy : don't want or need extra copies of our data
>
> ​	data integrity : we want to be able to update our data in one place and have that be the source of truth
>
> **denormalization** : Must be done in read heavy workloads to increase performance*(feel unnatural : make copy  for performance reason)* 





## Objectives of Normal Form

- To free the database from unwanted insertions, updates, & deletion dependencies

- To reduce the need for refactoring the database as new types of data are introduced

- To make the relational model more informative to users

- To make the database neutral to the query statistics



## Normal Forms

> most data modeling design just strive to achieve third normal form
>
> 4-6 is really just more for academic and research purposes

1. **How to reach First Normal Form (1NF):**

   - Atomic values: each cell contains unique and single values
   - Be able to add data without altering tables
   - Separate different relations into different tables
   - Keep relationships between tables together with foreign keys

2. **Second Normal Form (2NF):**

   - Have reached 1NF
   - All columns in the table must rely on the Primary Key

3. **Third Normal Form (3NF):**

   - Must be in 2nd Normal Form
   - No transitive dependencies
   - Remember, transitive dependencies you are trying to maintain is that to get from A-> C, you want to avoid going through B.

   **When to use 3NF:**

   - When you want to update data, we want to be able to do in just 1 place. We want to avoid updating the table in the Customers Detail table (in the example in the lecture slide).



## Fact and Dimension Tables

> work together to create an organized data model
>
> while fact and dimension are not created differently in the DDL, 
>
> they are conceptual and extremely important for organization

- Fact tables : consists of the measurements, metrics of facts of a business process

  ​						fact table can be aggregations of data,  but are not meant to be updated in place like a dimension.

- Dimension : a structure that categorizes facts and measures in order to enable users to answer business questions.

  ​					dimensions are people, products, place and time



## Star schema

1. Benefits

   - Denormalized

   - Simplifies queries
   - Fast aggregations

2. Drawbacks
   - issues that come with denormalization(data integrity, ...)
   - Decrease query flexibility
   - Many to many relationship -- simplified

## 

## Snowflake Schema

> Logical arrangement of tables in a multidimensional database represented by centralized fact tables 
>
> which are connected to multiple dimensions.



## Snowflake vs Star

- Star schema is a special, simplified case of the snowflake schema.
- Star schema does not allow for one to many relationships while the snowflake schema does
- Snowflake schema is more normalized than Star. but only in 1NF or 2NF