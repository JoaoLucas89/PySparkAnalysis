 Análise do Perfil e Comportamento de Passageiros em Aeroportos

Projeto de análise de dados com **Apache Spark (PySpark)** utilizando **Databricks**, baseado em uma pesquisa com passageiros do aeroporto de **San Francisco (SFO)**. O objetivo é extrair insights relevantes sobre o comportamento, perfil e percepção de usuários quanto à experiência no aeroporto.

---

## Objetivos

- Explorar e entender o comportamento de passageiros
- Cruzar variáveis demográficas com hábitos de viagem e percepções
- Visualizar os dados com gráficos interativos no Databricks
- Criar uma estrutura de projeto clara, replicável e de valor analítico

---

## Tecnologias Utilizadas

- Apache Spark (PySpark)
- Databricks Community Edition
- Python 3.x
- Visualizações do Databricks
- GitHub (para versionamento)

---

## Fonte de Dados

Utilizado o dataset público da Databricks:

/databricks-datasets/learning-spark-v2/sf-airbnb/survey_results.csv

## Pré-processamento

- Conversão de colunas categóricas para nomes legíveis (`region_name`, `sexo`, `renda`, `hiflyer`)
- Padronização de valores nulos
- Conversão de variáveis para tipos apropriados (idade, notas, voos, etc.)

---

## Análises Realizadas

### Perfil Demográfico
- Distribuição por sexo (`Masculino`, `Feminino`)
- Distribuição por faixa de renda
- Idade média dos passageiros por região

### ✈Hábitos de Viagem
- Média de voos por ano por faixa de renda e sexo
- Uso de aplicativos, redes sociais e Wi-Fi por faixa etária

### Percepções dos Passageiros
- Avaliação da segurança percebida por região (com percentuais)
- Avaliação da limpeza geral por faixa de renda
- Criação de **índice de satisfação geral**, combinando limpeza, segurança, sinalização e lojas

### Cidades com Mais Passageiros

```python
top_cidades = df.groupBy("Q17_CITY") \
    .count() \
    .orderBy("count", ascending=False) \
    .limit(10)

display(top_cidades)

### Visualizações Criadas

Gráfico de barras: top 10 cidades de origem dos passageiros

Gráficos de pizza: distribuição por sexo, por hiflyer

Gráfico de colunas: média de voos por região

Gráfico de linha: uso de apps por idade

Todos criados no Databricks com a função display(df) e exportados como imagem.
