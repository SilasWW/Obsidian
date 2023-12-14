# Q1.1
Select the correct statements below: 
a)Big data analytics applications perform many random disk accesses since they process data in random order. 
(b) Spark applies transformations to RDDs as soon as possible and stores the in- termediate results in memory. 
(c) Big data originates from a big variety of sources and can be structured, semi- structured, or unstructured. 
(d) Spark can be used to process structured data.

# A1.1
(a) **Big data analytics applications perform many random disk accesses since they process data in random order.**

- This statement is generally **incorrect**. Big data analytics applications, especially those based on modern processing frameworks like Hadoop or Spark, are designed to minimize random disk access due to its inefficiency. They typically process data in a more sequential manner and use techniques like data partitioning and distributed processing to enhance performance.

(b) **Spark applies transformations to RDDs as soon as possible and stores the intermediate results in memory.**

- This statement is **incorrect**. Spark follows a lazy evaluation approach, meaning that it does not apply transformations to Resilient Distributed Datasets (RDDs) as soon as they are defined. Instead, transformations are only executed when an action (like collecting the results or saving them to a file) is triggered. While Spark does store intermediate results in memory, this is not done immediately upon the application of transformations but rather when the data is actively used in actions.

(c) **Big data originates from a big variety of sources and can be structured, semi-structured, or unstructured.**

- This statement is **correct**. Big data indeed comes from a wide variety of sources, including social media, sensor data, business transactions, and more. It can be structured (like data in relational databases), semi-structured (like XML or JSON files), or unstructured (like text, images, and videos).

(d) **Spark can be used to process structured data.**

- This statement is **correct**. Spark is well-suited for processing structured data. It has components like Spark SQL which allow it to effectively handle structured data queries and operations, enabling SQL-like querying capabilities on structured data.

# Q1.2
Assume that you need to process a massively large dataset with a limited budget. Which framework would you choose as a more cost-effective solution, Hadoop or Spark? Explain your choice.

# A1.2
In conclusion, if your primary concern is speed and you have a dataset that can fit into memory, and your budget can accommodate the higher hardware costs, Spark might be the more cost-effective choice. However, if your project involves large-scale batch processing where speed is less critical, and minimizing hardware costs is a priority, Hadoop could be more suitable. The decision should be based on a detailed analysis of your specific use case, data characteristics, performance requirements, and budget constraints.

# Q2.1
a) Select the correct statements below:

1. (a)  A well-designed relational database can never have incorrect data.
    
2. (b)  Social value can be a significant reason for working with big data.
    
3. (c)  Clustering data is generally achieved with one scan of the data collection.
    
4. (d)  Support for ACID transaction properties is generally useless for big data analysis applications.

# A 2.1
(a) **A well-designed relational database can never have incorrect data.**

- This statement is **incorrect**. Even with a well-designed relational database, the possibility of incorrect data still exists. Data accuracy depends not only on the database design but also on the quality of the data entry processes, data integrity constraints, and ongoing data management practices.

(b) **Social value can be a significant reason for working with big data.**

- This statement is **correct**. Big data can be used for various purposes that provide social value, such as in healthcare for disease tracking and prevention, in urban planning for smart city development, or in environmental monitoring for climate change analysis.

(c) **Clustering data is generally achieved with one scan of the data collection.**

- This statement is generally **incorrect**. Most clustering algorithms, especially in big data contexts, require multiple scans of the data collection. Algorithms like K-means, for instance, iterate several times to refine the clusters. The process is more complex than a single scan, particularly with large datasets.

(d) **Support for ACID transaction properties is generally useless for big data analysis applications.**

- This statement is **incorrect**. While it's true that not all big data applications require strict ACID properties (particularly in cases where eventual consistency is acceptable), there are scenarios in big data where ACID properties are crucial. For instance, in financial systems or any other applications where data integrity and consistency are critical, ACID properties are very important.

Therefore, the correct statements are (b) "Social value can be a significant reason for working with big data," while the others (a), (c), and (d) are incorrect based on the general understanding and common practices in the field of big data and databases.

