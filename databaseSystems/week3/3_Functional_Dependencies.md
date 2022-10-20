# Functional Dependencies

* Is a constraint between 2 sets of attributes in a relation from a database.
* When an attribute or a set of attributes determine the value of another attribute in a database.
* Examination of `Functional Dependencies` helps create better designs by:
    * Preventing data being stored multiple times.
    * Maintains the quality of the data by making it easy to update/ delete data.
    * Helps determine relations and constraints.

## Functional Dependency Rules

* `Reflexive:` if `Y` is a subset of `X` then `X->Y`.
* `Augmentation:` if `X->Y` then `XZ->YZ`.
* `Transitivity:` if `X->Y` and `Y->Z` then `X->Z`.
* `Decomposition:` if `X->YZ` then `X->Y` and `X->Z`.
* `Pseudo-transitivity:` if `X->Y` and `EY->Z` then `XE->Z`.

## Closures

By determining the closure of `X` where X is a set of attributes, we can determine the keys for a relation.
1. All attributes must be functionally dependant on the key.
2. Candidate key should be minimal as the primary key will be chosen from the candidate keys.
