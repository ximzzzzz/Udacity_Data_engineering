# Lesson 4-2 Data Wrangling with Spark



## 1. functional programming <-> procedure programming(like for Loop)

## 2. why use functional programming : perfect for distributed systems

- functional programming gets its name from the functions you saw in your algebra class. 

- these functions are more strict than your average python function.
- because in math, function can give you only one answer when you give it an input

Python is not a functional programming language.  Then how is it possible that Spark programs can be written in Python if Python is not a functional programming language?

> ​	The PySpark API allows you to write programs in Spark and ensures that your code uses functional programming practices. Underneath the hood, the Python code uses py4j to make calls to the Java Virtual Machine (JVM).



## 3. DAG( Directed Acyclical Graph)

​	lazy evaluation, once spark builds the DAG from your code, it checks if it can procrastinate(미루다) waiting 

​	until the last possible moment to get the data

​	also  in spark , multi-step combos(function) are called stages

## 4. maps

​	in Spark, maps take data as input and then transform that data with whatever function you put in the map. They are 		like directions for the data telling how each input should get to the output. The first code cell creates a SparkContext 		object. With the SparkContext, you can input a dataset and parallelize the 

​	data across a cluster (since you are currently using Spark in local mode on a single machine, technically the dataset 	isn't distributed yet).



## 5. imperative(Spark DataFrames & Python) vs Declarative(SQL) programming

- loose definition(difference) 
  - imperative focus on 'HOW' -> get in to the car and go to bakery two miles away from here ....
  - Declarative focus on 'What' -> let's get cakes for my sister's birthday
- in most cases, Declarative systems are an abstraction layer of an imperative system that takes care of figuring out the necessary steps to achieve the result