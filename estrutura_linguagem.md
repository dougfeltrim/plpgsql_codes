# Estrutura da linguagem Pl/pgsql
```plpgsql
CREATE [OR REPLACE] FUNCTION nome ([tipo_param1],[tipo_param2],...)
RETURNS tipo_retorno
AS
'
    DECLARE
        varialvel tipo_variavel;
        ...
    BEGIN
        instrução
        ... 
        RETURN valor_retorno;
    END;
'
LANGUAGE 'plpgsql';
```