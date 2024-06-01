---
Title: DAM101 Unit Eleven
categories: [DAM101, Unit Eleven]
tags: [DAM101]
---


# Lesson 26:Database Locks and Concurrency Control

## Introduction to Concurrency Control

The prevention of concurrent access in a database is crucial for the sake of achieving the recoverability of transaction in a database. As a result of concurrency control, when several transactions perform at the same time, it becomes difficult to maintain isolation. Concurrency-control techniques keep track of the conflicts as well as cooperation of concurrent activities to allow for compatibility.

## Locks

Access controls are the basic ways of protecting data through the use of locks. They assist in keeping the transaction isolation since a single transaction can update a data item at any moment.

### Types of Locks

- **Shared Lock (S):** Enables a transaction to access a data item to retrieve information but cannot update it.

- **Exclusive Lock (X):** Enables a transaction to perform both ‘read’ and ‘modify’ operations on a data item.

### Why Lock Resources?

Locking guarantees that specific data items are locked at any one time and can be accessed by only one process at a time. It prevents other TANs access the locked data while a distinct transaction retains the lock in its language, therefore providing isolation.

### Lock Management

The concurrency-control manager invokes a transaction to request lock. A manager gives accesses according to compatibility with existing locks and queued activities, allowing multiple readers or a writer only.

## Two-Phase Locking (2PL)

Two-phase locking, is a protocol that is used in transactions, so that all the transaction operations be made serially. It involves two phases:

1. **Growing Phase:** They take locks and clients cannot unlock them.

2. **Shrinking Phase:** Transactions are rich to release locks and never acquire new ones.

## Deadlocks

Deadlock condition is a situation where the transactions wait endlessly for the locks to be released by the other transaction that is also waiting for the same from the first transaction.

### Handling Deadlocks

- **Deadlock Detection:** In a waits-for graph, the system checks for cycles after a certain time has elapsed.

- **Deadlock Prevention:** They limit transactions that cause a deadlock through aborting them based on priorities.

### Deadlock Prevention Schemes

- **Wait-Die:** Older Transactions wait for the Young ones.

- **Wound-Wait:** Consumers start to make transactions in a sequence where younger transactions go hand in hand with older transactions.

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