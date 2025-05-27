# Banco-de-dados-ATV-05
Crie o modelo conceitual, lógico e físico.  Insira todos os arquivos (inclusive as imagens dos modelos) utilizados na atividade no repositório do github. 

create database eleicao;
use eleicao;


CREATE TABLE Localidade (
    id_localidade INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);


CREATE TABLE Zona_Eleitoral (
    id_zona INT PRIMARY KEY AUTO_INCREMENT,
    id_localidade INT NOT NULL,
    numero INT NOT NULL,
    FOREIGN KEY (id_localidade) REFERENCES Localidade(id_localidade)
);


CREATE TABLE Secao_Eleitoral (
    id_secao INT PRIMARY KEY AUTO_INCREMENT,
    id_zona INT NOT NULL,
    numero INT NOT NULL,
    FOREIGN KEY (id_zona) REFERENCES Zona_Eleitoral(id_zona)
);


CREATE TABLE Eleitor (
    id_eleitor INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    titulo_eleitoral VARCHAR(20) UNIQUE NOT NULL,
    id_secao INT NOT NULL,
    FOREIGN KEY (id_secao) REFERENCES Secao_Eleitoral(id_secao)
);


CREATE TABLE Partido_Politico (
    id_partido INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    sigla VARCHAR(10) UNIQUE NOT NULL
);


CREATE TABLE Candidato (
    id_candidato INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    cargo VARCHAR(50) NOT NULL,
    id_partido INT NOT NULL,
    FOREIGN KEY (id_partido) REFERENCES Partido_Politico(id_partido)
);


CREATE TABLE Voto (
    id_voto INT PRIMARY KEY AUTO_INCREMENT,
    id_candidato INT NOT NULL,
    FOREIGN KEY (id_candidato) REFERENCES Candidato(id_candidato)
);
