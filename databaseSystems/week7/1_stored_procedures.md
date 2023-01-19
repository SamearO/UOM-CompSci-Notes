# Stored Procedures

* Stored procedures are segments of declarative SQL statements stored within the MySQL server.
* They can be called using the `CALL` statement.
* They are cached when called.
* They allow `passing of arguments`, `flow control` and can `call other procedures`.

## Advantages of Stored Procedures
* Minimises bandwith by reducing the need for sending SQL statements back and forth.
* Allows for `write once use anywhere` queries that are often common and complex.
* They are consistent as they can be used by multiple applications.
* They are more secure as stored procedures can be granted to specific applications without having to impose security rules on the underlying data.

## Disadvantages of Stored Procedures
* Additional system requirements.
* They are difficult to debug.
* They require a specialised skillset to operate.

## Stored Procedure Syntax
* The delimiter must be changed temporarily so that the SQL client does not terminate the query early.
* They can be deleted with `DROP procedure myProcedure;`
* They can be called with `CALL myProcedure();`
* They cannot be edited with SQL statements.

### Stored Procedures with inputs
* Parameters can be passed in and out of the procedure:
    * `IN` refers to parameters that are passed in and cannot be changed.

```SQL
DELIMITER //
CREATE PROCEDURE myProcedure(IN my_variable DATE, INT, INOUT inout_variable INT, OUT other_variable) --passing in variables
BEGIN
    SELECT * FROM my_table
    WHERE table_col = my_variable; -- using variables

    SELECT SUM(T.tot)
    INTO other_variable -- inputing into output variable
    FROM (
        SELECT number FROM my_table
    ) AS T -- creating namespace that can be used outside

    SET inout_variable = T.tot --changing inout variable

END //
DELIMTER ; 

-- Above procedure called with:
SET my_var = 10;
CALL myProcedure("19-1-2023", @my_var, @output_var)
```

### Variables in Stored Procedures
* Stored Procedures can themselves declare variables with `DECLARE variable_name VAR_TYPE DEFAULT default_value;`
* EG: `DECLARE totalOrder INT DEFAULTVALUE 0;`

### Flow Control in Stored Procedures
> loops are compared in the stored procedure cursors section
* SQL Statements support flow control.

```SQL
IF credit > 5000 THEN
    SET cust_level = "Gareth"
END IF
```

## Showing Stored Procedures
* Stored procedures are stored in `information_schema.routines` hence can be "showed".
```SQL
SELECT routine_name
FROM information_schema.routines
WHERE routine_type = 'PROCEDURE'
AND routine_schema = 'classicmodels';
```

## Stored Procedure Cursors
* A cursor allows iteration through a record set within a stored procedure. They are:
    * Read only
    * Non scrollable
    * Asensitive (points to the actual data instead of making a copy)