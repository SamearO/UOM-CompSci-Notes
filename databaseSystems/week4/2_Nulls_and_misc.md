# Nulls

Nulls are a state, not a data value where:
* The data value is unknown
* The data is withheld/ unavailable
* The data is not applicable

## Three valued logic with NULL in SQL

Introducing `NULL` creates more states for boolean logic.

### AND

| AND   | True    | False | NULL    |
| ----- | ------- | ----- | ------- |
| True  | True    | False | UNKNOWN |
| False | False   | False | False   |
| NULL  | UNKNOWN | False | UNKNOWN |

### OR

| OR    | True | False   | NULL    |
| ----- | ---- | ------- | ------- |
| True  | True | True    | True    |
| False | True | False   | UNKNOWN |
| NULL  | True | UNKNOWN | UNKNOWN |


# Stored Procedures

* Used to compose functions that can be used in more complex SQL queries.

```sql
CREATE PROCEDURE testProcedure()
BEGIN
Select * from test_table;
END

-- Calling the procedure
call testProcedure();
```

# Views
* A virtual table created by a query on another table.
* It can be queried but not changed unless the user has the right privileges.
* They can be used to provide different views to different communities or to protect sensitive data.

```sql
CREATE VIEW myView AS Select * from my_table where attribute IS NOT NULL

-- using the view
SELECT * FROM myView where attribute_1 IS NOT NULL
```
