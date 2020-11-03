# Lesson 4-2 Data Wrangling with Spark



## 1. functional programming <-> procedure programming(like for Loop)

## 2. why use functional programming : perfect for distributed systems

- functional programming gets its name from the functions you saw in your algebra class. 

- these functions are more strict than your average python function.
- because in math, function can give you only one answer when you give it an input

Python is not a functional programming language.  Then how is it possible that Spark programs can be written in Python if Python is not a functional programming language?

> ​	The PySpark API allows you to write programs in Spark and ensures that your code uses functional programming practices. Underneath the hood, the Python code uses py4j to make calls to the Java Virtual Machine (JVM).