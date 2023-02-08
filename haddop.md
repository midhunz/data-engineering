## Apache Hadoop

Apache Hadoop is an open-source software framework for storing, processing, and analyzing large and complex datasets. It is designed to scale from a single server to thousands of machines, each offering local computation and storage.

Apache Hadoop works by dividing large datasets into smaller chunks and distributing them across a cluster of commodity servers. This allows the data to be processed in parallel, reducing the amount of time it takes to complete a job.

The key components of Hadoop are the Hadoop Distributed File System (HDFS) and the MapReduce programming model. HDFS stores the data in a distributed fashion across multiple nodes in the Hadoop cluster, providing a high degree of fault tolerance. MapReduce processes the data by dividing the work into smaller chunks, called map tasks, that can be processed in parallel. The results of the map tasks are then combined, or reduced, into a smaller set of results.

When a Hadoop job is submitted, it is divided into map tasks and reduce tasks that are executed in parallel across the nodes in the Hadoop cluster. Each node processes a portion of the data and produces intermediate results that are passed on to the reduce tasks. The reduce tasks then process the intermediate results and produce the final output.

In addition to MapReduce, Hadoop provides a number of other tools and frameworks, including Pig, Hive, and Spark, that allow developers to process and analyze data stored in HDFS.

One of the key benefits of Hadoop is its ability to scale to handle extremely large datasets. By adding more nodes to the Hadoop cluster, the amount of data that can be processed can be increased linearly, allowing organizations to store and process vast amounts of data.

Overall, Hadoop provides a highly scalable and flexible platform for processing and analyzing large and complex datasets, making it a popular choice for organizations in a variety of industries.

### Apache Hadoop in laymans term

Hadoop is like a big room in a library where lots of books are stored. But instead of books, it stores lots of information like movies, pictures, or messages that people send to each other.

Think of all the information in the world as a big pile of papers. When you want to find something specific, like information about a specific animal or a specific person, it takes a long time to go through all the papers.

Hadoop helps us find what we are looking for faster. It takes all the papers and breaks them into smaller piles, like piles of papers about animals, or piles of papers about different countries. Then, it gives different piles to different people to look through at the same time. This way, everyone can work together to find what we are looking for faster.

So Hadoop is like a big helper for finding information quickly!

### Apache Hadoop architecture

The Apache Hadoop architecture consists of several key components that work together to process and store big data. The main components are:

-   Hadoop Distributed File System (HDFS): This is the storage layer of Hadoop and is responsible for storing and managing the data in a distributed fashion. Data is stored in HDFS as blocks, and each block is replicated across multiple nodes in the cluster for high availability.

-   YARN (Yet Another Resource Negotiator): This is the resource management layer of Hadoop that schedules and manages the execution of MapReduce jobs.

-   MapReduce: This is the processing layer of Hadoop and is responsible for processing the data stored in HDFS. MapReduce processes the data by dividing the work into smaller chunks, called map tasks, that can be processed in parallel. The results of the map tasks are then combined, or reduced, into a smaller set of results.

-   Hadoop Common: This is a set of common utilities and libraries that are used by the other components of Hadoop.

-   Hadoop Ecosystem: This includes a number of additional tools and frameworks, such as Pig, Hive, and Spark, that allow developers to process and analyze data stored in HDFS.

In a typical Hadoop deployment, the data is stored in HDFS and processed using MapReduce or one of the other tools in the Hadoop ecosystem. YARN manages the resources required for processing, ensuring that the cluster is used efficiently and that jobs are executed in a timely manner.

The Hadoop architecture is designed to be highly scalable, allowing organizations to add more nodes to the Hadoop cluster as their data grows. This allows Hadoop to process and store extremely large amounts of data, making it a popular choice for organizations in a variety of industries.


### HDFS 

The Hadoop Distributed File System (HDFS) is the primary storage system for Apache Hadoop. It is designed to store large amounts of data in a distributed manner across a cluster of commodity computers. The data is stored in a redundant fashion, with multiple copies of each file being stored on different nodes in the cluster, to ensure high availability and reliability.

***The main features of HDFS include:***

Distributed Storage: HDFS splits large files into smaller blocks and stores each block on a separate node in the cluster, providing both scalability and fault tolerance.

Scalability: HDFS can store petabytes of data and is designed to handle a high rate of data growth. It can scale horizontally by adding more nodes to the cluster.

Replication: HDFS replicates each block of data across multiple nodes in the cluster, providing redundancy and fault tolerance. If a node fails, the data can be recovered from another copy.

High Availability: HDFS is designed to be highly available, even in the case of node failures. It uses the replication of data blocks to ensure that the data is always available, even if a node fails.

Simple Coherency Model: HDFS provides a simple coherency model that allows clients to read a consistent view of the data, even while it is being written.

HDFS is an integral part of the Hadoop ecosystem and provides the foundation for storing and processing large amounts of data. By storing data in a distributed manner across a cluster, HDFS enables Hadoop to process large amounts of data quickly and efficiently.

**HDFS internal**

The internal details of the Hadoop Distributed File System (HDFS) include:

1.  Blocks: HDFS stores data in blocks, with each block being a fixed size (usually 128 MB). This allows HDFS to store very large files, while still being able to process the data in a distributed manner. Each block is stored on a different node in the cluster, providing both scalability and fault tolerance.

