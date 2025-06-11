# challenge-by-coodesh
Projeto (Bike Stores Inc) Teste , linguagem usada PL/SQL.

Nesse desafio trabalharemos utilizando a base de dados da empresa Bike Stores Inc com o objetivo de obter métricas relevantes para equipe de Marketing e Comercial.

Com isso, teremos que trabalhar com várioas consultas utilizando conceitos como INNER JOIN, LEFT JOIN, RIGHT JOIN, GROUP BY e COUNT.

O projeto

- Criar as consultas utilizando a linguagem escolhida;
- Entregar o código gerado do Teste.
  
- Construir as seguintes consultas:

- Listar todos Clientes que não tenham realizado uma compra;
- Listar os Produtos que não tenham sido comprados
- Listar os Produtos sem Estoque;
- Agrupar a quantidade de vendas que uma determinada Marca por Loja. 
- Listar os Funcionarios que não estejam relacionados a um Pedido.

- Documentação e detalhes como deve concluí que deve ser feito:

1. CLIENTES SEM COMPRAS: Usa LEFT JOIN para identificar clientes sem correspondência na tabela de pedidos.
2. PRODUTOS NÃO ENCONTRADOS: Similar ao anterior, verifica produtos sem itens associados em pedidos.
3. PRODUTOS SEM ESTOQUE: Agrupa estoques por produto e filtra aqueles com quantidade total zero ou nula.
4. VENDAS POR MARCA/LOJA: Combina múltiplos JOIN para relacionar lojas, marcas e vendas, com agrupamento composto.
5. FUNCIONARIOS SEM PEDIDOS: Identifica funcionários sem associação com nenhum pedido registrado.
