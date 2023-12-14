# Q1.1
a) Briefly discuss:
	(a) what consistency means in the context of ACID transactions
	(b) how relational systems support such consistency. b) Select the true statements:

# A1.1
a) **Consistency in the Context of ACID Transactions**

- Consistency in the ACID context refers to the guarantee that a transaction brings the database from one valid state to another. This means that all data written to the database must be valid according to all defined rules, including constraints, cascades, and triggers. In essence, a transaction must not violate any integrity constraints during its execution. If a transaction results in a breach of these constraints, the entire transaction should be rolled back and the database should remain in its original consistent state.

b) **Support for Consistency in Relational Systems**

- Relational database systems support consistency through various mechanisms:
    - **Constraint Enforcement**: This includes primary keys, foreign keys, unique constraints, and check constraints to ensure data integrity.
    - **Trigger Execution**: Triggers are automated rules defined in the database that execute in response to certain database events, helping to maintain consistency.
    - **Transactional Controls**: Commands like COMMIT and ROLLBACK ensure that changes made by a transaction are permanent only if they maintain consistency, or are undone if they don’t.
    - **SQL Standards Compliance**: SQL, as a language, has built-in features to enforce data integrity and consistency.

# Q1.2
Select the true statements: 
(a) Locking can be used to implement isolation. 
(b) A buffer manager with a NO STEAL policy complicates the implementation of atomicity. 
(c) Isolation and durability are mutually exclusive. 
(d) Transactions are a general concept that could potentially be applied to, for example, file systems.

# A1.2
a) **Locking can be used to implement isolation.**

- **True**: Locking mechanisms are a common way to achieve isolation in database systems. By locking data that a transaction is reading or writing, the database can prevent other transactions from accessing the same data simultaneously, thereby isolating the transactions from each other.

b) **A buffer manager with a NO STEAL policy complicates the implementation of atomicity.**

- **False**: A NO STEAL policy, where the buffer manager does not write dirty pages of an uncommitted transaction to disk, actually facilitates the implementation of atomicity. It ensures that changes made by a transaction are not made permanent (i.e., not "stolen" and written to disk) until the transaction commits. This makes it easier to roll back transactions and maintain atomicity.

c) **Isolation and durability are mutually exclusive.**

- **False**: Isolation and durability are not mutually exclusive; they are distinct properties of ACID transactions. Isolation ensures that concurrently executed transactions do not affect each other, while durability guarantees that once a transaction has been committed, its effects are permanent and survive system failures. These two properties can, and do, coexist in ACID-compliant systems.

d) **Transactions are a general concept that could potentially be applied to, for example, file systems.**

- **True**: The concept of transactions is not limited to database systems. It can be applied to any system that requires ensuring integrity and consistency in the face of concurrent operations or failures. This includes file systems, where transactions can help ensure that file operations are completed fully or not at all, maintaining the consistency of the file system.


