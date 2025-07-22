# Projeto de Machine Learning: Previsão de Cliques em Anúncios

## 1. Contexto e Objetivo de Negócio

Este projeto visa prever se um usuário irá clicar em um anúncio online, auxiliando equipes de marketing a otimizar campanhas e aumentar o ROI.

---

## 2. Descrição do Dataset

O dataset (`advertising.csv`) contém dados sintéticos de usuários e suas interações com anúncios.

| Feature                    | Descrição                                         | Tipo      |
|----------------------------|---------------------------------------------------|-----------|
| Daily Time Spent on Site   | Tempo médio no site (minutos)                     | Numérico  |
| Age                        | Idade do usuário                                  | Numérico  |
| Area Income                | Renda média na área geográfica                    | Numérico  |
| Daily Internet Usage       | Tempo médio na internet por dia (minutos)         | Numérico  |
| Ad Topic Line              | Título do anúncio (removido)                      | Categórico|
| City                       | Cidade do usuário (removido)                      | Categórico|
| Male                       | Sexo masculino (1) ou não (0)                     | Binário   |
| Country                    | País do usuário (removido)                        | Categórico|
| Timestamp                  | Data e hora do acesso                             | Data/Hora |
| Clicked on Ad              | Variável alvo: clicou (1) ou não (0)              | Binário   |

---

## 3. Metodologia

### 3.1. Análise Exploratória (EDA)
- Verificação de desbalanceamento de classes.
- Visualização da relação entre features e variável alvo.

### 3.2. Pré-processamento
- Remoção de variáveis categóricas de alta cardinalidade.
- Padronização das variáveis numéricas com `StandardScaler`.

### 3.3. Modelagem
- Regressão Logística.
- Pipeline para encapsular scaler e modelo.
- Otimização do hiperparâmetro `C` via GridSearchCV.

---

## 4. Resultados e Métricas de Avaliação

- **Acurácia:** XX%
- **AUC:** XX
- **Matriz de Confusão:**  
  *(Insira imagem da matriz de confusão)*
- **Curva ROC:**  
  *(Insira imagem da curva ROC)*

| Métrica   | Classe 0 | Classe 1 |
|-----------|----------|----------|
| Precisão  | XX       | XX       |
| Recall    | XX       | XX       |
| F1-Score  | XX       | XX       |

---

## 5. Como Executar o Projeto

1. Clone o repositório:
    ```bash
    git clone [URL-DO-SEU-REPOSITORIO]
    cd [NOME-DO-REPOSITORIO]
    ```
2. Crie um ambiente virtual e instale as dependências:
    ```bash
    python -m venv venv
    venv\Scripts\activate
    pip install -r requirements.txt
    ```
3. Execute o notebook:
    ```bash
    jupyter notebook projeto-de-regressao-logistica-solucoes.ipynb
    ```

**requirements.txt**
```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

## 6. Conclusão e Insights de Negócio

O modelo mostrou excelente desempenho, com AUC de XX. Idade e tempo de navegação são preditores chave. Equipes de marketing podem usar esses insights para segmentar campanhas e aumentar conversão.
