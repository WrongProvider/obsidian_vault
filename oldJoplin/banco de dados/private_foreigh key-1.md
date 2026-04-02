private/foreigh key

.open "paises_simples.db"

.mode column

.header on

PRAGMA foreign_keys = ON; --habilita chaves estrangeiras no SQLite

\-\- script para criar a tabela Continente

CREATE TABLE Continente(id\_cont INTEGER PRIMARY KEY, nome\_cont VARCHAR(20));

\-\- script para criar a tabela Pais

CREATE TABLE Pais(sigla CHAR(2) PRIMARY KEY,

nome_pais VARCHAR(50) NOT NULL,

populacao INTEGER NOT NULL,

extensao REAL NOT NULL,

moeda VARCHAR(15),

id_cont INTEGER,

FOREIGN KEY (id\_cont) REFERENCES Continente(id\_cont));-- script para criar a tabela Cor

CREATE TABLE Cor(nome VARCHAR(15) PRIMARY KEY);

\-\- script para criar a tabela Bandeira_Cor

CREATE TABLE Bandeira\_Cor(sigla\_pais CHAR(2), nome_cor VARCHAR(15),

PRIMARY KEY (sigla\_pais, nome\_cor),

FOREIGN KEY (sigla_pais) REFERENCES Pais(sigla),

FOREIGN KEY (nome_cor) REFERENCES Cor(nome));

Inserindo dados

INSERT INTO Continente VALUES(1, 'América do Sul');

INSERT INTO Continente VALUES(2, 'América Central');

INSERT INTO Pais VALUES('BR', 'Brasil', 21426223, 8510345.540, 'Real', 1);

INSERT INTO Cor VALUES ('Amarelo'), ('Branco'), ('Vermelho'), ('Azul'), ('Preto'), ('Verde');

INSERT INTO Bandeira_Cor VALUES('BR', 'Verde');

INSERT INTO Bandeira_Cor VALUES('BR', 'Amarelo');

INSERT INTO Bandeira_Cor VALUES('BR', 'Azul');

INSERT INTO Bandeira_Cor VALUES('BR', 'Branco');

INSERT INTO Bandeira_Cor VALUES('AR', 'Azul'); -- vai dar erro de Foreign Key

INSERT INTO Bandeira_Cor VALUES('BR', 'Grená'); -- vai dar erro de Foreign Key