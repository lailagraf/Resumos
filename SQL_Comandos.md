# Comandos SQL

## Comandos para criar tabelas e se conectar com banco de dados:
```sql
CREATE DATABASE nome_do_banco_de_dados;     --MySQL: criando banco de dados
USE nome_da_tabela;                         --MySQL: conectando-se a uma tabela
```

## Comandos que trazem informações sobre tabelas:
```sql
SHOW TABLES;                                --MySQL: mostra as tabelas do banco
DESC nome_da_tabela;                        --MySQL: mostra informações da estrutura de uma tabela 
SHOW CREATE TABLE TIME;                     --MySQL: descrição mais detalhada da tabela
```

## Comandos de criação de tabelas:
```sql
CREATE TABLE nome_da_tabela (                  --Cria e nomeia a tabela
    ID INT PRIMARY KEY AUTO_INCREMENT,         --Identifica a coluna primária / Auto_increment faz a numeração ser automática
    nome_da_coluna1 VARCHAR(50) NOT NULL,      --Nomeia a coluna e define o tipo de dado, NOT NULL define que é o dado é obrigatório
    nome_da_coluna2 INTEGER UNIQUE,            --Nomeia a coluna e define o tipo de dado, UNIQUE define que o dado tem q ser único, ou seja, não pode se repetir no banco

    nome_da_FK INT,                            --Cria uma chave estrangeira
    FOREIGN KEY(nome_da_FK)                    --Identifica a chave estrangeira
    REFERENCES nome_da_tabela(nome_da_coluna)  --Identifica a tabela de referência
);
```

**Tipos de dados:**
```sql
CHAR(1)                            --Define que o dado será do tipo caracter e deve ser usado quando sabemos que a quantidade de caracteres não irá variar.
VARCHAR(50)                        --Define que o dado será do tipo texto de até 50 caracteres
INT(11)                            --Define que o dado será do tipo número inteiro  
INTEGER                            --Define que o dado será do tipo número inteiro
FLOAT                              --Define que o dado será do tipo número real
BLOB                               --Define que o dado será do tipo objetos (fotos, documentos)
TEXT                               --Define que o dado será do tipo texto extenso
DATE                               --Define que o dado será do tipo data
ENUM('tipo','tipo2')               --MySQL: Define que o dado será do tipo texto domínio, ou seja uma seleção entre valores pré-definidos
```

## Comandos de inserção de itens na tabela:
```sql
INSERT INTO nome_da_tabela (nome_da_coluna1, nome_da_coluna2)   --Comando de identificação da tabela e colunas
VALUES                                                          --Comando para inserção de valores    
    (NULL, 9999),                                               --Quando não houver o dado, colocar NULL no campo
    ('Dado2', 9998);
```

## Comandos de atualização da tabela:
```sql
UPDATE nome_da_tabela                                      --Altera os dados especificados
SET nome_da_coluna = novo_valor
WHERE nome_da_coluna = 'Valor que identifica a linha';

ALTER TABLE nome_da_tabela                                 --Altera nome e tipos de dados de uma coluna
CHANGE nome_da_coluna novo_nome_da_coluna INT NOT NULL;

ALTER TABLE nome_da_tabela                                 --Adiciona a Primary Key na tabela
ADD PRIMARY KEY (nome_da_coluna);

ALTER TABLE nome_da_tabela                                 --Altera tipo de dados de uma coluna
MODIFY nome_da_coluna INT NOT NULL;

ALTER TABLE nome_da_tabela                                 --Adiciona nova coluna na tabela
ADD nome_da_coluna FLOAT(10,2) NOT NULL;

ALTER TABLE nome_da_tabela                                 --Adiciona nova coluna na tabela com uma posição definida
ADD nome_da_coluna FLOAT(10,2) NOT NULL;
AFTER nome_da_coluna_existente

ALTER TABLE nome_da_tabela                                 --Adiciona nova coluna na tabela na 1° posição
ADD nome_da_coluna FLOAT(10,2) NOT NULL;
FIRST;

ALTER TABLE nome_da_tabela                                 --Apaga coluna na tabela
DROP nome_da_coluna;
```

