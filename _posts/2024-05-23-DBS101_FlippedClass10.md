---
Title: DAM101 Unit Ten
categories: [DAM101, Unit Ten]
tags: [DAM101]
---
# Transaction

**What is transaction ?**

![transaction](https://static.vecteezy.com/system/resources/thumbnails/000/290/969/small/3__2835_29.jpg)


In a database management system (DBMS), a transaction is a sequence of one or more operations (such as read, write, update, or delete) executed as a single logical unit of work.

In databases,a transaction is a unit of program execution that accesses and possibly updates various data items.

The transaction consists of all operations executed between the **begin transaction** and **end transaction.**

### **Begain Transaction**

Begin Transaction marks the start of a new transaction. This indicates to the DBMS that all subsequent operations should be treated as a single, atomic unit of work. 

### **End Transaction**

End Transaction can mean either committing the transaction or rolling it back, depending on the outcome of the operations within the transaction block.

![ok](https://sqlmct.com/wp-content/uploads/2019/05/Begin_Commit-766x437.png)

## Properties a transaction should possess

![acid](https://static.javatpoint.com/sqlserver/images/sql-server-transaction2.png)

### Atomicity:

Atomicity is one of the core properties of database transactions, encapsulated within the ACID (Atomicity, Consistency, Isolation, Durability) principles that govern transaction management in database systems.

Atomicity ensures that a series of database operations within a transaction are treated as a single, indivisible unit of work. This means that either all operations in the transaction are executed successfully, or none of them are.

### Consistency:

Consistency is one of the core properties of database transactions, represented by the "C" in the ACID (Atomicity, Consistency, Isolation, Durability) principles.

In Database Management System (DBMS), consistency ensures that a transaction brings the database from one valid state to another valid state, maintaining the database's defined rules and constraints.

### Isolation:

Isolation is one of the key properties of database transactions, encapsulated within the ACID (Atomicity, Consistency, Isolation, Durability) principles.

In Database Management System (DBMS), isolation ensures that the operations of one transaction are hidden from other transactions until the transaction is committed, thereby preventing concurrent transactions from interfering with each other.

### Durability:

Durability property of DBMS is a important property if database that ensures that once a transaction is committed, its changes are permanent and will survive any system failures, such as crashes or power outages.

It guarantees that once data is written to the database, it will persist even in the event of hardware failures or software crashes.

***Lets imagine and understand what is actually happining***

Consider a transaction Ti that transfers $50 from account A
to account B.

The initial value of accounts: 

Account **A** is = $1000
Account **B** is = $2000

Steps involved are:

1. Transaction Ti reads the current balance of account A, which is $1000.
2. Transaction Ti subtracts $50 from the balance of account A.
3. After this operation, the balance of account A becomes $950.
4. Transaction Ti writes the new balance of account A, which is $950, back to the database.
5. Transaction Ti reads the current balance of account B, which is $2000.
6. Transaction Ti adds $50 to the balance of account B.
7. After this operation, the balance of account B becomes $2050.
8. Transaction Ti writes the new balance of account B, which is $2050, back to the database.

## Pactical Implementation of transaction in Posatgresql

**Steps Included:**

1. Lets create a database called **test_transaction** 

    ![alt text](<../image/Screenshot 2024-05-23 at 10.08.30 PM.png>)

2. Lets create a new table call **accounts**

    ![alt text](<../image/Screenshot 2024-05-23 at 10.12.23 PM.png>)

3. Inserting values inside the table **accounts**

    ![alt text](<../image/Screenshot 2024-05-23 at 10.13.55 PM.png>)

4. ***OK! Now lets begain the transaction***

    ![excired](https://media.tenor.com/taqSRWFOkaQAAAAM/kung-fu-panda.gif)

5. Start Transaction

    ![alt text](<../image/Screenshot 2024-05-23 at 10.27.07 PM.png>)
    ![oh](https://media.tenor.com/dnqXn34Lf2sAAAAj/frustrated-master-shifu.gif)

6. From the accounts A and B, we will update the balance by either deducting or adding to the previous value.

    **Initial**
    ![alt text](<../image/Screenshot 2024-05-23 at 10.13.55 PM.png>)
    **After updating**
    ![alt text](<../image/Screenshot 2024-05-23 at 10.35.41 PM.png>)

7. Commiting the changes made in both the accounts and after commiting the changes we cannot perform ROLL BACK operation or undo the changes.

    ![alt text](<../image/Screenshot 2024-05-23 at 10.38.36 PM.png>)

## Storage Structure in DB

Storage media categorized based on **speed**, **capacity**, and **resilience**:

1. Volatile storage
2. Non-volatile storage
3. Stable storage

### **1. Volatile storage**

* Volatile storage refers to computer memory that requires power to maintain the stored information.
* When the **power is turned off** or there is a system crash, the data stored in volatile storage is **lost**.
* This type of storage is typically used for temporary data that is needed during the processing of transactions but does not need to be permanently retained.
* Access is fast, allows direct access to data items.

### **2. Non-volatile storage**

* Non-volatile storage refers to computer memory that **retains stored data even when the power is turned off**.
* This type of storage is essential for databases to ensure data persistence, durability, and long-term retention of information.
* Non-volatile storage is used to store critical data such as database files, transaction logs, and backup files.
* Slower than volatile storage, especially for random
access.
- Susceptible to failures leading to data loss.

### **3. Stable Storage**

- type of storage that is highly reliable and ensures data durability and integrity even in the face of multiple failures, such as power outages, hardware malfunctions, or software bugs

- Achieved by replicating data in multiple non-volatile storage media with independent failure modes (usually disk)

**For a transaction to be durable:**
- Changes must be written to stable storage.


**For a transaction to be atomic:**
- Log records must be written to stable storage before any changes to the disk database.

- Log records each database modification, including transaction and data item identifiers, old and new values.

- Log-based recovery enables redoing or undoing modifications to ensure atomicity and durability.

- Committed transaction alters database into a new consistent state, persisting despite system failures.

- Committed transactions cannot be undone by aborting; compensating transactions may be necessary.

### Simple transaction state model

- Active: Initial state, transaction executing.

- Partially committed: After final statement execution.

- Failed: Normal execution can't proceed.

- Aborted: Rolled back, database restored to pre-transaction state.

- Committed: Successfully completed.

![model](https://i.imgur.com/b857XSq.png)






