Anotações de Banco de Dados SQL

Projeto de estudo com anotações e prática de banco de dados relacional com SQL. O banco de exemplo se chama estudoprova e simula um sistema simples de locadora de filmes, com clientes, funcionários, filmes e aluguéis.

Sobre o projeto
Exercícios e anotações para fixar os fundamentos de SQL e modelagem relacional
Dump completo do banco (estrutura + dados) para importar e praticar consultas
Tema: locadora de filmes (clientes alugam filmes do catálogo)
Tecnologias
Item	Versão
SGBD	MariaDB 10.4.32
Ferramenta de administração	phpMyAdmin 5.2.1
PHP (do phpMyAdmin)	8.2.12
Engine das tabelas	InnoDB
Charset	utf8mb4 (filmes usa utf8)

O dump foi gerado em 06/06/2025 (host 127.0.0.1).

Estrutura do banco
cliente

Cadastro dos clientes da locadora.

Coluna	Tipo	Observação
cpf	bigint(14)	Chave primária
nome	varchar(45)	
email	varchar(45)	
endereco	text	
telefone	bigint(20)	NOT NULL
funcioanario

Cadastro dos funcionários.

Coluna	Tipo	Observação
idFuncionario	int(11)	Chave primária, AUTO_INCREMENT
cpf	bigint(14)	
nome	text	
email	text	
dataNascimento	date	

O nome da tabela está escrito funcioanario (com as letras trocadas) no banco original. Foi mantido assim para o dump continuar funcionando.

filmes

Catálogo de filmes, com dados no estilo de um ranking de filmes.

Coluna	Tipo	Observação
id	int(11)	Chave primária
Titulo	text	Inclui a posição no ranking e o ano
Certificado	varchar(45)	Classificação (R, PG-13, etc.)
Duracao	varchar(45)	Ex.: 142 min
Genero	text	
Avaliacao	float	Nota do filme
Pontuacao	int(11)	
Descricao	text	Sinopse
Elenco	text	Direção e atores
Informacoes	text	Votos e bilheteria
aluguel

Registra qual cliente alugou qual filme.

Coluna	Tipo	Observação
comprovanteAluguel	int(11)	Chave primária
idFilmesFK	int(11)	Chave estrangeira → filmes.id
cpf	bigint(14)	Chave estrangeira → cliente.cpf
Relacionamentos
cliente (1) ──────< aluguel >────── (1) filmes
   cpf                 cpf | idFilmesFK               id
Um cliente pode ter vários aluguéis
Um filme pode aparecer em vários aluguéis
aluguel é a tabela que liga cliente e filmes
Conceitos praticados
Criação de tabelas com CREATE TABLE
Tipos de dados (int, bigint, varchar, text, float, date)
Inserção de dados com INSERT INTO
Chave primária (PRIMARY KEY) e AUTO_INCREMENT
Chave estrangeira (FOREIGN KEY) e integridade referencial
Índices (KEY) e alteração de tabelas com ALTER TABLE
Transações (START TRANSACTION / COMMIT)
Valores NULL e NOT NULL
Como usar
Instale o XAMPP (ou outro ambiente com MariaDB/MySQL e phpMyAdmin)
Inicie o Apache e o MySQL/MariaDB
Abra o phpMyAdmin e crie o banco estudoprova
Selecione o banco, vá em Importar e escolha o arquivo .sql do dump
Execute as consultas e pratique
Dados do banco
Tabela	Registros
cliente	5
funcioanario	5
filmes	1000 (ids de 0 a 999)
aluguel	0 (vazia)
Pontos de atenção
A tabela filmes tem linhas repetidas: a partir do id 398, os filmes das posições 301 a 400 se repetem várias vezes
Todos os clientes estão com telefone igual a 0
A tabela aluguel ainda não tem dados cadastrados
O nome da tabela funcioanario está com erro de digitação
Próximos passos
[ ] Inserir registros na tabela aluguel
[ ] Remover os filmes duplicados
[ ] Corrigir o nome da tabela funcioanario
[ ] Praticar consultas com SELECT, WHERE, ORDER BY e JOIN
[ ] Praticar funções de agregação (COUNT, AVG, GROUP BY)
Autor

Projeto de estudo pessoal sobre banco de dados SQL.
