---
layout: post
comments: true
title: Hadoop Review
---

Hadoop is a large-scale distributed batch-processing infrastructure.

# Key Component

## HDFS(Hadoop Distributed File System)
---Distributed data storage with high reliability

## MapReduce
* A parallel, distributed computational paradigm

## MapReduce
* Map tasks(mappers)
	* performs data transformation
* Reduce tasks(reducers)
	* combines results of map tasks
* (Internally) shuffle tasks
	* sends output of mappers to right reducers

<h1 style="text-align: center;color: pink;">Hadoop cluster</h1>

![hadoopcluster](http://i.imgur.com/QHVTdEE.png)

* Namenode
	* Runs Name Node, Secondary Name Node, Job tracker daemons
	* In practice, they may be running on difference machines
	* Stores locations of data and their replica in HDFS

* Datanode
	* Each runs a task tracker and data node daemon
	* Client can directly talk to data node, once obtains location of data from name node

* Job tracker
	* Takes requests from clients
	* Ask name node for location of data
	* Assign tasks to task trackers

* Task tracker
	* Accept (map, reduce, shuffle) tasks from job trackers
	* Send signal to job trackers that it is alive

<h1 style="text-align: center;color: rgb(181, 208, 252);">MapReduce data flow</h1>
![MapReduceDataFlow](http://i.imgur.com/oVBhdeN.png)

<h1 style="text-align: center; color: rgb(181, 208, 252);">Combiner</h1>
![Combiner](http://i.imgur.com/NsnOwFo.png)

* run on the node running the Mapper
* combine mapper results
	- before they are sent to reducers
* may be used in WordCount
	- (cat, 1), (cat, 1), (cat, 1) => (cat, 3)