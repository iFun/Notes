# ECE 356


## Introduction to database

### Drawbacks of Using File System
- cannot answer queries directly
- cannot enforce integrity
- lead to data redundancy and inconsistency
- updates in a file system are not always atomic
- offer limited support for multiple users
- not enough security

### Three levels in database

1. **Physical**  level: describes how a data is stored
2. **Logical level**: describes the structure of the data stored in a database and the relationship among the data
3. **View level**: describes a virtual structure of the data imposed by the database designer on top of the logical level(student and instructor have different views)

### Physical vs logical Schema
    Schema: the shape of structure of the databse
    Physical Schema: design at physicallevel(storage, file formats, indexes)
    logical Schema: design at logical level(data types, relations, rows, columns)
### Physical and logical data independence
The ability to modify the physical schema without changing the logical schema or the application program

## Entity-Relationship Model
#### 4 build blocks of the ER model
1. entities(*object that exists and unique from other objects*) and entity sets
2. relationships and relationship sets
3. constraints: cardinality, participation
4. primary keys

An __attribute__ can also be a property of a relationship set
Most common type of relationship is a binary relationship

An __entity__ is represented by a set of attributes

    Example: instructor = (ID,name,street,city,salary)
Domain is the set of permitted values for an attribute

    Example: salary has to be larger than 0

A __composite attribute__ comprise a collection of component attribute.
i.e. name -> first_name, middle_name, last_name

#### 4 mapping in a binary relationshsip
1. one to one
2. one to many
3. many to one
4. many to many

### Keys(super key and candidate key)

superkey = candidate key + some other unique keys

one of the candidate key selected by the designer is called __primary key__




## Indexing and Hashing















