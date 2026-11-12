# iFood Case

## Contexto

Considere uma empresa consolidada no setor de varejo de alimentos, com uma base de centenas de milhares de clientes e atuação por diferentes canais de venda.

A empresa comercializa produtos de diferentes categorias e utiliza campanhas de marketing para estimular novas compras.

Nos últimos anos, a companhia apresentou resultados financeiros saudáveis, mas as perspectivas de crescimento de lucro para os próximos anos são mais desafiadoras. Por isso, uma das prioridades é melhorar a eficiência das campanhas de marketing por meio de uma abordagem mais orientada por dados.

## O desafio

Uma nova campanha será realizada no próximo mês para oferecer um novo produto à base de clientes.

Para apoiar essa decisão, foi realizada uma campanha piloto com **2.240 clientes selecionados aleatoriamente**. Cada cliente teve um custo de contato e, posteriormente, foi identificado se realizou ou não a compra.

A campanha piloto teve:

- [ ] **2.240 clientes impactados**
- [ ] **Custo total:** 6.720 MU
- [ ] **Receita total:** 3.674 MU
- [ ] **Resultado:** -3.046 MU
- [ ] **Taxa de conversão:** aproximadamente 15%

Seu desafio é utilizar os dados disponíveis para propor uma estratégia que **melhore a rentabilidade da próxima campanha**.

A base disponibilizada contém informações sobre perfil dos clientes, histórico de compras, comportamento nos diferentes canais e respostas a campanhas anteriores.

## Objetivo do case

O objetivo é recomendar, com base nos dados disponíveis, como melhorar o resultado financeiro da próxima campanha.

Não existe uma única solução correta; esperamos uma análise que sustente sua recomendação, e a abordagem fica a seu critério.

---

# O que esperamos da sua solução

## 1. Análise dos dados e insights

Explore a base e apresente os insights que considerar relevantes para entender os clientes e a oportunidade da campanha.

## 2. Segmentação dos clientes

Proponha e descreva uma segmentação que faça sentido para o problema. A técnica e os critérios ficam a seu critério; explique brevemente como os grupos ajudam a compreender os clientes ou a orientar ações.

## 3. Estratégia e recomendação para a próxima campanha

Com base na análise, proponha uma estratégia quantitativa para decidir quais clientes impactar e recomende como aplicá-la na próxima campanha, buscando melhorar sua rentabilidade. A abordagem fica a seu critério; Machine Learning não é obrigatório.

## 4. Limitações e próximos passos

Explicite as premissas e limitações que considerar relevantes. Se a estratégia fosse implementada, indique brevemente o que faria em seguida ou como acompanharia seu resultado.

# Entregáveis

Esperamos receber dois materiais:

## 1. Análise técnica

Um notebook ou arquivo equivalente contendo o desenvolvimento da análise.

O material deve permitir compreender as principais decisões, análises e tratamentos realizados, além de acompanhar como os resultados foram obtidos. Não é necessário documentar cada linha de código.

## 2. Apresentação executiva

Uma apresentação curta destinada aos stakeholders do negócio.

Apresente os principais insights, a estratégia proposta e a recomendação para o negócio. Selecione o conteúdo e a narrativa que melhor sustentam sua conclusão.

A apresentação deve durar no máximo 10 minutos; idealmente, até 5 minutos para ser direta e objetiva.

---

# Ferramentas utilizadas

Desenvolva o case da forma como você trabalha normalmente, com as ferramentas que costuma utilizar. O uso de IA generativa não é proibido.

A apresentação será seguida de uma conversa sobre sua análise e recomendação.

---

# Dados disponíveis

A base disponibilizada contém as seguintes variáveis:

| **Variável** | **Descrição** |
| --- | --- |
| **AcceptedCmp1** | Indica se o cliente aceitou a oferta da 1ª campanha (1 = sim, 0 = não) |
| **AcceptedCmp2** | Indica se o cliente aceitou a oferta da 2ª campanha (1 = sim, 0 = não) |
| **AcceptedCmp3** | Indica se o cliente aceitou a oferta da 3ª campanha (1 = sim, 0 = não) |
| **AcceptedCmp4** | Indica se o cliente aceitou a oferta da 4ª campanha (1 = sim, 0 = não) |
| **AcceptedCmp5** | Indica se o cliente aceitou a oferta da 5ª campanha (1 = sim, 0 = não) |
| **Response** | Indica se o cliente aceitou a oferta da última campanha (1 = sim, 0 = não) |
| **Complain** | Indica se o cliente realizou alguma reclamação nos últimos 2 anos (1 = sim, 0 = não) |
| **Dt_Customer** | Data de entrada/cadastro do cliente na empresa |
| **Education** | Nível de escolaridade do cliente |
| **Marital_Status** | Estado civil do cliente |
| **Kidhome** | Número de crianças pequenas no domicílio do cliente |
| **Teenhome** | Número de adolescentes no domicílio do cliente |
| **Income** | Renda familiar anual do cliente |
| **MntFishProducts** | Valor gasto com produtos de peixe nos últimos 2 anos |
| **MntMeatProducts** | Valor gasto com produtos de carne nos últimos 2 anos |
| **MntFruits** | Valor gasto com frutas nos últimos 2 anos |
| **MntSweetProducts** | Valor gasto com doces nos últimos 2 anos |
| **MntWines** | Valor gasto com vinhos nos últimos 2 anos |
| **MntGoldProds** | Valor gasto com produtos de ouro nos últimos 2 anos |
| **NumDealsPurchases** | Número de compras realizadas com desconto |
| **NumCatalogPurchases** | Número de compras realizadas por catálogo |
| **NumStorePurchases** | Número de compras realizadas diretamente nas lojas |
| **NumWebPurchases** | Número de compras realizadas pelo site da empresa |
| **NumWebVisitsMonth** | Número de visitas ao site da empresa no último mês |
| **Recency** | Número de dias desde a última compra |
| **ID** | Identificador do cliente. |
| **Year_Birth** | Ano de nascimento do cliente. |
| **Z_CostContact** | Campo disponibilizado na base de dados. |
| **Z_Revenue** | Campo disponibilizado na base de dados. |
