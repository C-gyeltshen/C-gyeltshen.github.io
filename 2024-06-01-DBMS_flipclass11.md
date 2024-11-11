---
Title: DAM101 Unit Eleven
categories: [DAM101, Unit Eleven]
tags: [DAM101]
---


# Lesson 26:Database Locks and Concurrency Control

## Introduction to Concurrency Control

The prevention of concurrent access in a database is crucial for the sake of achieving the recoverability of transaction in a database. As a result of concurrency control, when several transactions perform at the same time, it becomes difficult to maintain isolation. Concurrency-control techniques keep track of the conflicts as well as cooperation of concurrent activities to allow for compatibility.

## Locks

**Access controls** are the basic ways of protecting data through the use of locks. They assist in keeping the transaction isolation since a single transaction can update a data item at any moment.

![lock](data:image/png;base64,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)

### Types of Locks

- **Shared Lock (S):** Enables a transaction to access a data item to retrieve information but cannot update it. A shared lock is basically a read-only lock for a row level.

- **Exclusive Lock (X):** Enables a transaction to perform both ‘read’ and ‘modify’ operations on a data item. An exclusive lock is read as well as a write lock.

    ![example](https://www.geeksforgeeks.org/wp-content/uploads/1-28.png)

### Why Lock Resources?

Locking guarantees that specific data items are locked at any one time and can be accessed by only one process at a time. It prevents other TANs access the locked data while a distinct transaction retains the lock in its language, therefore providing isolation.

### Lock Management

The concurrency-control manager invokes a transaction to request lock. A manager gives accesses according to compatibility with existing locks and queued activities, allowing multiple readers or a writer only.

## Two-Phase Locking (2PL)

Two-phase locking, is a protocol that is used in transactions, so that all the transaction operations be made serially. It involves two phases:

1. **Growing Phase:** They take locks and clients cannot unlock them.

2. **Shrinking Phase:** Transactions are rich to release locks and never acquire new ones.

    ![two-phase-lock](https://www.researchgate.net/publication/202199234/figure/fig4/AS:305900326801412@1449943729717/Two-Phase-Locking-Protocol.png)

## Deadlocks

Deadlock condition is a situation where the transactions wait endlessly for the locks to be released by the other transaction that is also waiting for the same from the first transaction.

### Handling Deadlocks

- **Deadlock Detection:** In a waits-for graph, the system checks for cycles after a certain time has elapsed.

- **Deadlock Prevention:** They limit transactions that cause a deadlock through aborting them based on priorities.

### Deadlock Prevention Schemes

- **Wait-Die:** Older Transactions wait for the Young ones.

- **Wound-Wait:** Consumers start to make transactions in a sequence where younger transactions go hand in hand with older transactions.

    ![lock](https://docs.oracle.com/javadb/10.8.3.0/devguide/dead.gif)

## Lock Granularity

Lock granularity can be defined as the extent of the area that can be locked to allow data access and modifications, which may involve attributes, a single tuple, a page, a table, and so on. The concept of coarser granularity present less overhead or amount of information needed, but lacks parallelism compared to finer granularity which presents more overhead or more amount of information needed together with more parallelism.

## Intention Locks

Intention locks contain locking at various degrees of abstraction without having to traverse down to specific nodes.

- **IS (Intention-Shared):** Specifies where an intention of acquiring shared locks at a lower degree exists.

- **IX (Intention-Exclusive):** Refers to a desire to obtain exclusive locks at a different level and is expressed by setting an intention to either acquire exclusive locks and perform locking or to do what is needed and acquire locks.

- **SIX (Shared + Intention-Exclusive):** Signals that the node is in shared mode and there are other, more restrictive, lock types lower in the hierarchy.

## Implementation of Locking

Lock management is responsible for managing lock requests while at the same time, it keeps a record of locked data in a lock table. It prevents any eventualities such as starvation and it resolves deadlocks, by identifying and taking the right measures.

## Concurrency Control Approaches

- **Pessimistic Concurrency Control:** It has expectations that conflict is inevitable and acts with a view of preventing it. Two well-known protocols are Two-Phase locking and Timestamp ordering.

- **Optimistic Concurrency Control:** Implements conflicts as being an exception and looks for them after a transaction, performing actions in case they are met.

### Timestamp Ordering Concurrency Control

In order for the transactions to be scheduled based on the time of execution they are given time stamps. In the example of the Thomas Write Rule, certain violations of the strict timestamp order could help in avoiding unnecessary aborts.

### Multi-Version Concurrency Control (MVCC)

MVCC provides multiple versions of data items so that a reader can reads a snapshot of the database in which no transaction is currently executing iff it checks some validity predicate and a writer can write into a new version of the database knowing that no reader is currently reading it iff it checks some validity predicate. It essential for the protocol to allow multiple concurrent clients and time travel semantic queries.

### Snapshot Isolation (SI)

In SI, through the isolation property of a transaction a transaction only views a consistent state of the database as it begun at the time when a particular transaction was initiated. This isolation level is invaluable to help avoid some of the anomalies but it is not immune to the write skew anomalies.

## Advanced Concurrency Control Techniques

Persistent locking techniques or prepared locking may not be advantageous in long duration transactions or applications with low level of emphasis on strict data consistency. It is also necessary to note that higher, advanced levels of techniques and weak consistency levels can optimize the concurrency and guarantee acceptable level of consistency.