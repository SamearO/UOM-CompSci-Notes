> The web programming has nothing to do with databases so I'll get back to them later

# MySQL Triggers
* Triggers are stored programs in MySQL that are invoked in response to an event. 
* Events are `INSERT`, `UPDATE` and `DELETE`.
* Triggers are either run `BEFORE` or `AFTER` the query is executed.
* They can be used to check data integrity, run scheduled tasks or for auditing data changes.
* `BEFORE` triggers are useful to update or validate records before storing them in the database.
* `AFTER` triggers are used to access fields set by the system such as a record's ID.

## Showing Triggers
```SQL
SHOW TRIGGERS;

DROP TRIGGER trigger_name; -- deleting a trigger
```

## Creating Triggers
* `BEFORE` can also be `AFTER`.
* `INSERT` can also be `UPDATE` or `DELETE`.
* `FOLLOWS` or `PRECEDES` allows for triggers to be daisy chained.
* Using `FOLLOWS` or `PRECEDES` can be bad practice hence it is better to create only 1 trigger and call procedures on it.

```SQL 
CREATE TRIGGER trigger_name 
    BEFORE INSERT ON table_name 
    FOR EACH ROW -- FOR EACH ROW is optional
    FOLLOWS previous_trigger -- can also be PRECEDES
BEGIN
    INSERT INTO table_audit
    old_row = OLD.row_name -- OLD and NEW can be used to query the previous data
END

```