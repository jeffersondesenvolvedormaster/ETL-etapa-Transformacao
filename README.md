## ETL- Transformação
Demonstração de correções no Dataset 

<img width="993" height="570" alt="Imagem ETL" src="https://github.com/user-attachments/assets/263bd1c9-7eef-4cf5-a01d-0a991f8f7e89" />




Observando a planilha "Base Vendas.xlsx", identifiquei diversos problemas que violam boas práticas de modelagem tabular para Power BI:

1. Coluna com mesclagem fora do padrão de modelagem, espaços em branco e sem titulo.
   
2. Espaços em branco entre na coluna cidade devido a tabela secundária gerando sobreposição de dados

3. Falta de Normalização - Múltiplos Indicadores por Linha
Cada cidade tem múltiplas linhas com "Quantidade" e "Faturamento", mas essas informações não possuem uma coluna separada de "Tipo de Indicador" ou "Métrica". Isso dificulta a criação de relacionamentos.

4. Estrutura Desnormalizada
A tabela está em formato "matriz cruzada" (pivot table), com meses como colunas (Janeiro, Fevereiro, Março, etc.). Para Power BI, os dados devem estar em formato "tall and narrow", onde cada linha representa um registro único, com meses em uma coluna de dimensão separada.

5. Coluna desnecessária pois será gerada à partir da agregação dos valores das outras colunas em formula DAX gernado melhor performance nos dados.






