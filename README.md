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

## Índices em Banco de Dados: Conceito, Utilidade, Vantagens e Desvantagens

### O que é um Índice em Banco de Dados?
Um índice em um banco de dados é uma estrutura que melhora a eficiência das consultas realizadas sobre as tabelas. Ele funciona como um mecanismo de busca que permite ao banco de dados localizar rapidamente as linhas de dados correspondentes a determinados valores de colunas. Isso é especialmente útil em tabelas grandes, onde as consultas podem ser muito lentas se não houver índices.

### Para que serve um Índice?
Os índices servem para acelerar a recuperação de dados de uma tabela. Em vez de percorrer cada linha da tabela para encontrar os dados que correspondem a uma consulta, o banco de dados pode usar o índice para localizar rapidamente as linhas relevantes. Isso resulta em consultas mais rápidas e menor carga no sistema.

### Vantagens dos Índices:
1. *Melhoria no Desempenho:* As consultas que envolvem colunas indexadas são mais rápidas, já que o banco de dados pode pular diretamente para as linhas relevantes em vez de percorrer toda a tabela.
2. *Melhor Utilização de Recursos:* Com consultas mais eficientes, o banco de dados consome menos recursos, como CPU e memória.
3. *Suporte a Restrições Únicas:* Índices únicos podem ser usados para garantir que os valores em uma coluna sejam exclusivos, evitando duplicatas.
4. *Ordenação:* Índices podem ser usados para acelerar a ordenação dos resultados de uma consulta.
5. *Join mais Eficiente:* Em operações de junção, índices nas colunas de junção podem melhorar significativamente o desempenho.

### Desvantagens dos Índices:
1. *Consumo de Espaço:* Índices ocupam espaço adicional no disco, o que pode ser significativo em tabelas muito grandes.
2. *Custo de Manutenção:* À medida que os dados são inseridos, atualizados ou excluídos, os índices precisam ser atualizados para refletir essas mudanças, o que pode aumentar o tempo de escrita.
3. *Desempenho de Inserção/Atualização:* A inserção e atualização de dados podem ser mais lentas devido à necessidade de atualizar os índices.
4. *Índices Inadequados:* Criar índices desnecessários ou inapropriados pode levar a um pior desempenho em vez de melhorá-lo.

### Exemplo usando PostgreSQL:
Suponha que temos uma tabela chamada "produtos" com as colunas "id", "nome", "preço" e "categoria". Para melhorar a consulta de produtos por nome, criaríamos um índice na coluna "nome":

```Sql
CREATE INDEX idx_nome ON produtos (nome);
```

Isso permitirá que consultas como a seguinte sejam executadas de maneira mais eficiente:

```Sql
SELECT * FROM produtos WHERE nome = 'Camiseta';
```

Lembre-se de que a criação de índices deve ser cuidadosamente planejada, considerando as consultas mais frequentes e o equilíbrio entre o desempenho de leitura e escrita. Índices excessivos podem prejudicar o desempenho geral do banco de dados.


## **Views no PostgreSQL**  

### **O que é uma View?**  
Uma *view* no PostgreSQL é uma tabela virtual baseada em uma consulta SQL. Ela não armazena os dados fisicamente, mas exibe os resultados da consulta sempre que é acessada. Funciona como uma forma de simplificar consultas complexas, abstraindo a lógica dos dados e melhorando a organização da informação.  

### **Para que serve?**  
- Facilita o acesso a dados complexos, permitindo que usuários utilizem consultas pré-definidas.  
- Melhora a segurança ao restringir o acesso a certas colunas ou linhas.  
- Promove a reutilização de consultas sem necessidade de repetir código.  
- Auxilia na manutenção e na organização de sistemas com regras de negócios complexas.  

### **Vantagens das Views**  
:white_check_mark: **Simplicidade**: Reduz a complexidade de consultas SQL repetitivas.  
:white_check_mark: **Segurança**: Pode ocultar informações sensíveis restringindo o acesso a certos dados.  
:white_check_mark: **Modularidade**: Permite mudanças na estrutura do banco sem impactar diretamente os usuários.  
:white_check_mark: **Facilidade de manutenção**: Centraliza a lógica de consultas, tornando mais fácil modificar e corrigir regras de negócios.  

### **Desvantagens das Views**  
:x: **Desempenho**: Como não armazenam dados, consultas complexas podem ser mais lentas, pois são executadas toda vez que a *view* é chamada.  
:x: **Restrições de Atualização**: Algumas *views* não podem ser modificadas diretamente, especialmente se envolverem agregações ou *joins*.  
:x: **Dependência de Estrutura**: Alterações nas tabelas subjacentes podem invalidar a *view*, exigindo manutenção adicional.  

### **Exemplo Prático**  
Suponha que temos uma tabela de pedidos e queremos criar uma *view* para mostrar apenas os pedidos entregues:  

```sql
CREATE VIEW pedidos_entregues AS
SELECT id_pedido, cliente_id, data_pedido, valor_total
FROM pedidos
WHERE status = 'Entregue';
```

Agora, para acessar os pedidos entregues, basta utilizar:  

```sql
SELECT * FROM pedidos_entregues;
```

Isso simplifica o acesso aos dados sem precisar repetir a condição `WHERE status = 'Entregue'` em várias consultas.  

Caso queira excluir essa *view*, basta rodar:  

```sql
DROP VIEW pedidos_entregues;
```  
