#Disys 
**Tombstones in Distributed Systems**:

- A tombstone is a marker placed on a data entry to indicate its logical deletion.
- It contains a timestamp for conflict resolution among system replicas.
- If a replica's tombstone timestamp is newer than that of another replica without a deletion, it confirms the deletion's correctness, prompting updates in other replicas.
- Conversely, if a replica without a deletion has a newer timestamp, it can lead to the reversal of the deletion, changing the tombstone to indicate the item is not deleted.
- This mechanism ensures consistent state across all replicas in the distributed system.