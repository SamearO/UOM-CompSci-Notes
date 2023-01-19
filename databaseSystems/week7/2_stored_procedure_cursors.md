# Stored Procedure Cursors
* A cursor allows iteration through a record set within a stored procedure. They are:
    * Read only
    * Non scrollable
    * Asensitive (points to the actual data instead of making a copy)

```SQL
DELIMTER //
CREATE PROCEDURE createEmailList(
    INOUT emailList varchar(4000)
)
BEGIN
    DECLARE finished INTEGER DEFAULT 0; -- gets set to 1 via handler to show that the cursor has terminated
    DECLARE emailAddress varchar(100) default "";

    DECLARE curEmail CURSOR FOR SELECT email from employees; -- declaring the cursor

    DECLARE CONTINUE HANDLER
        FOR NOT FOUND SET finished = 1; -- set finished to the handler value    

    OPEN curEmail; -- start loop
    getEmail: LOOP
        FETCH curEmail INTO emailAddress;
        IF finished = 1 THEN
            LEAVE getEmail;
        END IF;

        -- loop body starts here
        SET emailList = CONCAT(emailAddress, ";". emailList);

    CLOSE curEmail;
END //
DELIMITER ;
```