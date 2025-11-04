CREATE DATABASE IF NOT EXISTS formula1;
USE formula1;

CREATE TABLE pais (
    id_pais INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL UNIQUE,
    sigla_iso CHAR(3) NOT NULL UNIQUE
);

CREATE TABLE equipe (
    id_equipe INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL UNIQUE,
    id_pais INT NOT NULL,
    FOREIGN KEY (id_pais) REFERENCES pais(id_pais)
);

CREATE TABLE piloto (
    id_piloto INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    data_nasc DATE NOT NULL,
    id_nacionalidade INT NOT NULL,
    id_equipe INT NOT NULL,
    fidelidade_desde YEAR NOT NULL,
    FOREIGN KEY (id_nacionalidade) REFERENCES pais(id_pais),
    FOREIGN KEY (id_equipe) REFERENCES equipe(id_equipe)
);

CREATE TABLE campeonato (
    id_campeonato INT AUTO_INCREMENT PRIMARY KEY,
    ano YEAR NOT NULL UNIQUE,
    nome VARCHAR(100) NOT NULL,
    status ENUM('Em andamento', 'Encerrado') DEFAULT 'Em andamento'
);

CREATE TABLE grande_premio (
    id_gp INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    data_gp DATE NOT NULL,
    id_pais INT NOT NULL,
    id_campeonato INT NOT NULL,
    FOREIGN KEY (id_pais) REFERENCES pais(id_pais),
    FOREIGN KEY (id_campeonato) REFERENCES campeonato(id_campeonato)
);

CREATE TABLE participacao (
    id_participacao INT AUTO_INCREMENT PRIMARY KEY,
    id_piloto INT NOT NULL,
    id_gp INT NOT NULL,
    posicao INT CHECK (posicao BETWEEN 1 AND 20),
    pontos INT DEFAULT 0,
    FOREIGN KEY (id_piloto) REFERENCES piloto(id_piloto),
    FOREIGN KEY (id_gp) REFERENCES grande_premio(id_gp)
);

INSERT INTO pais (nome, sigla_iso) VALUES
('Brasil', 'BRA'),
('Reino Unido', 'GBR'),
('Alemanha', 'DEU'),
('Espanha', 'ESP'),
('França', 'FRA'),
('Itália', 'ITA'),
('Japão', 'JPN'),
('Estados Unidos', 'USA'),
('Austrália', 'AUS'),
('México', 'MEX');

INSERT INTO equipe (nome, id_pais) VALUES
('Ferrari', 6),
('Mercedes', 3),
('Red Bull Racing', 2),
('McLaren', 2),
('Aston Martin', 2),
('Alpine', 5),
('AlphaTauri', 6),
('Williams', 2),
('Haas', 8),
('Sauber', 3);

INSERT INTO campeonato (ano, nome, status) VALUES
(2021, 'Campeonato Mundial de Fórmula 1 - 2021', 'Encerrado'),
(2022, 'Campeonato Mundial de Fórmula 1 - 2022', 'Encerrado'),
(2023, 'Campeonato Mundial de Fórmula 1 - 2023', 'Encerrado'),
(2024, 'Campeonato Mundial de Fórmula 1 - 2024', 'Em andamento'),
(2020, 'Campeonato Mundial de Fórmula 1 - 2020', 'Encerrado'),
(2019, 'Campeonato Mundial de Fórmula 1 - 2019', 'Encerrado'),
(2018, 'Campeonato Mundial de Fórmula 1 - 2018', 'Encerrado'),
(2017, 'Campeonato Mundial de Fórmula 1 - 2017', 'Encerrado'),
(2016, 'Campeonato Mundial de Fórmula 1 - 2016', 'Encerrado'),
(2015, 'Campeonato Mundial de Fórmula 1 - 2015', 'Encerrado');

INSERT INTO piloto (nome, data_nasc, id_nacionalidade, id_equipe, fidelidade_desde) VALUES
('Lewis Hamilton', '1985-01-07', 2, 2, 2013),
('Max Verstappen', '1997-09-30', 2, 3, 2016),
('Charles Leclerc', '1997-10-16', 6, 1, 2019),
('Fernando Alonso', '1981-07-29', 4, 5, 2023),
('Lando Norris', '1999-11-13', 2, 4, 2019),
('Sergio Pérez', '1990-01-26', 10, 3, 2021),
('George Russell', '1998-02-15', 2, 2, 2022),
('Carlos Sainz', '1994-09-01', 4, 1, 2021),
('Pierre Gasly', '1996-02-07', 5, 6, 2023),
('Yuki Tsunoda', '2000-05-11', 7, 7, 2021);

INSERT INTO grande_premio (nome, data_gp, id_pais, id_campeonato) VALUES
('GP do Bahrein', '2024-03-02', 1, 4),
('GP da Arábia Saudita', '2024-03-09', 1, 4),
('GP da Austrália', '2024-03-24', 9, 4),
('GP do Japão', '2024-04-07', 7, 4),
('GP da China', '2024-04-21', 3, 4),
('GP de Miami', '2024-05-05', 8, 4),
('GP da Espanha', '2024-06-23', 4, 4),
('GP da Grã-Bretanha', '2024-07-07', 2, 4),
('GP da Hungria', '2024-07-21', 3, 4),
('GP da Bélgica', '2024-07-28', 5, 4);

INSERT INTO participacao (id_piloto, id_gp, posicao, pontos) VALUES
(1, 1, 2, 18),
(2, 1, 1, 25),
(3, 1, 3, 15),
(4, 2, 4, 12),
(5, 2, 5, 10),
(6, 3, 1, 25),
(7, 3, 6, 8),
(8, 4, 2, 18),
(9, 4, 7, 6),
(10, 5, 8, 4);

DELETE FROM participacao WHERE id_participacao = 10;

UPDATE participacao SET posicao = 1, pontos = 25 WHERE id_participacao = 4;

SELECT nome, data_nasc FROM piloto ORDER BY data_nasc ASC;

SELECT nome, fidelidade_desde FROM piloto
WHERE fidelidade_desde BETWEEN 2019 AND 2022
AND id_equipe IN (1, 2, 3);

SELECT p.nome AS piloto, e.nome AS equipe
FROM piloto p
INNER JOIN equipe e ON p.id_equipe = e.id_equipe
WHERE e.nome LIKE '%Red%';

SELECT p.nome AS piloto, e.nome AS equipe
FROM piloto p
INNER JOIN equipe e ON p.id_equipe = e.id_equipe
WHERE e.nome NOT LIKE '%Red%';
