A key is something that can uniquely identify an entity in a database. 

**Principles of primary keys:**
* A primary key should never change
* A primary key can never be null
* A primary key strictly must be unique, meaning, two entities can not have the same key
* All entities should have a primary key

There are several different types of keys:

* **Super key:** A super key is basically the baseline key. It is an attribute or set of attributes that can uniquely identify an entity, meaning essentially all keys are super keys.
* **Candidate keys:** A candidate key can also uniquely identify an entity, but it is only candidate key, when it is the least number of attributes possible. Meaning, the lowest amount of attributes that could uniquely identify an entity, would be the candidate key. Other keys with more attributes, would not be candidate keys, but just super keys. 
* **Primary key:** A primary key is the key, that is actually chosen to be the main key for a table, and that foreign keys in other tables will use when referring to entities in the table. A primary key must be a candidate key, and there can only be one primary key. 
* **Alternate keys:** Alternate keys are the candidate keys, that are not chosen to be the primary keys. That means, they could have been primary keys, since they meet the requirements of primary keys.
* **Foreign key:** A foreign key, is an attribute that holds a primary key from another table, in order to form a relationship between the entity in one table, and an entity in another table. 
* **Composite key:** A composite key, is just a key made up of several attributes, rather than just one.
* **Natural key:** A natural key is a key that is organically in the table, because the value was relevant for business logic reasons. This is essentially opposite of having a unique id, that is only there to identify each row, and not because the id itself represents the real world. Email could be a common example of a natural key, assuming an application only allows the user to register 1 email, and requires an email to register. 
* **Surrogate key:** A surrogate key is the opposite of a natural key. It is a key that doesn't have a natural place in the domain, but is added for practical database design reasons. Id's are typical examples of surrogate keys. 

