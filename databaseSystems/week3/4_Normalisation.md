# Normalisation

Normalisation is the process of organizing the data with a focus on minimizing redundancy in relations or a set of relations.

The first 3 Normal forms (out of 6) address these anomalies:

1. `Insertion Anomaly:` Omission of data during insertion due to absence of other data.
2. `Deletion Anomaly:` Unintended loss of data due to deletion of other data.
3. `Update Anomaly:` Data inconsistency that results from redundant data and partial updates.

## First Normal Form
A table is in 1NF if:
1. There are no repeating groups
2. The values in each column cannot be divided (atomic, so no composite attributes)

## Second Normal Form
A table is in 2NF if: 
1. It is in 1NF
2. There are no partial dependencies (every non-key attribute is Functionally Dependant on the Primary Key)

## Third Normal Form
A table is in 3NF if:
1. It is in 2NF
2. There are no transitive dependencies for non-key attributes. (Eg if A->B and B->C, the table should be split into AB and BC)