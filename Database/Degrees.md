The degree of a relationship, is the amount of entity types involved in the relationship. 

* A unary relationship only has one entity type. It is typically solved by adding a foreign key column, that holds primary keys to former entries in the very same table.
* Binary relationships, are probably the more classic types, and are usually solved with a junction table, or whatever is fitting the relationship cardinality. 
* Ternary/higher order: These are just like binary relationships, but with x entity-types involved. They're are solved similarly to binary relationships, just with more columns for foreign keys in the junction table. 