#Disys

Replication is having the same data on multiple machines. This is in itself an easy task, if the data on the machines never change. However, with regularly changing data, keeping the data synchronized across the replicas(nodes with copies of the data) becomes a significant challenge. 

[5.1 Replication (Martin Kleppmann)](https://www.youtube.com/watch?v=mBUCF1WGI_I&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&index=14)

**Problem: Retrying state updates**
Resending requests, particularly post-requests can result in actions being performed too many times.
![[Pasted image 20231129135946.png]]


**Solution: Exactly once semantic**
Retry + [[Idempotence]] or deduplication

**More problems**
![[Pasted image 20231129141711.png]]


![[Pasted image 20231129141759.png]]
Adding and removing can end out of the intended order, in case of faults. 

**Solution: Timestamps and Tombstones**

Adding Timestamps and [[Tombstones]] allows the replicas to reconcile periodically.

**Problem: Read-after-write consistency**
[5.2 Quorums (Martin Kleppmann)](https://www.youtube.com/watch?v=uNxl3BFcKSA&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&index=15) 

![[Pasted image 20231129155058.png]]

If you write to 2 replicas, but one of them, A, dont receive the request, and then immediately after want to read from the replicas, but now only A responds, you will not receive what you have just written. 
If you restrict the system such that, you can only read/write if all replicas are functional, the system is not fault tolerant. 

**Solution: Quorums**
![[Pasted image 20231129155554.png]]

If we introduce more replicas, we can introduce the concept of, a minimum number of nodes that need to be functional, for example, for reading the client must receive a minimum number of correct identical responses, for the response to be valid. If two responses are not identical, the newest timestamp will decide the correct one.

A quorum is the minimum count of nodes required to validate an operation in a distributed system. For a system with `n` replicas:

- **Write Quorum (`w`)**: This is the number of replicas that must acknowledge a write operation for it to be considered valid. It ensures that the data is reliably stored across multiple nodes.
    
- **Read Quorum (`r`)**: This is the minimum number of replicas from which a client must receive responses for a read operation to be considered valid. The system uses the newest timestamp among received responses to determine the most up-to-date data if there is a discrepancy.
    

Each operation (read or write) is tagged with a unique identifier, such as a timestamp, which allows the system to correlate responses and acknowledgments to the correct operation.

The quorum condition, *`r + w > n`*, guarantees overlap between read and write operations, ensuring that any read operation following a write will intersect with at least one replica that has the latest write. This overlap is crucial for maintaining consistent reads and ensuring that the most recent write is always available to be read.

*[[Quorum|Other quorom strategies]]*



## With multiple replicas, a question inevitably arises: how do we ensure that all the data ends up on all the replicas?


