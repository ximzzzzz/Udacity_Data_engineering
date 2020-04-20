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