2.  NameNode and DataNode: The HDFS cluster consists of a single NameNode and multiple DataNodes. The NameNode is the master node that manages the file system metadata, such as the file and directory structure, and the location of each block in the cluster. The DataNodes are responsible for storing the data blocks and serving the data to clients.

3.  Replication: HDFS replicates each block of data across multiple DataNodes, providing redundancy and fault tolerance. The default replication factor is 3, meaning that each block of data is stored on three different nodes in the cluster. If a node fails, the data can be recovered from another copy.

4.  Read and Write Operations: When a client wants to read data from HDFS, it sends a request to the NameNode, which returns the location of the blocks for the desired data. The client then retrieves the data directly from the DataNodes. When a client wants to write data to HDFS, it sends the data to the NameNode, which divides the data into blocks, assigns a location for each block, and then sends the blocks to the appropriate DataNodes for storage.

5.  Checkpointing: The NameNode periodically performs a checkpoint, during which it writes its metadata to disk. This allows the NameNode to recover quickly in the event of a failure, as it can read the metadata from disk and rebuild its in-memory state.

HDFS is designed to be a highly scalable and reliable storage system for big data. Its architecture, with the NameNode and DataNode, allows HDFS to store large amounts of data in a distributed manner, while providing high availability and fault tolerance. By providing a simple coherency model and efficient read and write operations, HDFS makes it easy for Hadoop to process large amounts of data quickly and efficiently.

### Hadoop Data node vs Name node

The Hadoop Distributed File System (HDFS) consists of two main components: the NameNode and the DataNode.

The NameNode is the master node in HDFS and is responsible for managing the file system namespace, including maintaining metadata about the files and directories stored in the file system. The NameNode also coordinates access to the data stored in the file system and keeps track of the location of data blocks on the DataNodes.

The DataNode is a worker node in HDFS and is responsible for storing the actual data blocks of a file. The DataNode stores the blocks of data in its local disk and serves the data to clients who request it. The DataNode also communicates with the NameNode to report on the state of its stored data blocks and to receive instructions for reading and writing data.

In summary, the NameNode is responsible for managing the metadata of the file system and coordinating access to the data stored in HDFS, while the DataNode is responsible for storing the actual data blocks and serving data to clients.

***More***

    *** NameNode

    NameNode is the master node in the Hadoop Distributed File System (HDFS) and is responsible for managing the metadata of the file system. It stores the metadata in memory and maintains a directory tree of all files and directories in the file system, including information about the location of each file's data blocks, the replication factor of the data, and the status of each block.

    The NameNode also coordinates access to the data stored in the HDFS. When a client wants to read or write data, it communicates with the NameNode to find the location of the data blocks, and then communicates directly with the appropriate DataNodes to read or write the data.

    Additionally, the NameNode is responsible for monitoring the health of the DataNodes and the data stored on them. If a DataNode fails or a data block becomes unavailable, the NameNode is responsible for re-replicating the data to ensure that it is still available and can be accessed by clients.

    

    *** Data Node

    A DataNode is a worker node in the Hadoop Distributed File System (HDFS). It is responsible for storing the actual data blocks of a file and serving the data to clients who request it. The DataNode stores the blocks of data in its local disk, and communicates with the NameNode to report on the state of its stored data blocks and to receive instructions for reading and writing data.

    When a client wants to write data to HDFS, the NameNode determines which DataNode should store the data based on the file's replication factor and the state of the DataNodes. The client then writes the data directly to the selected DataNode, which stores the data blocks on its local disk. When a client wants to read data from HDFS, the NameNode directs the client to the appropriate DataNode, which serves the data directly to the client.

    In addition to serving data, the DataNode is responsible for periodically reporting the state of its stored data blocks to the NameNode. This includes information such as the availability of each block and the number of replicas that exist for each block. The NameNode uses this information to maintain an up-to-date view of the file system and to ensure that data is always available and accessible to clients.






### HDFS commands

Here are some basic commands that you can use to interact with HDFS:

1.  hdfs dfs -ls: List the contents of a directory in HDFS
1.  hdfs dfs -mkdir: Create a new directory in HDFS
1.  hdfs dfs -put: Copy a file from the local file system to HDFS
1.  hdfs dfs -get: Copy a file from HDFS to the local file system
1.  hdfs dfs -cat: Display the contents of a file in HDFS
1.  hdfs dfs -rm: Delete a file or directory in HDFS
1.  hdfs dfs -rmdir: Delete an empty directory in HDFS
1.  hdfs dfs -tail: Display the last part of a file in HDFS
1.  hdfs dfs -du: Show the space used by a file or directory in HDFS
1.  hdfs dfs -cp: Copy files from one location in HDFS to another
1.  hdfs dfs -mv: Move files from one location in HDFS to another
1.  hdfs dfs -chmod: Change the permissions on a file or directory in HDFS
1.  hdfs dfs -chown: Change the owner and/or group of a file or directory in HDFS
1.  hdfs dfs -getmerge: Combine files from HDFS into a single file on the local file system
1.  hdfs dfs -expunge: Permanently delete files that have been marked for deletion in HDFS
1.  hdfs dfs -df: Show the capacity, used space, and remaining space in HDFS
1.  hdfs dfs -count: Count the number of directories, files, and bytes in HDFS
1.  hdfs dfs -help: Show the usage information for a specific HDFS command



