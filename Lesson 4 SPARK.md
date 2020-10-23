# Lesson 4 SPARK



## Numbers everyone should know

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