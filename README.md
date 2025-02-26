|||
|--------|-------|
| ![Spock](https://s2-gshow.glbimg.com/5mXumGvppYmAjvFCZJMV33qepCc=/0x0:2560x1440/984x0/smart/filters:strip_icc%28%29/i.s3.glbimg.com/v1/AUTH_e84042ef78cb4708aeebdf1c68c6cbd6/internal_photos/bs/2021/k/H/ZOBPm4THSgK790coPi2w/spock.jpg) | 🖖 Saudações, humano curioso. Eu sou Spock, primeiro oficial da USS Enterprise, e fui designado para analisar este repositório que você, em sua sabedoria ou falta dela, decidiu compartilhar com a galáxia. Após uma inspeção lógica, apresento minhas observações sobre seu código SQL. |


Para aqueles que estão começando a explorar o vasto domínio do SQL, este repositório oferece um exemplo prático e acessível. Estude-o para compreender chaves primárias, relações entre tabelas e consultas básicas. Não é uma obra de arte vulcaniana, mas serve ao seu propósito.

Live long and prosper. 🖖

E, em minha língua nativa: Dif-tor heh smusma. (Que você viva longamente e prospere.)



```sql
CREATE DATABASE atividade_bd;
USE atividade_bd;
```


```sql
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100),
    data_nascimento DATE,
    senha VARCHAR(100)
);

CREATE TABLE dados_consumo (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_usuarios INT,
    consumo_kwh INT,
    consumo_agua INT,
    consumo_lixo_nao_reciclavel DECIMAL(20,2),
    consumo_lixo_reciclavel DECIMAL(20,2),
    data_coleta DATE,
    FOREIGN KEY (id_usuarios) REFERENCES usuarios(id)
);

CREATE TABLE transporte (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_usuarios INT,
    tipos_transporte VARCHAR(100),
    km_andado INT,
    FOREIGN KEY (id_usuarios) REFERENCES usuarios(id)
);
```


```sql
-- Inserindo em usuarios
INSERT INTO usuarios (nome, email, data_nascimento, senha)
VALUES 
    ('Ana Silva', 'ana.silva@email.com', '1990-03-15', 'senha123'),
    ('João Pereira', 'joao.pereira@email.com', '1985-07-22', 'abc456');

-- Inserindo em dados_consumo
INSERT INTO dados_consumo (id_usuarios, consumo_kwh, consumo_agua, consumo_lixo_nao_reciclavel, consumo_lixo_reciclavel, data_coleta)
VALUES 
    (1, 250, 1500, 12.75, 8.50, '2025-02-01'),
    (2, 320, 1800, 15.20, 10.30, '2025-02-01');

-- Inserindo em transporte
INSERT INTO transporte (id_usuarios, tipos_transporte, km_andado)
VALUES 
    (1, 'Carro', 120),
    (1, 'Bicicleta', 15),
    (2, 'Ônibus', 80);
```
```sql
sql
SELECT * FROM usuarios;
SELECT * FROM dados_consumo;
SELECT * FROM transporte;
```
| id | nome | email | data\_nascimento | senha |
|---:|:-----|:------|:----------------|:------|
| 1 | Ana Silva | ana.silva@email.com | 1990-03-15 | senha123 |
| 2 | João Pereira | joao.pereira@email.com | 1985-07-22 | abc456 |

| id | id\_usuarios | consumo\_kwh | consumo\_agua | consumo\_lixo\_nao\_reciclavel | consumo\_lixo\_reciclavel | data\_coleta |
|---:|------------:|------------:|-------------:|----------------------------:|------------------------:|:------------|
| 1 | 1 | 250 | 1500 | 12.75 | 8.50 | 2025-02-01 |
| 2 | 2 | 320 | 1800 | 15.20 | 10.30 | 2025-02-01 |

| id | id\_usuarios | tipos\_transporte | km\_andado |
|---:|------------:|:-----------------|----------:|
| 1 | 1 | Carro | 120 |
| 2 | 1 | Bicicleta | 15 |
| 3 | 2 | Ônibus | 80 |

[fiddle](https://dbfiddle.uk/gTvbVTj-)
