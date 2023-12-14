## DBMS Architecture
# Q1.1
a) Consider a database server with persistent main memory and no secondary storage. Define the STEAL buffer management policy and discuss its usefulness for such a server.

# A1.1
a) **STEAL Buffer Management Policy in the Context of a Database Server with Persistent Main Memory**

The STEAL buffer management policy is a concept in database systems related to how the buffer manager handles modified pages (or "dirty" pages) in memory. In a STEAL policy, the buffer manager is allowed to write dirty pages from the buffer cache to disk (or persistent storage) before a transaction that modified them has been committed. This is in contrast to the NO STEAL policy, where dirty pages cannot be written to persistent storage until after the transaction commits.

### Usefulness of STEAL Policy for a Database Server with Persistent Main Memory

1. **Reduced Need for STEAL in Persistent Main Memory**:
    
    - In a traditional database system with volatile main memory and secondary storage (like a hard disk or SSD), the STEAL policy is crucial for managing limited memory space. However, in a server with persistent main memory (where data remains intact even after power loss), the pressure to free up buffer cache space by writing dirty pages to secondary storage is reduced. This is because the persistent main memory can hold a larger amount of data safely, even across system restarts.
2. **Implications for Recovery**:
    
    - The key advantage of the STEAL policy is that it supports efficient recovery mechanisms, such as Write-Ahead Logging (WAL). In systems with persistent main memory, the role of WAL and similar recovery mechanisms might change, but they remain important for ensuring atomicity and durability. Even with persistent memory, a database server still needs to ensure that transactions are atomic (all-or-nothing) and durable (changes survive system failures).
3. **Handling Large Transactions**:
    
    - For very large transactions that might exceed the capacity of the main memory, the STEAL policy allows the system to handle these transactions by writing some of the changes to persistent storage before the transaction commits. This can be beneficial even in systems with a large persistent main memory, as it provides a way to manage extremely large or long-running transactions.
4. **Performance Considerations**:
    
    - With persistent main memory, the performance penalty of writing dirty pages to storage is significantly less compared to traditional disk-based storage. This could make the implementation of the STEAL policy more efficient and less impactful on overall system performance.

In summary, while the STEAL policy is primarily designed for environments with limited, volatile main memory and slower secondary storage, its principles can still be useful in a database server with persistent main memory. It can contribute to efficient transaction handling, especially for large transactions, and support robust recovery mechanisms, albeit with different performance characteristics and implementation details compared to traditional disk-based systems.

# Q1.2
Select the true statements:

1. (a)  Writing the log is usually slower than writing the actual updates to relations.
    
2. (b)  SSD storage is volatile.
    
3. (c)  The FORCE policy is difficult to implement in reality, since committing large transactions can cause many disk writes, and the server might crash in the middle of the writing process.
    
4. (d)  Query optimisation are often improved by gathering statistics over relations.


# A1.2
  
Let's evaluate each of these statements for their accuracy:

1. **(a) Writing the log is usually slower than writing the actual updates to relations.**
    
    - **False**: Typically, writing the log is faster than writing the actual updates to relations. This is because log records are written sequentially, which is more efficient on most storage mediums, including HDDs and SSDs. In contrast, updates to relations may require random access writes, which are generally slower.
2. **(b) SSD storage is volatile.**
    
    - **False**: SSD (Solid State Drive) storage is non-volatile. This means that it retains data even when it is not powered, unlike volatile memory such as RAM.
3. **(c) The FORCE policy is difficult to implement in reality, since committing large transactions can cause many disk writes, and the server might crash in the middle of the writing process.**
    
    - **True**: The FORCE policy, which involves writing all changes made by a transaction to the disk before the transaction commits, can be challenging in practice. This is especially true for large transactions, as they can lead to a significant number of disk writes. If the server crashes during this process, it can result in a partially committed state, making recovery complex.
4. **(d) Query optimization is often improved by gathering statistics over relations.**
    
    - **True**: Gathering statistics over relations is a common technique used in query optimization. Statistics like the number of tuples in a relation, the distribution of key values, and the size of data pages help the database's query optimizer to make more informed decisions about the best way to execute a query, such as choosing the most efficient join order or the best index to use.

Therefore, statements (c) "The FORCE policy is difficult to implement in reality, since committing large transactions can cause many disk writes, and the server might crash in the middle of the writing process" and (d) "Query optimization is often improved by gathering statistics over relations" are true, while statements (a) and (b) are false.