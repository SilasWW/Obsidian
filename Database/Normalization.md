
Normalization is a database design process that reduces redundancy and improves data integrity.

1. Normal form (1NF):
	* **Only atomic values in each cell**, meaning no double values, and no values that could be further broken down into smaller values. Eg. two emails in one cell, or a full birthdate with both date, month and year, is not allowed.
	* **Unique column names** - in one table, there cant be 2 columns with the same name
	* **Primary keys** - each entity should have a primary key
	* **Order invariance** - the order of the rows shouldn't matter

2. 2NF:
	* It must be in 1NF
	* **No partial dependencies** - meaning, all attributes in the table, should be non-null. If there are partial dependencies, they should be eliminated by putting them in a separate table, that references to entities in the first table, via foreign keys, as a one-to-one or one-to-many relationship. 
	* 2NF is basically about that, attributes that are specific to the relationship between two entities, rather than specific to one of the two entities themselves, then these attributes should go in the junction table, and not in either of the entity-tables
	* It could be said that, the goal of 2NF, is to align the dependencies of the attributes, with the dependencies of the table itself. 

3. 3NF:
	* It must be in 2NF
	* Must also remove all transitive dependencies
	* 3NF can be achieved by sticking to the mantra, 'every non-key attribute must depend on the full primary key, and nothing but the full-primary key'