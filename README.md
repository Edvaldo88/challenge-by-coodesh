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


--- Clientes sem compras

SELECT c.customer_id, c.first_name, c.last_name
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

--- Produtos não comprados

SELECT p.product_id, p.product_name
FROM products p
LEFT JOIN order_items oi ON p.product_id = oi.product_id
WHERE oi.item_id IS NULL;

--- Produtos sem estoque

SELECT p.product_id, p.product_name
FROM products p
LEFT JOIN stocks s ON p.product_id = s.product_id
GROUP BY p.product_id, p.product_name
HAVING COALESCE(SUM(s.quantity), 0) = 0;

--- Vendas por Marca e Loja

SELECT 
    st.store_name,
    b.brand_name,
    SUM(oi.quantity) AS total_vendas
FROM orders o
INNER JOIN order_items oi ON o.order_id = oi.order_id
INNER JOIN products p ON oi.product_id = p.product_id
INNER JOIN brands b ON p.brand_id = b.brand_id
INNER JOIN stores st ON o.store_id = st.store_id
GROUP BY st.store_name, b.brand_name
ORDER BY st.store_name, b.brand_name;

--- Funcionários sem pedidos associados

SELECT s.staff_id, s.first_name, s.last_name
FROM staffs s
LEFT JOIN orders o ON s.staff_id = o.staff_id
WHERE o.order_id IS NULL;
