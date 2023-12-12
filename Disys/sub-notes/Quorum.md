1. **Majority Quorums**:
    - **Common Strategy**: `r > n/2`, `w > n/2`, hence `r + w > n`.
    - **Result**: Guarantees overlap and that each read will reflect the most recent write.
2. **Read-heavy Workloads**:
    
    - **Common Strategy**: Set `w` to a large number (close to `n`) and `r` to a small number (just over `n/2`).
    - **Result**: Writes are more expensive (need more acknowledgments), but reads are faster and cheaper, suitable for read-heavy systems.
3. **Write-heavy Workloads**:
    
    - **Common Strategy**: Set `r` to a large number (close to `n`) and `w` to a small number (just over `n/2`).
    - **Result**: Writes are cheaper, but reads are more expensive as they need more acknowledgments, suitable for write-heavy systems.
4. **Strict Consistency**:
    
    - **Common Strategy**: Set both `r` and `w` to `n`.
    - **Result**: This strategy maximizes consistency but sacrifices availability, as operations cannot proceed if any single replica is unavailable.
5. **High Availability**:
    
    - **Common Strategy**: Set `r` and `w` such that `r + w <= n`.
    - **Result**: Prioritizes availability over strict consistency. This allows the system to operate even when multiple nodes fail but can lead to stale reads.
6. **Optimistic Replication**:
    
    - **Common Strategy**: Set `w` to 1 and `r` to `n`.
    - **Result**: Writes are confirmed after just one replica acknowledges, aiming for high availability and low latency. However, reading requires checking all replicas to find the latest write, which can be slow.

Each of these strategies makes different trade-offs and the choice of which to use depends on the specific requirements of the system, such as whether consistency, availability, or latency is the highest priority. The CAP theorem is often referenced when discussing these trade-offs, as it states that in the presence of a network partition, a distributed system can only guarantee either consistency or availability, but not both simultaneously.

*What is the CAP theorem?*

The CAP theorem, also known as Brewer's theorem, is a fundamental principle in the field of distributed computing and database systems. Formulated by computer scientist Eric Brewer in 2000, the theorem states that a distributed data store cannot simultaneously guarantee all three of the following properties:

1. **Consistency**: Every read receives the most recent write or an error. In other words, all nodes see the same data at the same time. Consistency here is defined in the sense of linearizability, which means that the system behaves as if there is only a single copy of the data, and all operations are atomic.
    
2. **Availability**: Every request (whether read or write) receives a response — without the guarantee that it contains the most recent write. Availability in this context means that every request to a non-failing node in the system must result in a response, not that every node must be available at all times.
    
3. **Partition Tolerance**: The system continues to operate despite arbitrary message loss or failure of part of the system (i.e., network partitions). A network partition is a break in the network that prevents communication between two groups of nodes in the distributed system.

According to the CAP theorem, a distributed system can only satisfy two of these three properties at any given time, but not all three simultaneously:

- A system that chooses consistency and partition tolerance might sacrifice availability. During a partition, some nodes might not be able to respond to requests if they cannot guarantee consistency.
- A system that chooses availability and partition tolerance might sacrifice consistency. During a partition, nodes will still respond, but they might not have the most recent data.
- A system that chooses availability and consistency might sacrifice partition tolerance. In practice, however, such systems are less common because partition tolerance is often considered a mandatory requirement for distributed systems.

The CAP theorem highlights the trade-offs and limitations faced in the design and operation of distributed systems and has significant implications for the design of databases, especially those that need to operate over a wide network such as the internet. It's important to note that the theorem is a theoretical one, and in real-world scenarios, many systems aim to balance these three aspects rather than strictly adhering to only two at any given time.