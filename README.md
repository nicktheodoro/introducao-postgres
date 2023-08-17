# Banco de dados
Repositório destinado a documentar e exemplificar conceitos sobre banco de dados.

## Tipos de Dados no PostgreSQL

Aqui estão diversos tipos de dados oferecidos pelo PostgreSQL:

| Tipo          | Descrição                                                 |
|---------------|-----------------------------------------------------------|
| INTEGER       | Armazena números inteiros de precisão padrão. Adequado para a maioria dos casos de uso que envolvem valores inteiros. |
| BIGINT        | Armazena inteiros maiores, com uma faixa de valores muito maior do que o INTEGER. Útil quando se precisa de números inteiros muito grandes. |
| SMALLINT      | Armazena inteiros menores, ocupando menos espaço de armazenamento. Ideal quando a faixa de valores é pequena e o espaço é uma consideração importante. |
| NUMERIC/DECIMAL | Armazena números decimais de precisão arbitrária. É a escolha certa para valores que exigem exatidão decimal, como cálculos financeiros. |
| REAL          | Armazena números de ponto flutuante de precisão simples. Útil para aplicações onde a precisão é importante, mas a complexidade do DOUBLE PRECISION não é necessária. |
| DOUBLE PRECISION | Armazena números de ponto flutuante de precisão dupla. Apropriado para cálculos científicos e engenharia que exigem alta precisão. |
| SERIAL        | Um tipo de dados que automaticamente gera valores inteiros únicos crescentes, frequentemente usado para chaves primárias. |
| BIGSERIAL     | Similar ao SERIAL, mas armazena números inteiros maiores em um intervalo maior. Útil quando são necessários valores inteiros muito grandes. |
| CHAR(n)       | Armazena strings de tamanho fixo. Útil quando o tamanho das strings é previsível e constante. |
| VARCHAR(n)    | Armazena strings de tamanho variável. Adequado para strings com comprimento variável. |
| TEXT          | Armazena strings de tamanho variável mais longas. Usado quando se precisa de uma grande capacidade para armazenamento de texto. |
| DATE          | Armazena datas. Útil para registrar informações de data específicas. |
| TIME          | Armazena horários. Ideal para registros de tempo precisos. |
| TIMESTAMP     | Armazena data e hora. Combinação de DATE e TIME para registro completo. |
| INTERVAL      | Armazena intervalos de tempo. Útil para medições de tempo decorrido. |
| BOOLEAN       | Armazena valores verdadeiro ou falso. Usado para representar estados lógicos. |
| BYTEA         | Armazena dados binários, como imagens ou arquivos. |
| UUID          | Armazena identificadores únicos universais. |
| JSON          | Armazena dados JSON (formato de texto). Adequado para armazenar informações semi-estruturadas. |
| JSONB         | Armazena dados JSON binários (otimizados para busca). Oferece busca rápida em dados JSON. |
| INET          | Armazena endereços IP. Útil para armazenar informações de rede. |
| CIDR          | Armazena notação CIDR para redes. |
| POINT, LINE, LSEG, BOX | Armazenam dados geométricos. Úteis para aplicações que envolvem geolocalização e cálculos espaciais. |

## Tipos de Restrições no PostgreSQL

Aqui estão os tipos de restrições que podem ser aplicados em tabelas no PostgreSQL:

| Tipo de Restrição | Descrição                                                 |
|-------------------|-----------------------------------------------------------|
| PRIMARY KEY       | Garante que a coluna ou conjunto de colunas seja única e não nula, servindo como identificador único para cada registro na tabela. |
| FOREIGN KEY       | Cria uma relação entre a coluna ou conjunto de colunas em uma tabela (chave estrangeira) e a chave primária em outra tabela (chave primária correspondente). Mantém a integridade referencial entre tabelas. |
| UNIQUE            | Garante que os valores na coluna ou conjunto de colunas sejam únicos em toda a tabela. |
| NOT NULL          | Garante que a coluna não possa conter valores nulos, ou seja, deve sempre conter algum valor válido. |
| CHECK             | Define uma condição que os valores em uma coluna devem satisfazer. Usado para aplicar validações específicas aos dados. |
| EXCLUSION         | Restrição de exclusão mútua para tabelas particionadas, evitando conflitos entre os valores de várias tabelas. |

## Linguagens de Banco de Dados: DQL, DDL e DML

Linguagens fundamentais para interagir com bancos de dados: DQL (Data Query Language), DDL (Data Definition Language) e DML (Data Manipulation Language). Compreender essas linguagens é essencial para uma gestão eficaz de dados em sistemas de informação.

### DQL - Data Query Language

A DQL é usada para recuperar informações específicas armazenadas em um banco de dados. É usada principalmente para consultas complexas e seleção de dados com base em critérios específicos.

Exemplo: Selecionar os nomes dos clientes que fizeram compras nos últimos 30 dias.

```sql
SELECT nome
FROM Clientes
WHERE data_compra >= DATE_SUB(CURRENT_DATE, INTERVAL 30 DAY);
```

### DDL - Data Definition Language

A DDL é usada para criar, modificar e excluir objetos no banco de dados. Ela define a estrutura e a organização dos dados.

Exemplo: Criar uma tabela "Produtos" com colunas para ID do produto, nome e preço.

```sql
CREATE TABLE Produtos (
    id INT PRIMARY KEY,
    nome VARCHAR(50),
    preco DECIMAL(10, 2)
);
```

### DML - Data Manipulation Language

A DML é usada para manipular os dados armazenados no banco de dados. Ela permite inserir, atualizar e excluir registros.

Exemplo 1: Inserir um novo produto na tabela "Produtos".

```sql
INSERT INTO Produtos (id, nome, preco)
VALUES (1, 'Camiseta', 19.99);
```

Exemplo 2: Atualizar o preço de um produto específico.

```sql
UPDATE Produtos
SET preco = 24.99
WHERE id = 1;
```

Exemplo 3: Excluir um produto da tabela "Produtos".

```sql
DELETE FROM Produtos
WHERE id = 1;
```
