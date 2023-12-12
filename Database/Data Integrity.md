  
In database design, ensuring data integrity is crucial for maintaining accurate, consistent, and reliable data. Data integrity refers to the overall completeness, accuracy, and consistency of data. There are several types of data integrity that are important in the context of database design:

1. **Entity Integrity**: This ensures that each row in a table is a unique entity. It is usually enforced by defining a primary key for each table, so no two rows can have the same value for the primary key fields, and none can have a null value in those fields.
   Sikrer at der er en specifik entry per entity, ved at give dem et unikt id
    
2. **Referential Integrity**: This involves maintaining consistency among rows of different tables. It is typically enforced through foreign keys. Referential integrity ensures that a foreign key value always points to an existing row in the referenced table or is null.
    
3. **Domain Integrity**: This type of integrity ensures that each column in a database adheres to a specific domain. It is about the validity of entries for a given column. This can involve restrictions like data type, range constraints, format constraints, and uniqueness constraints.