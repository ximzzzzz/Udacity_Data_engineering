# Lesson 4-3 Setting up Spark Clusters with AWS



Spark Cluster Managers

- standalone, mesos, yarn
- mesos, yarn are for sharing a spark cluster across an entire team of engineers and analysts

데이터가 작은경우엔 cpu -> ram -> ssd 가 한 컴퓨터에 있고 ssd에서 ram으로 데이터를 로드한 뒤 필요에 따라 cpu에서 사용하는 방식인데,

빅데이터의 경우 한 컴퓨터에서 처리할 수 없기 때문에 각 역할을 담당하는 곳에서 가져와야한다



### Overview of the Set up of a Spark Cluster

1. **Amazon S3** will store the dataset.
2. We rent a cluster of machines, i.e., our **Spark Cluster**, and it is located in AWS data centers. We rent these using AWS service called **Elastic Compute Cloud (EC2)**.
3. We log in from your local computer to this Spark cluster.
4. Upon running our Spark code, the cluster will load the dataset from **Amazon S3** into the cluster’s memory distributed across each machine in the cluster.

![l4-3](https://user-images.githubusercontent.com/44566113/99043506-ad405880-25d1-11eb-90a7-59c613614ae7.JPG)

#### New Terms:

- **Local mode**: You are running a Spark program on your laptop like a single machine.
- **Standalone mode**: You are defining Spark Primary and Secondary to work on your (virtual) machine. You can do this on EMR or your machine. Standalone mode uses a resource manager like YARN or Mesos.



### EC2 vs EMR

|                                | **AWS EMR**                                                  | **AWS EC2**                                                  |
| :----------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Distributed computing**      | Yes                                                          | Yes                                                          |
| **Node categorization**        | Categorizes secondary nodes into core and task nodes as a result of which data can be lost in case a data node is removed. | Does not use node categorization                             |
| **Can support HDFS?**          | Yes                                                          | Only if you configure HDFS on EC2 yourself using multi-step process. |
| **What protocol can be used?** | Uses S3 protocol over AWS S3, which is faster than s3a protocol | ECS uses s3a                                                 |
| **Comparison cost**            | Bit higher                                                   | Lower                                                        |



### Circling back about HDFS

Previously we have looked over the Hadoop Ecosystem. To refresh those concepts, we have provided reference material here. HDFS (Hadoop Distributed File System) is the file system. HDFS uses MapReduce system as a resource manager.

Spark can replace the MapReduce algorithm. Since Spark does not have its own distributed storage system, it leverages using HDFS or AWS S3, or any other distributed storage. Primarily in this course, we will be using AWS S3, but let’s review the advantages of using HDFS over AWS S3.

### What is HDFS?

HDFS (Hadoop Distributed File System) is the file system in the Hadoop ecosystem. Hadoop and Spark are two frameworks providing tools for carrying out big-data related tasks. While Spark is faster than Hadoop, Spark has one drawback. It lacks a distributed storage system. In other words, Spark lacks a system to organize, store and process data files.

### MapReduce System

HDFS uses MapReduce system as a resource manager to allow the distribution of the files across the hard drives within the cluster. Think of it as the MapReduce System storing the data back on the hard drives after completing all the tasks.

Spark, on the other hand, runs the operations and holds the data in the RAM memory rather than the hard drives used by HDFS. Since Spark lacks a file distribution system to organize, store and process data files, Spark tools are often installed on Hadoop because Spark can then use the Hadoop Distributed File System (HDFS).

### Why do you need **EMR Cluster**?

Since a Spark cluster includes multiple machines, in order to use Spark code on each machine, we would need to download and install Spark and its dependencies. This is a manual process. **Elastic Map Reduce** is a service offered by AWS that negates the need for you, the user, to go through the manual process of installing Spark and its dependencies for each machine.





![AWS CLI](https://video.udacity-data.com/topher/2020/May/5ec81111_dend-refresh-02-1/dend-refresh-02-1.png)



### Why use AWS CLI?

AWS CLI enables you to run commands that allow access to currently available AWS Services. We can also use AWS CLI to primarily create and check the status of our EMR instances. Mostly during your work, you would normally create clusters that are similar in sizes and functionalities, and it can get tedious when you use the AWS console to create a cluster. If you have a pre-generated script to generate EMR saved to your text editor, you can re-run as often as you’d like to generate new clusters. This way we can bypass setting security groups and roles through AWS console. You can embed all these features, including selecting number of cores, applications to install, and even custom script to execute at the time of cluster launch by using a pre-generated script.