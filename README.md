# Projeto de Classificação: Previsão de Cliques em Anúncios Online

## 📄 Sumário

Este projeto de portfólio demonstra um fluxo completo de Machine Learning, desde a preparação dos dados até a avaliação comparativa de modelos, para prever se um usuário de internet clicará em um anúncio. O modelo campeão, uma **Regressão Logística** otimizada, alcançou um **AUC (Area Under the Curve) de 0.998**, provando ser uma solução robusta, precisa e, crucialmente, interpretável para resolver o problema de negócio.

---

## 🎯 Contexto e Objetivo de Negócio

O objetivo deste projeto é desenvolver um modelo de classificação binária que responda à pergunta: **"Com base no perfil e comportamento de um usuário, qual a probabilidade de ele clicar em um anúncio online?"**

Uma solução eficaz para este problema permite que equipes de marketing digital otimizem o retorno sobre o investimento (ROI) em campanhas, direcionando anúncios de forma mais inteligente e personalizando o conteúdo para perfis com maior propensão à conversão.

---

## 🛠️ Metodologia

O projeto foi estruturado seguindo as melhores práticas de um ciclo de vida de Data Science, dividido em dois notebooks principais.

### 1. Preparação de Dados e Engenharia de Features (`01_data_preparation.ipynb`)

O trabalho começou com o dataset `advertising.csv`. A etapa de preparação incluiu:
* **Limpeza de Dados:** Remoção de colunas com alta cardinalidade que poderiam prejudicar a performance do modelo, como `Ad Topic Line`, `City`, e `Country`.
* **Engenharia de Features:** A coluna `Timestamp` foi transformada para extrair features temporais (`Hour`, `DayOfWeek`, `Month`), permitindo que o modelo aprendesse com padrões baseados em quando o usuário interagia com o site.

### 2. Análise, Modelagem e Avaliação (`02_logistic_regression_analysis.ipynb`)

Com os dados limpos, o segundo notebook focou na análise e modelagem.

#### Análise Exploratória de Dados (EDA)

Foram geradas visualizações para entender a relação entre as features e a variável alvo (`Clicked on Ad`).

![Boxplots das Features Chave vs. Clique](/images/feature_boxplots.png)
*Gráfico gerado a partir do notebook `02_logistic_regression_analysis.ipynb`.*

A análise dos boxplots acima revelou tendências muito claras:
* **Idade (`Age`):** Usuários que clicaram no anúncio (`Clicked on Ad = 1`) tendem a ser mais velhos.
* **Tempo no Site e na Internet:** Usuários que clicam passam, em média, significativamente menos tempo tanto no site (`Daily Time Spent on Site`) quanto na internet em geral (`Daily Internet Usage`).

#### Modelagem e Otimização

* **Modelo Baseline:** A Regressão Logística foi escolhida como o modelo inicial por sua eficiência e alta interpretabilidade.
* **Pipeline e Otimização:** Para garantir a robustez e a comparação justa, todos os modelos foram treinados dentro de um `Pipeline` que incluía a padronização dos dados (`StandardScaler`). O `GridSearchCV` foi aplicado para encontrar os melhores hiperparâmetros para a Regressão Logística.

#### Análise de Interpretabilidade (SHAP)

Para entender *por que* o modelo toma suas decisões, foi utilizada a biblioteca SHAP.

![Gráfico de Barras SHAP](images\shap_summary_plot_beeswarm.png)
*Gráfico gerado a partir do notebook `02_logistic_regression_analysis.ipynb`.*

O gráfico de barras SHAP confirmou as descobertas da EDA de forma quantitativa. Ele mostra que o tempo de uso da internet e o tempo no site são os fatores de maior impacto, seguidos pela idade do usuário.

#### Benchmarking

Para validar a escolha do modelo, a performance da Regressão Logística otimizada foi comparada com outros dois algoritmos poderosos: `Random Forest` e `XGBoost`.

---

## 📈 Resultados

O processo de benchmarking demonstrou que a **Regressão Logística** não apenas foi o modelo mais simples, mas também o que apresentou a melhor performance geral.

### Tabela Comparativa dos Modelos

| Modelo | AUC | Accuracy |
| :--- | :---: | :---: |
| **Logistic Regression** | **0.9980** | **0.9733** |
| Random Forest | 0.9947 | 0.9567 |
| XGBoost | 0.9882 | 0.9467 |

*Tabela de resultados gerada pelo notebook `02_logistic_regression_analysis.ipynb`.*

### Desempenho do Modelo Campeão

O desempenho detalhado da Regressão Logística no conjunto de teste é apresentado no relatório e na matriz de confusão abaixo.

```text
--- Relatório de Classificação: Regressão Logística ---
              precision    recall  f1-score   support
           0       0.95      1.00      0.98       157
           1       1.00      0.94      0.97       143

    accuracy                           0.97       300
   macro avg       0.98      0.97      0.97       300
weighted avg       0.97      0.97      0.97       300