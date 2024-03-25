---
Title: DBS101 Flipped Class 5
categories: [DBS101, Flipped_Class_4]
tags: [DBS101]
---

# Normal Form


**Normalization** refers to the process of organizing the attributes and tables of a relational database to minimize redundancy and dependency.

A **Normal Form** is a set of guidelines or rules that define how data should be organized within tables to minimize redundancy and dependency, thereby reducing the likelihood of data anomalies.

**Data anomalies** are inconsistencies or errors that can occur in a database when it is not properly normalized.

There are many types of normal forms, and some of the normal forms that I have learned are:

1. First and Second Normal Form
2. Third Normal Form
3. Boyce-Codd Normal Form (BCNF)
4. Fourth Normal Form

## 1. First Normal Form and Second Normal Form 

### First Normal Form

* First Normal Form states that an attribute of a table cannot hold multiple values. It must hold only single-valued attributes, or the value must be an atomic value.

* First Normal Form disallows multi-valued attributes, composite attributes, and their combinations.


    | EMP_ID      |  EMP_NAME     |       EMP_PHONE         |           
    |-------------|:-------------:|------------------------:|
    |     1       |  Chimi        | 17895216,77207234       |
    |     2       |    Sonam      | 17851105                |
    |     3       | Rinchen       | 17486374                |

    **Table 1**


    | EMP_ID      |  EMP_NAME     |  EMP_PHONE |           
    |:-----------:|:------------:|:-----------:|
    |     1       |  Chimi        | 17895216   |
    |     1       |  Chimi        | 77207234   |
    |     2       |    Sonam      | 17851105   |
    |     3       | Rinchen       | 17486374   |

    **Table 2**

* Multi valued attribute EMP_PHONE got decomposed after normalization.

### Second Normal Form.

* To be in the **second normal form**, a relation must be in the **first normal form**, and the relation must not contain any **partial dependency** of attributes toward the primary key.

* In the second normal form, all non-key attributes should be fully functionally dependent on the primary key.

    ![primary key and non key attribute](https://s3.studytonight.com/curious/uploads/pictures/1689067555-.png)

    |  	   Teacher_id       |  	 Subject          |  	  Teacher_age            |
    |:---------------------:|:-------------------:|:----------------------------:|
    |   3	                |      English        |         34                 	 |
    | 	4                   |  	   Dzongkha       |  	     56                  |
    |  5	                |      Chemistry      |  	     34                  |
    |  6	                |      physics        |          45                	 |
    |  7	                |  	   Maths          |  	     65                  |

* Non-prime attribute TEACHER_AGE is dependent on TEACHER_ID, which is a proper subset of a candidate key. That's why it violates the rule for 2NF.

* To convert the given table into 2NF, we decompose it into two tables:
    1. TEACHER_DETAIL table
    2. TEACHER_SUBJECT table

    **1. TEACHER_DETAIL table**

    |  	   Teacher_id       |  	 Subject          | 
    |:---------------------:|:-------------------:|
    |  3	                |      English        |         
    |  	4                   |  	   Dzongkha       |  	   
    |  5	                |      Chemistry      |  	                   
    |  6	                |      physics        |          
    |  7	                |  	   Maths          | 


    **2. TEACHER_SUBJECT table**

    |  	   Teacher_id       |	  Teacher_age          |
    |:---------------------:|:------------------------:|
    |  3	                |          34              |
    |  	4                   |          56              |
    |  5	                |          34              |
    |  6	                |         45               |
    |  7	                |  	      65               |

## 2. Third Normal Form

A table is said to be in the Third Normal Form when,
1. It satisfies the First Normal Form and the Second Normal form.
2. And, it doesn't have Transitive Dependency.

**Transitive dependency ?**

* Transitive dependency occurs when a non-prime attribute ( attribute that is not part of any candidate key) depends on another non-prime attribute, rather than directly on a candidate key.

**Example**

Let's say we have a table called Employee with attributes (Employee_ID, Employee_Name, Department, Manager). Here, Employee_ID is the primary key, and Manager represents the manager of each employee.

| Employee_ID | Employee_Name | Department | Manager   |
|-------------|---------------|------------|-----------|
| 1           | Chimi         | IT         | Sonam     |
| 2           | Sonam         | HR         | Rinchen   |
| 3           | Rinchen       | Finance    | Tshering  |

* Manager depends on the Department and Department depends on Employee_ID, then we have a transitive dependency because Manager depends indirectly on Employee_ID through the Department.

**To solve transitive dependency**

1. Decomposed Tables:

Employee:

| Employee_ID | Employee_Name |
|-------------|---------------|
| 1           | Chimi         |
| 2           | Sonam         |
| 3           | Rinchen       |

Department:

| Department | Manager   |
|------------|-----------|
| IT         | Sonam     |
| HR         | Rinchen   |
| Finance    | Tshering  |

## 3. Boyce-Codd Normal Form (BCNF)

**Functional dependency ?**

A functional dependency in a database refers to a relationship between two attributes in a relation (or table) such that one attribute's value uniquely determines the value of another attribute. It doesn't necessarily have to be between a primary key and a non-key attribute.

**Example of BCNF**

| EmployeeID | Name    | Department |
|------------|---------|------------|
| 1          | Nidup   | HR         |
| 2          | Bob     | IT         |
| 3          | Wangmo  | HR         |

In this case, EmployeeID serves as the primary key, and Name is functionally dependent on EmployeeID, because given an EmployeeID, there is only one corresponding Name. 

However, Department is not functionally dependent on EmployeeID, as multiple employees can belong to the same department.

* If a relational schema is in BCNF, then all redundancy based on functional dependencies has to be removed. 

* A table is in BCNF if every functional dependency X → Y, where X is the superkey of the table.

| Condition                                                                                                                                                 | Definition                                                                                                                                                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If a relational schema is in BCNF                                                                                                                         | Then all redundancy based on functional dependencies should be removed.                                                                                            |
| A table is in BCNF                                                                                                                                         | If every functional dependency X → Y, where X is the superkey of the table.                                                                                      |


## 4. Fourth Normal Form

* A relation will be in 4NF if it is in Boyce Codd normal form and **Fourth Normal** Form comes into picture when **Multi-valued Dependency** occur in any relation.

**Multi-Valued Dependency ?**

| bike_model | mani_year  | colour   |
|------------|------------|----------|
| R15        | 2022       | blck     |
| R15        | 2022       | red      |
| bmw        | 2018       | yellow   |
| bmw        | 2019       | golden   |

* Multivalued dependency occurs when two attributes in a table are independent of each other but, both depend on a third attribute.


* Suppose there is a bike manufacturer company which produces two colors(white and black) of each model every year.

* Here columns COLOR and MANUF_YEAR are dependent on BIKE_MODEL and independent of each other.

* In this case, these two columns can be called as multivalued dependent on BIKE_MODEL.

**Decomposed Tables:**

Table 1: bike_model and mani_year

| bike_model | mani_year  |
|------------|------------|
| R15        | 2022       |
| R15        | 2022       |
| bmw        | 2018       |
| bmw        | 2019       |

Table 2: bike_model and colour

| bike_model | colour   |
|------------|----------|
| R15        | black    |
| R15        | red      |
| bmw        | yellow   |
| bmw        | golden   |


We can split the original table into two tables to remove the multi-valued dependency between bike_model and mani_year. Now each table represents a single-valued dependency, ensuring that the database is normalized.