## Comandos para deletar itens da tabela:
```sql
DELETE                                                --Deleta uma linha inteira
FROM nome_da_tabela
WHERE nome_da_coluna <> 'String ou valor';
```

## Comandos para recuperação de itens da tabela:
```sql
SELECT *                                           --Mostra todas as colunas da tabela
FROM nome_da_tabela;                               --Nome da tabela que estamos consultando 

SELECT nome_da_coluna1, nome_da_coluna2            --Mostra as colunas na ordem que foram nomeadas da tabela
FROM nome_da_tabela;                               --Nome da tabela que estamos consultando 
```

## Operadores mátemáticos:
```sql
SELECT                                                             --Sintaxe
    nome_da_coluna1, 
    nome_da_coluna2, 
    (nome_da_coluna1 / nome_da_coluna2) AS nome_da_nova_coluna     --Cria a nova coluna e renomeia
FROM nome_da_tabela;
```
**Mais operadores matemáticos**
```sql
+ adição
- subtração
/ divisão
^ expoente
|/ raiz quadrada
@ valor absoluto
% resto
```

## Operadores de String e funções:
```sql
--Sintaxe
SELECT nome_da_coluna1 || ', ' || nome_da_coluna2 AS nova_coluna          
FROM nome_da_tabela; 

SELECT CONCAT(nome_da_Coluna1, ', ', nome_da_coluna2) AS nova_coluna
FROM nome_da_tabela

--É possível acumular várias funções
SELECT CONCAT(UPPER(nome_da_Coluna1, ', ', nome_da_coluna2 )) AS nova_coluna   
FROM nome_da_tabela

--Traz os registros nulos com o texto definido, as vezes é usado ******
SELECT IFNULL(nome_da_Coluna1, 'Dado não informado'),  
        nome_da_coluna2 AS nova_coluna  
FROM nome_da_tabela;
```
**Outros operadores:**
```sql
|| Une duas strings
CONCAT() Une duas strings
LOWER() Colaca as letras das strings em minúsculo
LENGHT() Traz o número de caracteres de uma string
UPPER() Colas as letras das strengs em maísculo
```

## Comandos de filtragem
```sql
SELECT nome_da_coluna1, nome_da_coluna2            --Sintaxe
FROM nome_da_tabela
WHERE nome_da_coluna > valor;

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna BETWEEN valor AND valor;

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna IN ('nome', 'nome');

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna NOT IN (5, 6) AND nome_da_coluna = 'String';

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna NOT IN (5, 6) OR nome_da_coluna = 'String';

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna LIKE 'XX%';

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna IS NULL;                     --Traz linhas sem dados (nulas)

SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
WHERE nome_da_coluna IS NOT NULL;     
```

## Operadores de comparação
```sql
= igual
> maior que
< menor que
>= maior e igual que
IN está em uma lista
<= menor ou igual
<> diferente
!= diferente
BETWEEN entre dois valores
NOT IN não está em uma lista
```

## Função de agregação
```sql
COUNT()                                 --Contar a quantidade de uma coluna, usar associada ao GROUP BY
GROUP BY nome_da_coluna                 --Agrupa os valores dentro de cada valor distinto 
```

## Operadores de agregação numérica EM COLUNAS
```sql
MAX()                                      --Traz o valor máximo de uma coluna
MIN()                                      --Traz o valor mínimo de uma coluna
AVG()                                      --Traz o valor médio de uma coluna
TRUNCANTE(parêmetro,n° de casas decimais)  --Trava um valor para o n° de casas especificado
SUM()                                      --Soma os valores de uma coluna, pode ser usada com o GROUP sem o COUNT

--Exemplos de sintaxe
SELECT MAX(nome_da_coluna) AS máximo,             
       MIN(nome_da_coluna) AS mínimo,
       TRUNCATE(AVG(nome_da_coluna),2)
FROM nome_da_tabela;

```

## Para agregação em linhas, utilize operações aritméticas
```sql
SELECT nome_da_coluna,            
       nome_da_coluna2,
       (nome_da_coluna + nome_da_coluna2) AS total
       TRUNCATE((nome_da_coluna + nome_da_coluna2)/2,2) AS DIVISÂO
FROM nome_da_tabela;
```

