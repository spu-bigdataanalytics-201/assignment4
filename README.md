# Assignment4 - Introduction to Spark

Hi!

In this repository, we will get our hand's dirty with Spark. 

This assignment has the same tasks and goals as previous assignment, but this time, we will utilize [Apache Spark](https://spark.apache.org/) and it's ecosystem.

Apache Spark is a general purpose processing engine for analytics. It is generally used for large datasets, typically in terabytes or petabytes. It has wide coverage on APIs and can be used for processing batches of data, real-time streams, machine learning, and ad-hoc query. Processing tasks are distributed over a cluster of nodes, and data is cached in-memory, to reduce computation time. We will be using Spark for our previous airline dataset, with size of **1.6 GB** and **120M records**, which should be an easy job for Spark to handle.

## Introductory Knowledge and Concepts

### Spark

TBD

### Spark Python API

TBD

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
