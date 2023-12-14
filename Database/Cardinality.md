# [[One-to-one]] relationships:

One entity that has a relationship with one other entity. If one entity have only one attribute, and that is the relationship itself, it can simply be put as an attribute of the other entity. For example, a user and a username. The username likely would only have the user as an attribute, and can therefore be put as an attribute in a User table. 
However, if both entities have multiple attributes, like a car with a model, color, age and so on, and an owner, that has a name and age and so on, they need to be put in separate Owner and Car tables, and connected with a foreign key. 

Implemented typically by splitting the tables up into two tables, and connecting them with a foreign key, in the child table. The foreign keys need to be unique. 


# [[One-to-many]] relationships:

Same as a one-to-one basically, but the foreign keys need'nt be unique, 

# [[Many-to-many]] relationships:
Typically solved with a junction table, which is a table specifically holding relationships. 

