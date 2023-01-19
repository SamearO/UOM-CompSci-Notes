# Not Only SQL 

* Databases that don't rely on `Relational Database Models`.
* Databases that have a different priority to `RDBMs`.

## Categories of NoSQl Databases
* `Key` based databases using key value pairs.
* `Document` based databases.
* `Column` based databases where each column is stored in its own file for managing large data stores.
* `Graph` based stores entities as nodes and relations as edges.

## CAP Theorem
* `Consistency`: All nodes should contain the same copies of replicated data.
* `Availability`: The system should be consistently available for read and write operations
* `Partition Tolerance`: The system should continually be available in situations where the system is partitioned due to a network fault
* The theorem is that any database can only have 2/3 of these desirable properties.
* SQL has `Consistency` and `Availability` while MongoDB has `Consistency` and `Partition Tolerance`.

## Eventual Consistency
* Most NoSQL distributed databases accept a weaker consistency while guaranteeing availability and partition tolerance hence the database will `eventually be consistent`.