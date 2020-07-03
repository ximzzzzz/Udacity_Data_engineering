# NoSQL Data Models



## 2. Non Relational Databases

> NoSQL and Non-Relational are interchangeable terms.
>
> NoSQL = Not Only SQL



### When Not to Use SQL:

- **Need high Availability in the data**: Indicates the system is always up and there is no downtime
- **Have Large Amounts of Data**
- **Need Linear Scalability**: The need to add more nodes to the system so performance will increase linearly
- **Low Latency**: Shorter delay before the data is transferred once the instruction for the transfer has been received.
- **Need fast reads and write**

### 

### Apache Cassandra

- masterless architecture
- linearly scalable
- open source



### Eventual Consistency

Over time (if no new changes are made) each copy of the data will be the same, but if there are new changes, the data may be different in different locations. The data may be inconsistent for only milliseconds. There are workarounds in place to prevent getting stale data.





### CAP Theorem

> A theorem in computer science that states it is **impossible** for a distributed data store to **simultaneously provide** more than two out of the following three guarantees of **consistency, availability** and **partition tolerance**

- **Consistency**: Every read from the database gets the latest (and correct) piece of data or an error
- **Availability**: Every request is received and a response is given -- without a guarantee that the data is the latest update
- **Partition Tolerance**: The system continues to work regardless of losing network connectivity between nodes



### WHERE clause

- Data Modeling in Apache Cassandra is query focused, and that focus needs to be on the WHERE clause
- Failure to include a WHERE clause will result in an error

### Additional Resource

AVOID using "ALLOW FILTERING": Here is a reference [in DataStax](https://www.datastax.com/dev/blog/allow-filtering-explained-2) that explains ALLOW FILTERING and why you should not use it.