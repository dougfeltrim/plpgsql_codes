```plpgsql
# Ex1:

CREATE OR REPLACE FUNCTION media (NUMERIC, NUMERIC)
RETURNS NUMERIC
AS
' 
    DECLARE result NUMERIC;
    BEGIN
        result := ($1 + $2) / 2;
        RETURN result;
    END;
'
LANGUAGE 'plpgsql';


#Ex2:

CREATE OR REPLACE FUNCTION media (NUMERIC, NUMERIC, NUMERIC)
RETURNS NUMERIC
AS
' 
    DECLARE result NUMERIC;
    BEGIN
        result := ($1 + $2 + $3) / 3;
        RETURN result;
    END;
'
LANGUAGE 'plpgsql';
```