## Comandos de junção
```sql
--INNER = dentro, traz os dados que estiverem nas DUAS tabelas
SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
INNER JOIN nome_da_tabela2            
ON nome_da_FK = nome_da_FK2;

--Junção de 3 tabelas
SELECT nome_da_coluna1, nome_da_coluna2            
FROM nome_da_tabela
INNER JOIN nome_da_tabela2           
ON nome_da_FK = nome_da_FK2
INNER JOIN nome_da_tabela3            
ON nome_da_FK = nome_da_FK3;

--Junção de 3 tabelas com nomes de colunas coincidentes, pode-se renomear as tabelas conforme abaixo:
SELECT T.nome_da_coluna1, T1.nome_da_coluna2, T2.nome_da_coluna3            
FROM nome_da_tabela T
INNER JOIN nome_da_tabela2 T2          
ON nome_da_FK = nome_da_FK2
INNER JOIN nome_da_tabela3 T3            
ON nome_da_FK = nome_da_FK3;
```

## View
```sql
CREATE VIEW nome_da_view AS    --Cria uma tabela que fica disponível para consulta sempre que chamar pelo nome
SELECT sua_querry;

DROP VIEW nom_da_view;         --Apaga uma view

SELECT nome_da_coluna, nome da coluna1
FROM nome_da_view
```

## Comando de ordenação
```sql
SELECT nome_da_coluna
FROM nome_da_tabela
ORDER BY nome_da_coluna_ou_índice_da_coluna;

SELECT nome_da_coluna                        --Ordena de forma descendente
FROM nome_da_tabela
ORDER BY nome_da_coluna_ou_índice_da_coluna DESC;

SELECT nome_da_coluna                        --Ordena de forma ascendente
FROM nome_da_tabela
ORDER BY nome_da_coluna_ou_índice_da_coluna ASC;
```
### Programação no Banco de Dados MySQL
```sql
DELIMITER $                         --Primeiro é necessário mudar o delimitador

CREATE PROCEDURE nome_do_procedimento ()
BEGIN
  qualquer_programação;
END 
$

CREATE PROCEDURE conta()
BEGIN
  SELECT 10+10 AS conta;
END 
$

CREATE PROCEDURE conta(numero1 INT, numero2 INT)
BEGIN
  SELECT numero1 + numero2 AS conta;
END 
$

CALL conta(1,1);

CALL nome_da_procedure()$           --Chamando uma procedure

DROP PROCEDURE nome_da_procedure;   --Apaga uma procedure
```

## Subqueries
```sql
--Exemplos de sintaxe
SELECT nome_da_coluna, nome_da_coluna1
FROM nome_da_tabela
WHERE nome_da_coluna = (SELECT MIN(nome_da_coluna) FROM nome_da_tabela);

SELECT nome_da_coluna, nome_da_coluna1
FROM nome_da_tabela
WHERE nome_da_coluna > (SELECT AVG(nome_da_coluna) FROM nome_da_tabela);
```

## Trigger (gatilho)
```sql
CREATE TRIGGER nome_da_trigger                             --Primeiro é necessário mudar o delimitador
BEFORE/AFTER INSERT/DELETE/UPDATE ON nome_da_tabela
FOR EACH ROW                                               --ROW = linha
BEGIN 
  comando_sql
END
$

--Exemplos de triggers
CREATE TRIGGER backup_user                             --Primeiro é necessário mudar o delimitador
BEFORE DELETE ON nome_da_tabela
FOR EACH ROW
BEGIN 
  INSERT INTO bkp_usuario VALUES
    (NULL, OLD.idusuario, OLD.nome, OLD.login);
END
$

CREATE TRIGGER backup_product                            --Primeiro é necessário mudar o delimitador
BEFORE INSERT ON nome_da_tabela
FOR EACH ROW
BEGIN 
  INSERT INTO bkp_produto VALUES
    (NULL, NEW.idproduto, NEW.nome, NEW.preço);
END
$
```