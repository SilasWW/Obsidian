
# Big data
## Q1.1
Select the correct statements below: 
a)Big data analytics applications perform many random disk accesses since they process data in random order. 
(b) Spark applies transformations to RDDs as soon as possible and stores the in- termediate results in memory. 
(c) Big data originates from a big variety of sources and can be structured, semi- structured, or unstructured. 
(d) Spark can be used to process structured data.

## A1.1
(a) **Big data analytics applications perform many random disk accesses since they process data in random order.**

- This statement is generally **incorrect**. Big data analytics applications, especially those based on modern processing frameworks like Hadoop or Spark, are designed to minimize random disk access due to its inefficiency. They typically process data in a more sequential manner and use techniques like data partitioning and distributed processing to enhance performance.

(b) **Spark applies transformations to RDDs as soon as possible and stores the intermediate results in memory.**

- This statement is **incorrect**. Spark follows a lazy evaluation approach, meaning that it does not apply transformations to Resilient Distributed Datasets (RDDs) as soon as they are defined. Instead, transformations are only executed when an action (like collecting the results or saving them to a file) is triggered. While Spark does store intermediate results in memory, this is not done immediately upon the application of transformations but rather when the data is actively used in actions.

(c) **Big data originates from a big variety of sources and can be structured, semi-structured, or unstructured.**

- This statement is **correct**. Big data indeed comes from a wide variety of sources, including social media, sensor data, business transactions, and more. It can be structured (like data in relational databases), semi-structured (like XML or JSON files), or unstructured (like text, images, and videos).

(d) **Spark can be used to process structured data.**

- This statement is **correct**. Spark is well-suited for processing structured data. It has components like Spark SQL which allow it to effectively handle structured data queries and operations, enabling SQL-like querying capabilities on structured data.


# Hardware and DBMS design
## Q2.1.1
Select the correct statements below: 
(a) If only old values are logged during updates, durability can still be implemented. 
(b) Key-value stores excel at joining large relations. 
(c) SSDs are faster than HDDs, partly because they have no moving parts. 
(d) Support for ACID transaction properties is important for workloads with many small update transactions.

## A2.1.1
a) **False** - Logging only old values during updates may not be sufficient to guarantee durability. Durability in database systems often requires that both old and new values are logged, or that the new values are written in such a way that the system can recover to a consistent state after a crash. Logging only old values might not provide enough information to reconstruct the latest state of the database after a failure.

b) **False** - Key-value stores generally do not excel at joining large relations. They are designed for high performance on large volumes of data, particularly for operations involving direct access to values via keys. However, relational operations like joins, which are common in relational databases, are not a strength of key-value stores. These stores typically lack the complex querying and transaction capabilities necessary for efficiently joining large relations.

c) **True** - SSDs (Solid State Drives) are faster than HDDs (Hard Disk Drives), and one of the reasons for this is indeed because they have no moving parts. SSDs use flash memory for data storage, which allows for faster data access and retrieval compared to the mechanical parts and spinning disks used in HDDs.

d) **True** - Support for ACID (Atomicity, Consistency, Isolation, Durability) transaction properties is important for workloads with many small update transactions. ACID properties ensure that even in the event of system failures, power failures, or other unexpected issues, the transactions are processed reliably. In scenarios with many small updates, maintaining the integrity and consistency of the database is crucial, and ACID properties provide this guarantee.

## Q2.1.2
Discuss pros and cons of using a RAM-based relational database system, compared to an SSD-based system. Be sure to mention both pros and cons. For pros, it is not enough to state that it will be faster, as that is a given, but rather how it could be simpler.

## A2.1.2
Using a RAM-based relational database system compared to an SSD-based system comes with its own set of advantages and disadvantages. Here's a detailed discussion:

### RAM-Based Relational Database System

#### Pros:

1. **Simplicity in Data Access and Management**: RAM-based databases inherently simplify data access due to their in-memory nature. There's no need for complex disk I/O operations, making the data access patterns straightforward and reducing the overhead associated with data retrieval and storage.
    
2. **Reduced Latency for Data Operations**: Access times in RAM are significantly lower than on SSDs, leading to faster read and write operations. This is particularly beneficial for applications requiring real-time data processing and high-speed transactions.
    
3. **Efficient Use of Processor Caches**: In-memory databases can make better use of processor caches, as data does not have to be frequently moved from disk to RAM. This can lead to performance improvements in data processing and querying.
    
4. **Simplified Database Design**: The high speed of RAM can allow for simpler database designs, as the need for complex indexing and data optimization strategies (often used to mitigate disk I/O latency) is reduced.
    

#### Cons:

1. **Volatility and Data Durability Issues**: RAM is volatile, meaning data is lost when the power goes off. Ensuring data durability requires additional mechanisms, such as regular snapshots or logging to a persistent storage medium, which can add complexity and overhead.
    
2. **Cost and Scalability Concerns**: RAM is more expensive per gigabyte than SSDs, making large databases more costly to scale. The physical limitations of how much RAM can be installed on a server also pose scalability challenges.
    
3. **Increased Power Consumption**: RAM consumes more power than SSDs, especially at scale, which can increase operational costs and have environmental impacts.
    
4. **Heat Generation**: High-density RAM usage in servers generates more heat, requiring more effective cooling solutions.
    

### SSD-Based Relational Database System

#### Pros:

1. **Non-Volatility and Better Data Durability**: SSDs are non-volatile storage mediums, ensuring data persistence even when the power is off, thus providing better data durability out-of-the-box compared to RAM-based systems.
    
2. **Cost-Effectiveness and Higher Capacity**: SSDs offer a more cost-effective solution for larger databases. They provide higher storage capacity at a lower cost compared to RAM, making them suitable for larger datasets.
    
3. **Reduced Power Consumption**: SSDs generally consume less power than an equivalent RAM setup, especially beneficial for large-scale deployments.
    
4. **Better Heat Management**: SSDs generate less heat compared to large RAM configurations, easing the demands on cooling systems in data centers.
    

#### Cons:

1. **Slower Access Times Compared to RAM**: While SSDs are faster than traditional HDDs, they are still slower than RAM, leading to higher latency in data retrieval and updates.
    
2. **Wear and Tear Over Time**: SSDs have limited write cycles; frequent write operations can lead to quicker wear and tear, potentially reducing the lifespan of the drive.
    
3. **Complex Data Retrieval and Caching Mechanisms**: To mitigate the slower access speeds, SSD-based systems often require more complex caching and data retrieval strategies, which can add to the system's complexity.
    
4. **Fragmentation Over Time**: Over time, SSDs can suffer from fragmentation, which can degrade performance, although this is less of an issue compared to traditional HDDs.
    

In summary, RAM-based databases offer superior speed and simplicity in data management but come with challenges in terms of cost, scalability, and data durability. SSD-based systems, while slower, provide a more balanced approach in terms of cost, capacity, and durability, suitable for larger, persistent datasets. The choice between the two depends largely on the specific requirements and constraints of the application and infrastructure.