# Database

Este repositório contém exemplos de código SQL que demonstram como criar, ler, atualizar e excluir dados em um banco de dados SQLite. Também são ilustrados o uso de chaves primárias e estrangeiras, tipos de dados e operações de *JOIN para int


## Tabela orders
```
CREATE table orders (
  id INT NOT NULL,
  order_number INT,
  customer_id INT,                                   
  product_id INT,
  PRIMARY key (id),
  FOREIGN KEY (customer_id) REFERENCES customer(id),
  FOREIGN KEY (product_id) REFERENCES products(id)
)
```

## Tabela products

```
CREATE TABLE products (
  id INT NOT NULL,
  name STRING,                 
  price MONEY,
  PRIMARY KEY (id)
  )
```


### Operações Básicas de SQL

### Inserir Dados
Inserção em products:
```
INSERT INTO products VALUES (1, "Pen", 1.20);
```

### Inserção específica de colunas:
```
INSERT INTO products (id, name) VALUES (1, "Pencil");
```

## Consultar Dados

### Selecionar todos os dados da tabela products:
```
SELECT * FROM 'products';
```

### Selecionar apenas o nome e o preço dos produtos:
```
SELECT name, price FROM 'products';
```

### Filtrar produtos com id igual a 1:
```
SELECT * FROM products WHERE id = 1;
```

## Atualizar Dados

### Atualizar o preço de um produto (onde id é 2):
```
UPDATE products SET price = 0.80 WHERE id = 2;
```

### Adicionar uma nova coluna à tabela products:

```
ALTER TABLE products ADD stock INT;
```

## Excluir Dados

### Excluir um produto com id igual a 2:
```
DELETE FROM products WHERE id = 2;
```

## Relacionamentos entre Tabelas

#### Chaves Primárias e Estrangeiras

#### Chave Primária: 
Usada para garantir a unicidade de uma coluna, como id na tabela products. PRIMARY KEY (id)

#### Chave Estrangeira: 
Usada para referenciar dados em outra tabela. No exemplo abaixo, a coluna customer_id da tabela orders faz referência ao id da tabela customer, e product_id faz referência ao id da tabela products.
FOREIGN KEY (customer_id) REFERENCES customer(id),
FOREIGN KEY (product_id) REFERENCES products(id)

## Uso de INNER JOIN
O INNER JOIN é utilizado para combinar dados de duas tabelas com base em uma coluna comum. No exemplo abaixo, unimos as tabelas orders e customer com base no customer_id para exibir informações detalhadas dos pedidos.

Exemplo de codigo 
```
SELECT orders.order_number, customer.first_name, customer.last_name, customer.address
FROM orders
INNER JOIN customer ON orders.customer_id = customer.id;
```

## Guia de SQL no W3Schools
- Editor SQLite Online: https://sqliteonline.com/
- Tipos de Dados no SQL: https://www.w3schools.com/sql/sql_datatypes.asp
- Chave Primária no SQL: https://www.w3schools.com/sql/sql_primarykey.asp
- Chave Estrangeira no SQL: https://www.w3schools.com/sql/sql_foreignkey.asp
- JOIN no SQL: https://www.w3schools.com/sql/sql_join_inner.asp
