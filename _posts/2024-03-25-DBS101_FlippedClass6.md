---
Title: DBS101 Flipped Class 6
categories: [DBS101, Flipped_Class_6]
tags: [DBS101]
---

# Document based databases

Document based database is a type of **NoSQl database** which does not use the **relational model to store data**, instead it uses the documents to store the data in the database.

![relational database model and document based database](https://developer.couchbase.com/static/relational_vs_doc1-bcb37aacf0a51c8c73ec1439ad962e9a.png)

A document database stores data in JSON, BSON, or XML documents.

Documents can be stored and retrieved in a form that is much more similar to a dictionary with keys and value.


Elements can be accessed by using the index value that is assigned for faster querying.

### Differences between the relational database model and document based database.

|         Relational Database Model                             |            Document database                                       |
|:--------------------------------------------------------------|:-------------------------------------------------------------------|
|1. Data are stored using rows and columns in a table           | 1. Data is stored using documents .                                   |
|2. Uses SQL commands                                           |2. Uses NOSQL commands.                                             |
|3. Relational databases have a structured schema that defines the tables, columns, data types, constraints, and relationships between tables.                                                 |3. Document databases have a flexible schema, allowing documents within a collection to have varying structures.|
|4. There are relationships between the tables and it is referred using FOREIGNl  KEYS.|4. There is no dynamic relationship between two documents so documents can be independent of one another.|


# Key-Value based databases

* Key value database is another type of database that does not use tables to store data; instead,  every data element in the database is stored in key-value pairs.

    ![key value db](https://www.scylladb.com/wp-content/uploads/Key-Value-Database-diagram-1-e1644958285831.png)

* Data is retrieved using the unique key allotted to each element in the database.

* Key value databases only have two columns, one for key and one for their value.

* The value stored can be simple data types like strings and numbers or complex objects.

### **Features on the key value db**

**Simplicity**

* Key-value databases have one of the simplest data models among NoSQL databases.

* schemas are less fashioned there for data is stored in key value format in two columns.

**Scalability**

* support data replication which means maintaining multiple copies of data across different nodes, allowing the system to continue operating even if some nodes fail.

* Horizontal scalability, also known as scaling out, refers to the ability to increase the capacity or performance of a system by adding more hardware or resources.

* Horizontal scalability involves adding more servers or nodes to handle increased workload or data volume.

**Speed**

* Since data is accessed directly by its unique key, retrieval times are typically fast and predictable, especially for simple lookup operations 
