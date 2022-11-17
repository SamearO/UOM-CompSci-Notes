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

# Converting UNF to 3NF
Example is using the following functional dependencies:
* AB -> C
* A -> DE
* B -> F
* F -> GH
* D -> IJ

## Converting to 2NF
* Start by identifying the attributes that are functionally dependant on either part of the key.
* The key is a minimal set of attributes who's closure includes all attributes. 
* In this case it is `AB`.
* Split them based on the key they are FD on.
* Make relations for attributes that are FD of a combination of the key.

Therefore:

1. R1 = {[A], D, E, I, J}
2. R2 = {[B], F, G, H}
3. R3 = {[A,B], C}

## Converting to 3NF
* For each of the previous relations, split them based on their transitive dependencies.

Therefore:
1. R11 = {[D], I,J}
2. R12 = {[A], D, E}
3. R21 = {[F], G, H}
4. R22 = {[B], F}
5. R3 = {[A,B], C}

