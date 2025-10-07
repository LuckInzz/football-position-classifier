# Análise de Dados e Modelagem para Classificação de Posições de Jogadores de Futebol



Este projeto realiza uma análise exploratória e modelagem de dados de jogadores de futebol para classificar suas posições (Defensor, Meio-campo, Atacante) com base em suas estatísticas.



## Sumário



1.  **Carregamento do Dataset:** Carrega os dados de estatísticas de jogadores de futebol.

2.  **Limpeza do Dataset:** Realiza a limpeza e pré-processamento dos dados.

3.  **Seleção de Features:** Identifica as features mais relevantes para a classificação.

4.  **Separação e Divisão do Dataset:** Divide os dados em conjuntos de treino e teste e aplica transformações.

5.  **Modelagem:** Treina e avalia diferentes modelos de classificação (KNN, Árvore de Decisão, Naïve Bayes).

6.  **Análise de Resultados:** Compara o desempenho dos modelos e analisa a importância das features.



## Detalhes do Projeto



### 1. Carregamento do Dataset



Os dados são carregados de um dataset do Kaggle usando a biblioteca `kagglehub`.



### 2. Limpeza do Dataset



-   Remoção de jogadores com a posição 'GK' (Goleiro).

-   Simplificação de posições secundárias (ex: 'DF,MF' se torna 'DF').

-   Remoção de jogadores com baixa minutagem (menos de 10 '90s').



### 3. Seleção de Features



Um subconjunto de colunas relevantes é selecionado. As estatísticas são normalizadas por 90 minutos jogados para comparar jogadores com diferentes minutagens de forma justa. A técnica RFECV (Recursive Feature Elimination with Cross-Validation) com uma Árvore de Decisão é utilizada para identificar o número ideal e quais features são as mais importantes para a classificação.



### 4. Separação e Divisão do Dataset



Os dados são separados em features (X) e a variável alvo (y - Posição). O dataset é dividido em conjuntos de treino (80%) e teste (20%) usando `train_test_split` com estratificação para manter a proporção das classes. As features são escaladas usando `StandardScaler` e transformadas usando `PowerTransformer` para melhor performance dos modelos.



### 5. Modelagem



Três modelos de classificação são treinados e avaliados:



-   **K-Nearest Neighbors (KNN):** Um modelo baseado na proximidade dos dados. Foi utilizado `GridSearchCV` para encontrar os melhores hiperparâmetros. A acurácia e o relatório de classificação foram calculados. A importância das features foi visualizada usando SHAP.

-   **Árvore de Decisão:** Um modelo baseado em regras de decisão. Também foi utilizado `GridSearchCV` para encontrar os melhores hiperparâmetros. A importância das features foi calculada e visualizada. A estrutura da árvore treinada foi plotada.

-   **Naïve Bayes:** Um modelo probabilístico simples. O modelo foi treinado e avaliado, e as médias das features por posição foram visualizadas usando um heatmap.



### 6. Análise de Resultados



As métricas de desempenho (Acurácia, Precisão, Recall, F1-score) dos três modelos são comparadas visualmente usando um gráfico de barras. A precisão de cada modelo para cada posição individual (DF, FW, MF) também é comparada em um gráfico de barras separado.



## Requisitos



-   Python 3.7+

-   Bibliotecas: `kagglehub`, `pandas`, `sklearn`, `matplotlib`, `seaborn`, `shap`



Para instalar as dependências, você pode usar pip
