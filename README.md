# Desafio 02 — Ciência de Dados
### Trilhas Inova III | Análise do consumo de energia elétrica em instituições públicas

**Integrantes:** Israel de Menezes, Wildney Luis Tavares Nunes Junior e Yan Souza Melo.

## 1. A base escolhida

A equipe escolheu a base de dados **Consumo de Energia de Órgãos Públicos Federais**, disponibilizada no portal de dados do Governo Federal.

- **Fonte:** [Base de consumo de energia](https://repositorio.dados.gov.br/seges/consumo-energia/consumo-energia.csv)
- **Data de acesso:** 25/11/2026

A escolha ocorreu pela possibilidade de analisar o consumo de energia elétrica em instituições públicas, comparar valores observados com uma referência histórica e identificar padrões de redução ou aumento ao longo dos meses. Os dados podem apoiar o acompanhamento do consumo e apontar situações que mereçam investigação.

## 2. As perguntas investigadas

1. Como o consumo agregado evoluiu entre setembro de 2021 e abril de 2022?

   Busca identificar o comportamento mensal do consumo e observar períodos de redução ou aumento em relação à referência histórica.

2. Quais instituições apresentaram maiores reduções e quais registraram aumento no consumo?

   A comparação ajuda a identificar instituições com resultados expressivos e casos que merecem investigação.

3. Entre as instituições com registros nos oito meses, o consumo observado foi menor que a referência histórica?

   A comparação com instituições presentes em todos os meses reduz o efeito das diferenças na quantidade de registros mensais.

## 3. Preparação dos dados

A base foi carregada e analisada com Python e Pandas. Foram verificadas dimensões, tipos de dados, valores ausentes, duplicatas, zeros nas colunas de consumo e registros repetidos por instituição e mês. Os meses foram padronizados para facilitar a análise temporal.

A base contém **803 registros e 8 colunas**. Há valores ausentes nas colunas textuais `justificativa_meta` (715) e `observacao` (453); eles foram mantidos, pois não impedem os cálculos numéricos. Foram encontrados cinco registros com zero em pelo menos uma coluna de consumo, tratados como pontos de investigação, não como erros automáticos.

Não foram encontradas linhas totalmente duplicadas nem siglas de instituições repetidas no mesmo mês. A base reúne **130 siglas distintas de instituições**.

## 4. Análise

### Pergunta 1 — Evolução mensal

Foram comparadas as somas do consumo de referência e do consumo observado em cada mês. O consumo observado ficou abaixo da referência na maioria dos meses, mas março de 2022 apresentou aumento.

A redução agregada de todos os registros foi de aproximadamente **21,18%**. Como a quantidade de instituições varia por mês, essa comparação é descritiva e deve ser interpretada com cautela.

### Pergunta 2 — Comparação por instituição

Os registros foram agrupados por sigla, comparando o total de referência com o consumo observado. Foram identificadas instituições com reduções expressivas e outras com aumento.

IFB e IBRAM aparecem entre casos com reduções elevadas; IFES, FUNASA e FIOCRUZ aparecem entre casos com aumento no consumo observado. Os rankings são exploratórios e podem ser influenciados por meses faltantes e valores extremos.

### Pergunta 3 — Instituições com registros completos

Foram selecionadas **61 instituições presentes nos oito meses**, totalizando 488 registros. Nesse grupo, a redução agregada foi de aproximadamente **24,45%**, oferecendo uma comparação mais consistente do que a base completa.

## 5. Estatística e visualizações

Foram produzidos gráficos da evolução mensal da redução em relação à referência, quantidade de registros por mês, comparação de instituições e distribuição das diferenças entre referência e consumo observado no grupo completo.

As visualizações mostram que as reduções predominam, mas o comportamento varia entre meses e instituições.

Março de 2022 se destacou por apresentar aumento agregado em relação à referência. A quantidade de registros também varia entre meses, o que reforça a necessidade de cautela na interpretação das comparações.

## 6. Teste de hipótese

**Objetivo:** verificar se, entre as 61 instituições com registros completos, o consumo observado médio por instituição foi menor que a referência histórica.

- **H₀ (hipótese nula):** a média de referência é igual à média do consumo observado (diferença média = 0).
- **H₁ (hipótese alternativa):** a referência média é maior que o consumo observado (diferença média > 0).
- **Nível de significância:** α = 0,05.
- **Teste:** t pareado unilateral, usando a instituição como unidade de análise.

| Indicador | Resultado |
|---|---:|
| Instituições no teste | 61 |
| Diferença média (referência − consumo) | 240.090,01 |
| Estatística t | 3,2829 |
| Valor-p (t pareado, unilateral) | 0,000858081 |
| Valor-p (Wilcoxon, complementar) | 0,00000000189087 |

Como o valor-p do teste t foi inferior a 0,05, rejeita-se H₀. Há evidência estatística de que, no grupo analisado, o consumo observado médio foi menor que a referência. Isso não significa que todas as instituições reduziram o consumo nem demonstra que uma política específica causou a redução.

O teste de Wilcoxon foi aplicado como análise complementar e também apresentou resultado estatisticamente significativo.

## 7. Conclusões

A análise mostrou consumo observado abaixo da referência histórica na maioria dos meses. A redução agregada foi de aproximadamente **21,18% na base completa** e de **24,45% no grupo de 61 instituições com registros em todos os meses**.

O teste de hipótese indicou evidência estatística de consumo médio inferior à referência nesse grupo.

Também foram identificados períodos e instituições com aumento de consumo, o que demonstra que os resultados não foram uniformes. Recomenda-se investigar registros com aumentos expressivos, validar dados e avaliar possíveis oportunidades de melhoria na gestão energética.

Os resultados não permitem afirmar causalidade.

## 8. Reflexão

Python facilitou a organização, limpeza, agrupamento e comparação dos dados. Em relação a uma planilha, permitiu automatizar cálculos, analisar centenas de registros, criar visualizações e aplicar testes estatísticos de maneira mais eficiente e reprodutível.

### Divisão de responsabilidades

- **Yan Souza Melo:** análise de dados e desenvolvimento do notebook Python.
- **Israel de Menezes:** organização da pasta do projeto e dos dados no repositório.
- **Wildney Luis Tavares Nunes Junior:** elaboração do README e documentação.

O desafio contribuiu para praticar análise exploratória de dados, organização de projetos, colaboração em equipe e interpretação de resultados estatísticos.

## Tecnologias utilizadas

Python • Pandas • NumPy • Matplotlib • SciPy • Google Colab • GitHub

---

*Projeto desenvolvido como atividade do Desafio 02 — Ciência de Dados, Trilhas Inova III.*