# Q3.1
Select the correct statements below: 
(a) All big data applications are evil in nature. 
(b) Spark is designed for supporting user-facing and interactive applications. 
(c) Many big data applications require so much computation that a distributed processing framework is necessary. 
(d) A machine learning model that is based on real data can never have any bias, because it accurately models real life.

# A3.1
Let's evaluate each of these statements:

(a) **All big data applications are evil in nature.**

- This statement is **incorrect**. The nature of big data applications is not inherently evil; they can be used for a wide range of purposes, both beneficial and harmful, depending on the context and the intent of their use. Big data applications have been used for positive impacts in areas like healthcare, environmental protection, and public safety, as well as for more controversial purposes.

(b) **Spark is designed for supporting user-facing and interactive applications.**

- This statement is **correct** to an extent. Spark is designed to handle large-scale data processing efficiently and can support user-facing and interactive applications. It is particularly effective for jobs that require fast iterative processing, like interactive data exploration and machine learning applications.

(c) **Many big data applications require so much computation that a distributed processing framework is necessary.**

- This statement is **correct**. Big data applications often involve processing such vast amounts of data that they require distributed processing frameworks, like Hadoop or Spark, to process the data efficiently across multiple computers.

(d) **A machine learning model that is based on real data can never have any bias, because it accurately models real life.**

- This statement is **incorrect**. Machine learning models, even when based on real data, can still be biased. Bias in machine learning models can arise from various sources, including biased data collection, unrepresentative training datasets, and flawed assumptions in the algorithm design. Just because a model is based on real data does not guarantee that it is free of bias.

Therefore, the correct statements are (b) "Spark is designed for supporting user-facing and interactive applications" and (c) "Many big data applications require so much computation that a distributed processing framework is necessary." Statements (a) and (d) are incorrect.

# Q3.2
What is the the most important disk access pattern of typical big data applications? Support your answers with arguments.

# A3.2
The most important disk access pattern for typical big data applications is sequential access. This pattern is central to the design and efficiency of many big data processing frameworks and systems. Here's why:

1. **Efficient Handling of Large Volumes of Data**:
    
    - Big data applications often involve processing extremely large datasets. Sequential access allows these systems to read and write large blocks of data efficiently. Since the data is accessed in a contiguous block, it reduces the time spent on seeking different parts of the disk, which is a major bottleneck in random access.
2. **Compatibility with Distributed File Systems**:
    
    - Big data applications frequently utilize distributed file systems like the Hadoop Distributed File System (HDFS). These systems are designed around the principle of sequential access, where data is stored and processed in large blocks (e.g., 64 MB or 128 MB blocks in HDFS). This approach is optimal for the high-throughput data access required by big data applications.
3. **MapReduce and Similar Frameworks**:
    
    - The MapReduce programming model, commonly used in big data processing, is tailored for sequential data access. In this model, large datasets are divided into chunks, and the 'map' function processes these chunks in parallel. This processing is inherently sequential within each chunk, making sequential access the most efficient pattern.
4. **Minimizing Disk Seek Time**:
    
    - Disk seek time (the time taken for the disk drive to find the correct part of the disk to read or write data) is significantly reduced with sequential access. In big data applications, where the cost of reading from and writing to disk can be a major performance bottleneck, minimizing seek time is crucial for maintaining high throughput.
5. **Streaming Data and Real-time Processing**:
    
    - Many big data applications involve streaming data, such as logs, social media feeds, or sensor data. These data streams are naturally suited to sequential access, as data is typically processed in the order it arrives.
6. **Simplifying Data Processing Pipelines**:
    
    - Sequential access simplifies the design of data processing pipelines. When data is read and written in order, it's easier to partition the work across multiple nodes in a distributed system and to maintain data locality, which is key for performance in distributed computing.

In conclusion, sequential access is the most important disk access pattern in big data applications due to its efficiency in handling large datasets, compatibility with distributed file systems, alignment with the MapReduce model, reduction in disk seek time, suitability for streaming data, and simplification of data processing pipelines. This pattern enables big data systems to process and analyze large volumes of data in a scalable and efficient manner.

