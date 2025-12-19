## ETL- Transformação
Demonstração de correções no Dataset 

<img width="1360" height="768" alt="Transformação ETL" src="https://github.com/user-attachments/assets/9aa1d948-9746-4655-84f2-955547e30ad7" />

### Análise de Boas Práticas de Modelagem para Power BI
Observando a planilha "Base Vendas.xlsx", identifiquei diversos problemas que violam boas práticas de modelagem tabular para Power BI:

1. Estrutura Desnormalizada
A tabela está em formato "matriz cruzada" (pivot table), com meses como colunas (Janeiro, Fevereiro, Março, etc.). Para Power BI, os dados devem estar em formato "tall and narrow", onde cada linha representa um registro único, com meses em uma coluna de dimensão separada.

3. Dados Duplicados e Mistos
Há dados de dois períodos (2022 e outro período) misturados na mesma tabela. Os dados estão intercalados verticalmente (linhas 1-21 para 2022 e linhas 23-31 para outro período), o que prejudica a integridade.

5. Falta de Normalização - Múltiplos Indicadores por Linha
Cada cidade tem múltiplas linhas com "Quantidade" e "Faturamento", mas essas informações não possuem uma coluna separada de "Tipo de Indicador" ou "Métrica". Isso dificulta a criação de relacionamentos.

7. Coluna "A" Sem Significado Claro
A coluna A contém valores como "s" e números de ano (2022), não sendo clara sua função ou semanticamente significativa.
