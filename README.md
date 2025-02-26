``` 
CREATE DATABASE atividade_bd;
USE atividade_bd;
```


``` 
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



``` 
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

> ``` status
> Records: 2  Duplicates: 0  Warnings: 0
> ```


> ``` status
> Records: 2  Duplicates: 0  Warnings: 0
> ```


> ``` status
> Records: 3  Duplicates: 0  Warnings: 0
> ```

``` 
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
