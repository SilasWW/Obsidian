#Disys
#Replication

## Replication
[5.1 Replication (Martin Kleppmann)](https://www.youtube.com/watch?v=mBUCF1WGI_I&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB&index=14)

**Problem: Retrying state updated**

![[Pasted image 20231129135946.png]]


**Solution: Exactly once semantic**
Retry + [[idempotence]] or deduplication

**More problems**
![[Pasted image 20231129141711.png]]

![[Pasted image 20231129141759.png]]

**Solution: Timestamps and Tombstones**

Adding Timestamps and [[Tombstones]] allows the replicas to reconcile periodically. 