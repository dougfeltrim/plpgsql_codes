# Comandos

## Executando uma função:
```plpgsql
> SELECT nome_função (parâmetros);
```
## Excluindo uma função:
```plpgsql
> DROP FUNCTION nome ([tipo_param [, tipo_param, …]])
```
## Comentários:
```plpgsql
Comenta até o final da linha:  --

/*

 Comenta todas as
 linhas incluídas

*/
```
## Parâmetros

O tipo de cada parâmetro é definido na lista de parâmetros na assinatura da função.

São nomeados automaticamente, de acordo com a ordem na lista:  <b>$1, $2, etc.</b>

Obs: os parâmetros são <b>CONSTANTES</b>.

Portanto, <b>não</b> podem receber valores no corpo da
função.

# Declaração de variáveis
As variáveis são declaradas na seção <b>DECLARE</b>.

O nome pode incluir letras, underscores e números (estes não no início).
O nome é case <b>INsensitive</b>.

Variáveis podem ser inicializadas na declaração:

DECLARE salario NUMERIC := 1000;

### Obs 1: variáveis não podem ser inicializadas na declaração usando-se parâmetros ou outras variáveis:
```plpgsql
DECLARE salario NUMERIC := 1000;
 desconto NUMERIC := salario * 0.15; ---> ERRO!
```
### Obs 2: CONSTANTES são declaradas assim:
```plpgsql
DECLARE pi CONSTANT REAL := 3.141593;
```

# Apelidos
### Normalmente, é bastante útil criar apelidos para os parâmetros, para que possam ser usadosno corpo da função. Isto é feito através da cláusula ALIAS FOR:
```plpgsql
DECLARE saldo ALIAS FOR $1;
        saque ALIAS FOR $2;
```

# Tipos Especiais
## Há 3 tipos (pseudo-tipos) de dados que se adaptam aos tipos originais de um atributo ou de uma tupla de uma tabela, ou ainda do conjunto de atributos de um result set.

### O tipo %TYPE permite que se defina uma variável com o mesmo tipo de outra variável ou com o mesmo tipo de um atributo específico de uma tabela. Ex:
```plpgsql
DECLARE endereço1 CHAR(25);
        endereço2 endereço1%TYPE;
        desconto Produto.preço%TYPE;
```
### O tipo %ROWTYPE permite que se defina uma variável do tipo registro, possuindo os mesmos campos de uma determinada tabela.Ex:
```plpgsql
DECLARE um_cliente Cliente%ROWTYPE;
```
### O tipo RECORD permite que se defina uma variável do tipo registro, cuja estrutura será determinada em tempo de execução, adaptando-se aos dados  que se deseja armazenar na mesma.

# Atribuições
Atribuições permitem que se estabeleça um novo valor para uma variável. O operador utilizado é := . Ex:
```plpgsql
saldo := saldo + saque;
```