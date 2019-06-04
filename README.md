# ExerciciosJoin


1- Crie a tabela Empresa, com as variáveis: id_empresa, CNPJ e nome_empresa.
Após isso crie a tabela Funcionarios, com as variáveis: id_funcionario, nome_funcionario,
data_admissao e id_empresa.
Insira pelo menos três empresas na tabela Empresa, e 6 funcionários na tabela funcionários
sendo que cada empresa deve ter dois funcionários.
Selecione o nome da empresa e de seus respectivos funcionários utilizando INNER JOIN.


2- Utilizando FULL JOIN na tabela do exercício anterior, selecione todos os registros
da tabela Empresa e da tabela Funcionários.


3- Explique quando usar cada um dos quatro tipos de JOIN (INNER JOIN, FULL
JOIN, LEFT JOIN e RIGHT JOIN).


#-- EXERCICIO 1

CREATE TABLE EMPRESA (
 ID_EMPRESA INT,
 CNPJ VARCHAR(255),
 NOME_EMPRESA VARCHAR(255),
 PRIMARY KEY (ID_EMPRESA)
);

CREATE TABLE FUNCIONARIOS (
  ID_FUNCIONARIOS INT,
  NOME_FUNCIONARIO VARCHAR(255),
  DATA_ADMISSAO DATETIME,
  ID_EMPRESA INT,
  PRIMARY KEY (ID_FUNCIONARIOS),
  FOREIGN KEY (ID_EMPRESA) REFERENCES EMPRESA(ID_EMPRESA)
);

INSERT INTO EMPRESA VALUES(1, '12345678925', 'UNA');
INSERT INTO EMPRESA VALUES(2, '12345678925', 'SINQIA');
INSERT INTO EMPRESA VALUES(3, '12345678925', 'ANIMA');

INSERT INTO FUNCIONARIOS VALUES (1, 'PEDRO', GETDATE(), 1);
INSERT INTO FUNCIONARIOS VALUES (2, 'MARIA', GETDATE(), 1);
INSERT INTO FUNCIONARIOS VALUES (3, 'JULIA', GETDATE(), 2);
INSERT INTO FUNCIONARIOS VALUES (4, 'FLAVIA', GETDATE(), 2);
INSERT INTO FUNCIONARIOS VALUES (5, 'SHEILA', GETDATE(), 3);
INSERT INTO FUNCIONARIOS VALUES (6, 'TIAGO', GETDATE(), 3);

SELECT EMPRESA.NOME_EMPRESA, FUNCIONARIOS.NOME_FUNCIONARIO FROM EMPRESA
INNER JOIN FUNCIONARIOS
ON EMPRESA.ID_EMPRESA = FUNCIONARIOS.ID_EMPRESA


#-- EXERCICIO 2

SELECT * FROM EMPRESA
FULL JOIN FUNCIONARIOS
ON FUNCIONARIOS.ID_EMPRESA = EMPRESA.ID_EMPRESA


#-- EXERCICIO 3

INNER JOIN: A cláusula INNER JOIN permite usar um operador de comparação para comparar os valores de colunas provenientes 
de tabelas associadas. Por meio desta cláusula, os registros de duas tabelas são usados para que sejam gerados os dados relacionados de ambas.
Deve-se usar a cláusula INNER JOIN para obtermos os dados relacionados das duas tabelas

RIGHT JOIN: A cláusula LEFT JOIN ou LEFT OUTER JOIN permite obter não apenas os dados relacionados de duas tabelas, 
mas também os dados não relacionados encontrados na tabela à esquerda da cláusula JOIN
Deve-se usar quando se quer obter não apenas os dados relcionados de duas tabelas,
mas tambem os dados não relacionados encontrados na tabela à esquerda da clasula JOIN.

RIGHT JOIN: A cláusula RIGHT JOIN ou RIGHT OUTER JOIN permite obter não apenas os dados relacionados de duas tabelas, 
mas também os dados não relacionados encontrados na tabela à direita da cláusula JOIN
Deve-se usar quando se quer obter não apenas os dados relacionados de duas tabelas,
mas tambem os dados não relacionados encontrados na tabela à direita da clasula JOIN.

FULL JOIN: O Outer Join (também conhecido por Full Outer Join ou Full Join), tem como resultado
todos os registros que estão na tabela A e todos os registros da tabela B.
Deve-se usar quando se quer um JOIN COMPLETO, ou seja, todos os dados das duas tabelas.
