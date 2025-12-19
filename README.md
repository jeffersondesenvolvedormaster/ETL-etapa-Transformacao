## ETL- Transformação
### Análise Comparativa: Transformações Aplicadas (Antes vs. Depois)

## Antes:
<img width="993" height="570" alt="Imagem ETL" src="https://github.com/user-attachments/assets/263bd1c9-7eef-4cf5-a01d-0a991f8f7e89" />




### Observando a planilha "Base Vendas.xlsx", identifiquei diversos problemas que violam boas práticas de modelagem tabular para Power BI:

1. Coluna com mesclagem fora do padrão de modelagem, espaços em branco e sem titulo.
   
2. Espaços em branco entre na coluna cidade devido a tabela secundária gerando sobreposição de dados

3. Falta de Normalização - Múltiplos Indicadores por Linha
Cada cidade tem múltiplas linhas com "Quantidade" e "Faturamento", mas essas informações não possuem uma coluna separada de "Tipo de Indicador" ou "Métrica". Isso dificulta a criação de relacionamentos.

4. Estrutura Desnormalizada
A tabela está em formato "matriz cruzada" (pivot table), com meses como colunas (Janeiro, Fevereiro, Março, etc.). Para Power BI, os dados devem estar em formato "tall and narrow", onde cada linha representa um registro único, com meses em uma coluna de dimensão separada.

5. 'Coluna' desnecessária pois será gerada à partir da agregação dos valores das outras colunas em formula DAX gernado melhor performance nos dados.

   ## Transformação realizada no Power Query:
 ## Depois:  
<img width="1360" height="768" alt="Transformações realizadas ETL" src="https://github.com/user-attachments/assets/0394a456-9144-41c6-b1ff-01191239bb42" />


## Transformação realizada no Power Query, Feito as seguintes mudanças:

1. Despivotamento de Colunas (Unpivot) ✓
Antes: Meses como colunas (Janeiro, Fevereiro, Março, Abril, Maio, Junho, Julho, Agosto, Setembro, Outubro, Novembro, Dezembro)
Depois: Coluna única "Mês" com valores em linhas (Janeiro, Fevereiro, Março, etc.)
Obs. Esta é a transformação mais importante realizada.

2. Formato Tall and Narrow Implementado ✓
Antes: Estrutura larga com ~13 colunas de dados (1 por mês)
Depois: Estrutura estreita com apenas 6 colunas: Data, Mês, Ano, Cidade, Quantidade, Faturamento
A tabela agora segue o padrão recomendado para Power BI.

3. Coluna de Data Criada ✓
Antes: Não existia coluna de data explícita
Depois: Coluna "Data" criada (formato: 01/04/2022, 01/08/2022, etc.) -  combinando ano e mês para geração de ID data.

4. Coluna "Ano" Explicitada ✓
Antes: Ano misturado com os dados ou em coluna sem contexto
Depois: Coluna "Ano" dedicada com valor "2022"

5. Eliminação de Dados Duplicados/Mistos ✓
Antes: Dois períodos de dados misturados (2022 e outro período)
Depois: Dados consolidados em uma única estrutura coerente

6. Remoção de Colunas Irrelevantes ✓
Antes: Coluna "A" com valores sem significado ("s", "2022")
Depois: Coluna removida - não aparece mais

7. Consolidação de "Indicador" ✓
Antes: Linhas alternadas entre "Quantidade" e "Faturamento" em coluna "Indicador"
Depois: Convertidas em colunas separadas "Quantidade" e "Faturamento"

8. Aumento de Linhas (Normalização)
Antes: ~31 linhas (com estrutura de pivot)
Depois: 360 linhas (conforme mostrado: "6 COLUNAS, 360 LINHAS")
Isto é esperado quando se despivotar - cada combinação de cidade/mês/ano vira uma linha.

### Etapas de Transformação Aplicadas (visíveis no painel direito)

✓ Fonte

✓ Navegação

✓ Cabeçalho - Navegação (primeira linha como cabeçalho)

✓ Tipo Alterado

✓ Colunas Removidas

✓ Linhas em Branco Removidas

✓ Linhas Filtradas

✓ Somente as Colunas Selecionadas

✓ Coluna em Pivô

✓ Colunas Renomeadas

✓ Colunas Reordenadas

## Resultado Final

A tabela agora está muito mais adequada para modelagem em Power BI, com:

✓ Estrutura normalizada

✓ Uma linha por fato (uma venda por cidade/data)

✓ Sem dados pivotados

✓ Pronta para relacionamentos com dimensões

✓ Melhor desempenho de consultas

As transformações seguem exatamente as recomendações de boas práticas!




