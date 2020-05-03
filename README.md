# Assignment4 - Introduction to Spark

Hi!

In this repository, we will get our hand's dirty with Spark. 

This assignment has the same tasks and goals as previous assignment, but this time, we will utilize [Apache Spark](https://spark.apache.org/) and it's ecosystem.

Apache Spark is a general purpose processing engine for analytics. It is generally used for large datasets, typically in terabytes or petabytes. It has wide coverage on APIs and can be used for processing batches of data, real-time streams, machine learning, and ad-hoc query. Processing tasks are distributed over a cluster of nodes, and data is cached in-memory, to reduce computation time. We will be using Spark for our previous airline dataset, with size of **1.6 GB** and **120M records**, which should be an easy job for Spark to handle.

## Introductory Knowledge and Concepts

We will look into Spark and pyspark API for Spark.

<h3> Spark </h3>

Spark is a processing engine for large scale datasets. It handles parallel processing operations so that you don't have to build your own.

Sparks architecture consists of 2 main sides.

1. Master Daemon (Driver Process)
2. Worker Daemon (Slave Process)

#### Directed Acyclic Graph (DAG)

DAG is nothing but a graph which holds the track of operations applied on RDD.

DAGScheduler is the scheduling layer of Apache Spark that implements stage-oriented scheduling. It transforms a logical execution plan (i.e. RDD lineage of dependencies built using RDD transformations) to a physical execution plan (using stages).

#### Shared Variables

Generally, while functions passed on, it executes on the specific remote cluster node. Usually, it works on separate copies of all the variables those we use in functions. These specific variables are *precisely copied to each machine*. Also, on the remote machine, no updates to the variables sent back to the driver program. Therefore, it would be inefficient to support general, read-write shared variables across tasks. Although, in spark for two common usage patterns, there are two types of shared variables, such as:

1. Broadcast Variables
2. Accumulators

<sub>Content taken from [techvidvan.com](https://techvidvan.com/tutorials/spark-shared-variable/).</sub>


#### RDD

RDD (Resilient, Distributed, Dataset) is **immutable** distributed collection of objects. RDD is a logical reference of a dataset which is partitioned across many server machines in the cluster. RDDs are Immutable and are self recovered in case of failure. An RDD could come from any datasource, e.g. text files, a database via JDBC, etc.

RDDs have two sets of operations.

1. Transformations 
2. Actions

##### Transformations and Actions

Transformation applies some function on a RDD and creates a new RDD, it does not modify the RDD that you apply the function on.(Remember that RDDs are immutable). Also, the new RDD keeps a pointer to it’s parent RDD.

Transformations are lazy operations on a RDD that create one or many new RDDs, e.g. map,filter, reduceByKey, join, cogroup, randomSplit

**Narrow transformation** — doesn’t require the data to be shuffled across the partitions. for example, Map, filter etc..
**Wide transformation** — requires the data to be shuffled for example, reduceByKey etc..

**An Action** is used to either save result to some location or to display it. You can also print the RDD lineage information by using the command filtered.toDebugString(filtered is the RDD here).

#### Spark DataFrame

In Spark, DataFrames are the distributed collections of data, **organized into rows and columns**. Each column in a DataFrame has a name and an associated type. DataFrames are similar to traditional database tables, which are structured and concise. We can say that DataFrames are relational databases with better optimization techniques.

Spark DataFrames can be created from various sources, such as Hive tables, log tables, external databases, or the existing RDDs. DataFrames allow the processing of huge amounts of data.

### Spark Python API

Create your Spark Environment using Google Colab with the script we had. After creating the environment, you can do the following to get your `sc` object.

After loading Spark, initating an instance of spark can be done as below.

``` py
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .master("local[*]") \
    .appName("My Awesome Spark App!") \
    .getOrCreate()
```

Read from a text file, create an RDD.

```py
sc.textFile('data.csv', use_unicode=True).take(4)
```

Creating a dataframe.

``` py
df = sqlContext.createDataFrame(
  data=[('a', 4), ('b', 2)], 
  schema=['Column A', 'Column B']
)
```

Apply a transformation to the data.

```py
df2 = df[df.column_name != 'some_value']
```

Apply an action to get a result.

```py
df3.filter(df3.size > 1000).count()
```
<sub>Content taken from [Spark Basics : RDDs,Stages,Tasks and DAG](https://medium.com/@goyalsaurabh66/spark-basics-rdds-stages-tasks-and-dag-8da0f52f0454).</sub>

### Tools to Use for Spark

There are four ways of using spark. 

- Using [Google Colab](https://colab.research.google.com/) **(Recommended)**
- Using [Databricks](https://community.cloud.databricks.com/)
- Install it on your own system, either using [dockers](http://docker.com/) or on your host system directly.
- ~~Using Saint Peter's University Data Science Lab [Notebooks](https://dsl.saintpeters.edu:8443/).~~ *

To make this part easy, you don't have to install it on your own computer. However, you will have to use all the other tools. 

Databricks will work on the fly, you just need to create and account. SPU data science lab is similar to Databricks, after you log in, you will be able to create notebooks. For Google Colab, you have to run the following script first, in order to be able to use spark.

Installing Spark on your local system is another option. You can install everything directly on your own computer, else you can utilize docker containers and make a docker compose to configure master and worker nodes. Check out this marvelous article on medium by [@marcovillarreal_40011](https://medium.com/@marcovillarreal_40011) on how to [create a spark standalone cluster with Docker and docker-compose](https://medium.com/@marcovillarreal_40011/creating-a-spark-standalone-cluster-with-docker-and-docker-compose-ba9d743a157f). You can try `docker-compose` to build your own standalone spark instance.

<sub>Not available due to COVID 19 and VPN restrictions.</sub>

### About the Dataset

The data consists of flight arrival and departure details for all commercial flights within the USA, from October 1987 to April 2008.

Each row represents an individual flight record with details of that flight in the row. The information are:

- Time and date of arrival
- Originating and destination of airports
- Amount of time for a plane from taxi to takeoff

You can find more information about this dataset in the website of [Statistical Computing](http://stat-computing.org/dataexpo/2009/).

## Tasks

> Find the # of flights each airline made using Spark.

Try to find the count for the entire dataset.

### Setup

Follow below instructions to set up your assignment repository.

- [ ] Download images from [My Google Drive](https://drive.google.com/open?id=1145wIkSlzA61CdHS4hZZFgF6ZzIbaVJM). (Only SPU emails are allowed to download.)
- [ ] Create a folder named as `data` in this directory. Put the data files in this folder.
- [ ] Load the entire dataset into a DataFrame.

### MapReduce 

Use map-reduce algorithm to find out the results of the following questions.

- [ ] Find the counts of all airlines using MapReduce algorithm. Use Spark and PySpark API to complete this task.
- [ ] Find the mean departure delay per origination airport.

## What are All These Files?

Following table is will give it a meaning for each file.

File                | Description 
-------             | ----------- 
README.md           | A descriptive file to give an introduction of current project/ assignment. Includes a todo list that **you have to edit**.
LICENCE             | The licence of the file that every project should have.
.gitignore          | The file to control which files should be ignored by Git.
.gitkeep            | An empty file to keep folders under git.
requirements.txt    | A list of python packages you may need for the assignment.
*.ipynb             | Sample notebook as a reference for how your notebooks should be organized.

## Your To-Do List for This Assignment

- [ ] I **have completed** all the tasks in [tasks](#tasks) section.
- [ ] I edit this README file and checkmarked things I've completed in the tasks section.
- [ ] My notebook(s) are well organized with headings, comments, that makes it visually appealing.
- [ ] My notebook(s) have the results of my execution.
- [ ] My notebook(s) are reproducible.
- [ ] I download the final version of my repository, and uploaded to the [blackboard](https://saintpeters.blackboard.com/)!
