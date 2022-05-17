![walmart 2](https://user-images.githubusercontent.com/97288194/151464581-e98d27a2-1649-4f7e-8c45-df3e6ee02910.jpg)

# Walmart-Sales-Store

# 1.0 Contexto (Business)

O CFO do Walmart quer prever quanto cada loja venderá. Ele precisa saber se o orçamento será suficiente para fazer uma reforma em cada loja.

# 2.0 Desafio

Aqui estão os dados históricos de vendas de 45 lojas Walmart localizadas em diferentes regiões, cada loja contém muitos departamentos.
O CFO do Walmart pediu que você projetasse as vendas de cada departamento em cada loja.

# 3.0 Premissas do Negócio

stores.csv: Este arquivo contém informações anônimas sobre as 45 lojas, indicando o tipo e o tamanho da loja.

train.csv: Estes são os dados históricos de treinamento, que cobrem de 2010-02-05 a 2012-11-01. Dentro deste arquivo você encontrará os seguintes campos:

Store - O número da loja

Dept - O número do departamento

Date - A semana

Weekly_Sales -  Vendas para determinado departamento em determinada loja

IsHoliday - Se a semana é uma semana de feriado especial

test.csv

Este arquivo é idêntico ao train.csv, exceto que retemos as vendas semanais. Você deve prever as vendas para cada trio de loja, departamento e data neste arquivo.

features.csv: Este arquivo contém dados adicionais relacionados à loja, departamento e atividade regional para as datas especificadas. Ele contém os seguintes campos:

Store - O número da loja

Date - A semana

Temperature - Temperatura média da região

Fuel_Price - Custo do combustível na região

MarkDown1-5 - Dados anônimos relacionados a descontos promocionais que o Walmart está executando. Os dados MarkDown só estão disponíveis após novembro de 2011 e não estão disponíveis para todas as lojas o tempo todo. Qualquer valor ausente é marcado com um NA.

CPI - O índice de preços ao consumidor

Unemployment - a taxa de desemprego

IsHoliday - se a semana é uma semana de feriado especial

Por conveniência, os quatro feriados se enquadram nas semanas a seguir no conjunto de dados (nem todos os feriados estão nos dados):

Super Bowl: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13

Labor Day: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13

Thanksgiving: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13

Christmas: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13

# 4.0 Estratégia de Solução

A estratégia adotada foi a seguinte:

**Passo 01.** Descrição dos dados: Pesquisei os NAs, verifiquei os tipos de dados (e adaptei alguns deles para análise) e apresentei uma descrição estatística.

**Passo 02**. Engenharia de Variáveis: Novas funcionalidades foram criadas para possibilitar uma análise mais completa.

**Etapa 03.** Filtragem de Dados: As entradas que não continham informações ou que continham informações que não correspondiam ao escopo do projeto foram filtradas.

**Passo 04.** Análise Exploratória de Dados: Realizei análises de dados univariados, bivariados e multivariados, obtendo propriedades estatísticas de cada um deles, correlações e testando hipóteses (as mais importantes estão detalhadas na seção a seguir).

**Etapa 05:** Preparação de dados: Aqui optei por usar os recursos de redimensionamento com o método MinMaxScaler e apliquei OneHotEncoding para recursos de feriado e método LabelEncoder para tipo de recurso.

**Passo 06**. Seleção de recursos: Os recursos estatisticamente mais relevantes foram selecionados usando o pacote Boruta. Alternativamente, realizei a seleção de recursos usando o Random Forest como seletor de recursos, obtendo as "importâncias dos recursos" de ambos. Nas próximas etapas, os modelos de aprendizado de máquina treinados usando os recursos selecionados por Boruta apresentaram melhor desempenho de generalização.

**Passo 07**. Modelagem de aprendizado de máquina: alguns modelos de aprendizado de máquina foram treinados. O que apresentou melhores resultados após a validação cruzada passou por mais uma etapa de ajuste fino de hiperparâmetros para otimizar a generalização do modelo.

**Passo 08.** Model-to-business: O desempenho dos modelos é convertido em valores de negócios.

# 5.0 Conclusão

Usei o modelo Random Forest Regressor para aprender todo o comportamento dos dados e, após modelar os dados, usei-os para fazer previsões, usando 70% do conjunto de dados para treiná-lo e depois testá-lo em 30% dos dados não  visto pelo modelo para medir seu desempenho. Após todos os passos citados e com as previsões feitas, realizei a avaliação do desempenho do modelo, trazendo o resultado da previsão para cada loja Walmart, através de duas métricas: melhor e pior cenário. E MAE e MAPE: duas métricas de fácil entendimento para que a equipe de negócios possa utilizar os dados do modelo de forma mais prática no seu dia a dia. Trouxe também 4 gráficos que demonstram o resultado e erro do modelo para cada loja e por fim consegui gerar um resultado completo do modelo com uma previsão total de R$ 1.075.524,77 de receita.

# 6.0 Próximos passos e melhorias

* Aumentar a precisão do modelo em 8%.
* Implantar o modelo em produção, para que o tempo possa consumir os resultados do modelo por meio de um aplicativo da web (telegram).
