# Estratégia de Targeting para Campanha de Marketing

## Contexto

Case técnico para a vaga de **Analista Pleno de Estratégia de Fraudes** no iFood.

Uma empresa de varejo de alimentos realizou uma campanha piloto com 2.240 clientes
selecionados aleatoriamente para oferecer um novo produto. O resultado foi prejuízo.
O desafio é utilizar os dados disponíveis para propor uma estratégia data-driven que
melhore a rentabilidade da próxima campanha.

## Resultados do Piloto

| Métrica | Valor |
|---|---|
| Clientes impactados | 2.240 |
| Custo por contato | 3 MU |
| Receita por conversão | 11 MU |
| Custo total | 6.720 MU |
| Receita total | 3.674 MU |
| Conversões | 334 (14,9%) |
| **Resultado** | **-3.046 MU (rentabilidade: -45,3%)** |
| Ponto de equilíbrio | 27,3% de conversão |

## Abordagem

```
Fase 1 → Tratamento e limpeza dos dados
Fase 2 → Análise exploratória (EDA) + Segmentação
Fase 3 → Estratégia de targeting por regras
Fase 4 → Machine Learning (regressão logística)
```

### Fase 1 — Tratamento

| # | Tratamento | Decisão |
|---|---|---|
| 1 | Year_Birth (3 valores inválidos: 1893, 1899, 1900) | Imputar mediana (manter cliente) |
| 2 | Income nulo (24 linhas) | Imputar mediana |
| 3 | Income outlier (666.666) | Capar no percentil 99 |
| 4 | Marital_Status (Absurd, YOLO, Alone) | Reagrupar em "Other" |
| 5 | Z_CostContact e Z_Revenue | Remover (parâmetros fixos, não features) |
| 6 | Feature engineering | Age, Months_Enrolled, Total_Spent, Total_Accepted_Cmps, Total_Kids, Total_Purchases |

Base final: 2.240 linhas × 33 colunas (zero nulos, zero duplicatas).

### Fase 2 — EDA e Segmentação

Correlação com Response (top variáveis):

| Variável | Correlação |
|---|---|
| Total_Accepted_Cmps | +0,43 |
| AcceptedCmp5 | +0,33 |
| AcceptedCmp1 | +0,29 |
| Total_Spent | +0,27 |
| AcceptedCmp3 | +0,25 |
| MntWines | +0,25 |
| Recency | -0,20 |
| Total_Kids | -0,17 |

Perfil do conversor:
- Renda 19% maior (60.052 vs 50.297 MU)
- Gasta 83% mais (987 vs 539 MU)
- Aceitou 5x mais campanhas anteriores (1,0 vs 0,18)
- Recency 32% menor (35 vs 52 dias)
- 50,6% sem filhos vs 24,6% dos não-conversores

### Fase 3 — Estratégia por Regras

| Cenário | Clientes | Conversões | Taxa | Lucro | Rentabilidade |
|---|---|---|---|---|---|
| Piloto | 2.240 | 334 | 14,9% | -3.046 | -45,3% |
| C1: Accepted >= 1 | 463 | 188 | 40,6% | +679 | +48,9% |
| C2: AcceptedCmp5 == 1 | 163 | 92 | 56,4% | +523 | +107,0% |

Insight: variáveis de campanha dão lucro isoladas; variáveis de gasto não — são complementares.

### Fase 4 — Machine Learning

Regressão logística considerando todas as variáveis simultaneamente.

| Cenário | Clientes | Conversões | Taxa | Lucro | Rentabilidade |
|---|---|---|---|---|---|
| **ML Equilíbrio** | **164** | **135** | **82,3%** | **+993** | **+201,8%** |
| ML Lucro máx. | 425 | 240 | 56,5% | +1.365 | +107,1% |
| ML Rentab. máx. | 52 | 47 | 90,4% | +361 | +231,4% |

Variáveis que mais aumentam a probabilidade de conversão:
1. Months_Enrolled (tempo de cadastro)
2. Education_PhD
3. Total_Accepted_Cmps
4. AcceptedCmp3
5. MntMeatProducts

## Recomendação Final

Adotar o **ML de equilíbrio** (164 clientes, +993 MU, +201,8% de rentabilidade).
Captura 73% do lucro máximo e 76% da rentabilidade máxima simultaneamente.

As estratégias por regras (C1 e C2) serviram como base analítica — o ML pegou o que
funcionava nelas e otimizou considerando todas as variáveis em conjunto.

## Limitações

1. Modelo treinado e testado na mesma base (sem split treino/teste)
2. Custo (3 MU) e receita (11 MU) fixos — se mudarem, o equilíbrio (27,3%) muda
3. Base do piloto pode não representar a população total
4. Variáveis externas (sazonalidade, concorrência, preço) não consideradas

## Próximos Passos

1. Teste A/B antes de escalar (grupo controle vs tratamento)
2. Divisão treino/teste para estimativa realista de performance
3. Incorporar custo variável por canal de contato
4. Monitorar conversão, lucro e rentabilidade ao longo das campanhas
5. Explorar modelos mais complexos (Random Forest, XGBoost)

## Estrutura do Projeto

```
ifood-fraud-strategy-case/
├── README.md
├── notebooks/
│   └── case_analise.py          # Notebook Databricks exportado
├── data/
│   └── ifood_case_data.csv      # Base de dados (2.240 clientes)
└── presentation/
    └── apresentacao_executiva.pptx
```

## Como Reproduzir

1. Subir `data/ifood_case_data.csv` como tabela no Databricks
2. Importar `notebooks/case_analise.py` como notebook no Databricks
3. Executar as células em ordem

## Tecnologias

- Databricks (SQL + Python/pandas)
- scikit-learn (regressão logística)
- matplotlib (visualizações)
- Git (versionamento)
