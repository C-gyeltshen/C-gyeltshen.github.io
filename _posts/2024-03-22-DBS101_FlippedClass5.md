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
2. Boyce-Codd Normal Form (BCNF)
3. Third Normal Form
4. Fourth Normal Form

## First Normal Form and Second Normal Form 

### First Normal Form

* First Normal Form states that an attribute of a table cannot hold multiple values. It must hold only single-valued attributes, or the value must be an atomic value.

* First Normal Form disallows multi-valued attributes, composite attributes, and their combinations.


    | EMP_ID      |  EMP_NAME     |       EMP_PHONE         |           
    |-------------|:-------------:|------------------------:|
    |     1       |  Chimi        | 17895216,77207234       |
    |     2       |    Sonam      | 17851105                |
    |     3       | Rinchen       | 17486374                |
    **Table 1**


    ***TO:***

    | EMP_ID      |  EMP_NAME     |  EMP_PHONE |           
    |:-----------:|:------------:|:-----------:|
    |     1       |  Chimi        | 17895216   |
    |     1       |  Chimi        | 77207234   |
    |     2       |    Sonam      | 17851105   |
    |     3       | Rinchen       | 17486374   |
    **Table 2**

* Multi valued attribute EMP_PHONE got decomposed after normalization.

### Second Normal Form

* To be in the **second normal form**, a relation must be in the **first normal form**, and the relation must not contain any **partial dependency** of attributes toward the primary key.

* In the second normal form, all non-key attributes should be fully functionally dependent on the primary key.

    |  	   Teacher_id       |  	 Subject          |  	  Teacher_age            |
    |:---------------------:|:-------------------:|:----------------------------:|
    |  3	                |      English        |         34                 	 |
    |  	4                   |  	   Dzongkha       |  	     56                  |
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
