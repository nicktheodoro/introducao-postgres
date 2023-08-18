### Estudo de Caso: Controle de Produtos e Estoque

Você foi contratado para criar um sistema de controle de produtos e estoque para uma loja. Aqui estão as tabelas que você precisa criar:

#### Tabela: Categoria
| Atributo     | Tipo de Dado | Restrições    |
|--------------|--------------|---------------|
| id           | SERIAL       | PRIMARY KEY   |
| nome         | VARCHAR(50)  | NOT NULL      |

#### Tabela: Produto
| Atributo     | Tipo de Dado | Restrições    |
|--------------|--------------|---------------|
| id           | SERIAL       | PRIMARY KEY   |
| nome         | VARCHAR(100) | NOT NULL      |
| preco        | NUMERIC      | NOT NULL      |
| categoria_id | INTEGER      | FOREIGN KEY (Categoria) |

#### Tabela: Estoque
| Atributo     | Tipo de Dado | Restrições    |
|--------------|--------------|---------------|
| id           | SERIAL       | PRIMARY KEY   |
| produto_id   | INTEGER      | FOREIGN KEY (Produto) |
| quantidade   | INTEGER      | NOT NULL      |

Agora, aqui estão os desafios e bônus para esse estudo de caso:

#### Desafio 1: Inserir Dados

Preencha as tabelas de Categoria, Produto e Estoque com alguns dados fictícios, garantindo que as restrições sejam respeitadas.

#### Desafio 2: Consulta de Produtos

Escreva uma consulta para exibir o nome, preço e categoria de todos os produtos.

#### Desafio 3: Atualização de Preço

Atualize o preço de um produto específico na tabela de Produtos.

#### Desafio 4: Contagem de Categorias

Calcule quantas categorias diferentes existem na tabela Categoria.

#### Desafio 5: Estoque Total

Calcule a quantidade total de produtos em estoque.

#### Desafio 6 (Bônus): Produtos Esgotados

Liste os produtos que estão completamente esgotados (quantidade em estoque igual a zero).

#### Desafio 7 (Bônus): Preço Médio por Categoria

Calcule o preço médio dos produtos para cada categoria.

#### Desafio 8 (Bônus): Produtos em Estoque Baixo

Liste os produtos que têm uma quantidade em estoque menor do que um valor específico.

#### Desafio 9 (Bônus): Produtos por Categoria

Exiba o nome da categoria e a quantidade de produtos nela para cada categoria existente.

#### Desafio 10 (Bônus): Detalhes do Estoque

Crie uma consulta que mostre o nome do produto, a quantidade em estoque e o nome da categoria para todos os produtos.

Esses desafios e bônus abrangem uma variedade de operações, consultas e funções de agregação, permitindo que você pratique várias habilidades ao criar consultas SQL eficientes.