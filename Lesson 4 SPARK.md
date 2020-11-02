# Lesson 4 SPARK



## 1. Numbers everyone should know

- ## GENERAL

### 	CPU : THE BRAIN OF YOUR COMPUTER 

​	CPU operation : 0.4 ns (fastest)

### 	MEMORY : place to store data before it goes to your cpu, 

### 						your computer's scratch paper(스케치북) for helping with more complicated calculations

​		MEMORY REFERENCE : 100 ns (second)

### 	STORAGE : THE FILE CABINET FOR DATA

​		RANDOM READ FROM SSD : 16 mu second

### 	NETWORK : ACCESS TO OUTSIDE WORLD 

​		ROUND TRIP FOR DATA FROM EU TO US : 150 ms



- ## CPU

  The CPU can also store small amounts of data inside itself in what are called **registers**. These registers hold data that the CPU is working with at the moment.

  The registers make computations more efficient: the registers avoid having to send data unnecessarily back and forth between memory (RAM) and the CPU.

  2.5 GHz CPU means it can handle 2.5 billion(십억) operations per second.

  and in lecture, it assumes for each operation, the cpu processes 8 byes of data. 

  so they can assume cpu processes 20 billion bytes per second

- ## memory

  memory takes 250x longer than the CPU

  characteristics of memory

  - Efficient : for feeding our CPU's data

  - Ephemeral : lose all the data everytime shut down machine

  - Expensive : google bypass this problem by building distributed systems using **commodity hardware**(a computer that you and i would buy if we're on tight budget)

    rather than relying on lots of memory, google leveraged **long-term storage** on cheap pre-used hardware



- ## storage

  long-term storage like a hard drive disk is cheap and durable. but much slower than memory.

  loading data from magnetic disk can be 200 times slower.

  even the newer solid-state drives known as SSD are 15 times slower

- ## network

  Transferring data across a network, ie between computers, is the biggest bottleneck when working with big data.

  distributed systems try to minimize shuffling data back and forth across different computers

  (use the cluster of servers connected by a network)

  One of the advantages of Spark is that it only shuffles data between computers when it absolutely has to.





2. ## MapReduce

   

   MapReduce is a programming technique for manipulating large data sets. "Hadoop MapReduce" is a specific implementation of this programming technique.

   The technique works by first dividing up a large dataset and distributing the data across a cluster. In the map step, each data is analyzed and converted into a (key, value) pair. Then these key-value pairs are shuffled across the cluster so that all keys are on the same machine. In the reduce step, the values with the same keys are combined together.

   While Spark doesn't implement MapReduce, you can write Spark programs that behave in a similar way to the map-reduce paradigm. In the next section, you will run through a code example.

   

## 3. Spark Use Cases and Resources

Here are a few resources about different Spark use cases:

- [Data Analytics](http://spark.apache.org/sql/)
- [Machine Learning](http://spark.apache.org/mllib/)
- [Streaming](http://spark.apache.org/streaming/)
- [Graph Analytics](http://spark.apache.org/graphx/)



## You Don't Always Need Spark

Spark is meant for big data sets that cannot fit on one computer. But you don't need Spark if you are working on smaller data sets. In the cases of data sets that can fit on your local computer, there are many other options out there you can use to manipulate data such as:

- [AWK](https://en.wikipedia.org/wiki/AWK) - a command line tool for manipulating text files
- [R](https://www.r-project.org/) - a programming language and software environment for statistical computing
- [Python PyData Stack](https://pydata.org/downloads.html), which includes pandas, Matplotlib, NumPy, and scikit-learn among other libraries

Sometimes, you can still use pandas on a single, local machine even if your data set is only a little bit larger than memory. Pandas can read data in chunks. Depending on your use case, you can filter the data and write out the relevant parts to disk.

If the data is already stored in a relational database such as [MySQL](https://www.mysql.com/) or [Postgres](https://www.postgresql.org/), you can leverage SQL to extract, filter and aggregate the data. If you would like to leverage pandas and SQL simultaneously, you can use libraries such as [SQLAlchemy](https://www.sqlalchemy.org/), which provides an abstraction layer to manipulate SQL tables with generative Python expressions.

The most commonly used Python Machine Learning library is [scikit-learn](http://scikit-learn.org/stable/). It has a wide range of algorithms for classification, regression, and clustering, as well as utilities for preprocessing data, fine tuning model parameters and testing their results. However, if you want to use more complex algorithms - like deep learning - you'll need to look further. [TensorFlow](https://www.tensorflow.org/) and [PyTorch](https://pytorch.org/) are currently popular packages.



## Spark's Limitations

Spark has some limitation.

Spark Streaming’s latency is at least 500 milliseconds since it operates on micro-batches of records, instead of processing one record at a time. Native streaming tools such as [Storm](http://storm.apache.org/), [Apex](https://apex.apache.org/), or [Flink](https://flink.apache.org/) can push down this latency value and might be more suitable for low-latency applications. Flink and Apex can be used for batch computation as well, so if you're already using them for stream processing, there's no need to add Spark to your stack of technologies.

Another limitation of Spark is its selection of machine learning algorithms. Currently, Spark only supports algorithms that scale linearly with the input data size. In general, deep learning is not available either, though there are many projects integrate Spark with Tensorflow and other deep learning tools.



## Hadoop versus Spark

The Hadoop ecosystem is a slightly older technology than the Spark ecosystem. In general, Hadoop MapReduce is slower than Spark because Hadoop writes data out to disk during intermediate steps. However, many big companies, such as Facebook and LinkedIn, started using Big Data early and built their infrastructure around the Hadoop ecosystem.

While Spark is great for iterative algorithms, there is not much of a performance boost over Hadoop MapReduce when doing simple counting. Migrating legacy code to Spark, especially on hundreds of nodes that are already in production, might not be worth the cost for the small performance boost.



## Beyond Spark for Storing and Processing Big Data

Keep in mind that Spark is not a data storage system, and there are a number of tools besides Spark that can be used to process and analyze large datasets.

Sometimes it makes sense to use the power and simplicity of SQL on big data. For these cases, a new class of databases, know as NoSQL and NewSQL, have been developed.

For example, you might hear about newer database storage systems like [HBase](https://hbase.apache.org/) or [Cassandra](http://cassandra.apache.org/). There are also distributed SQL engines like [Impala](https://impala.apache.org/) and [Presto](https://prestodb.io/). Many of these technologies use query syntax that you are likely already familiar with based on your experiences with Python and SQL.

In the lessons ahead, you will learn about Spark specifically, but know that many of the skills you already have with SQL, Python, and soon enough, Spark, will also be useful if you end up needing to learn any of these additional Big Data tools.