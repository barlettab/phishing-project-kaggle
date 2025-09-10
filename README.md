# Detecção de Phishing com Machine Learning

Este projeto tem como objetivo desenvolver e avaliar modelos de Machine Learning para prever com precisão se uma URL é de phishing ou legítima, com base em um conjunto de características extraídas.

## 1. Definição do Problema

Diante do cenário de crescente sofisticação dos ataques de phishing, este projeto aborda as seguintes questões centrais:

- É possível prever com precisão se uma página é phishing ou legítima com base nas características extraídas?
- Quais são as principais características que diferenciam uma página phishing de uma legítima?
- Como é o desempenho do modelo de classificação entre os algoritmos de machine learning Random Forest, Árvore de Decisão e Regressão Linear?

## 2. Coleta e Compreensão dos Dados

O dataset utilizado, "Phishing_Legitimate_full.csv", contém 10.000 entradas e 50 colunas. Uma análise inicial revelou que não há valores ausentes e a distribuição da classe alvo (`CLASS_LABEL`) é balanceada (5000 legítimas e 5000 de phishing). A correlação entre as variáveis foi visualizada através de um heatmap.

## 3. Pré-processamento e Limpeza dos Dados

- A coluna 'id' foi removida por não ser relevante para a modelagem.
- Outliers foram identificados através de box plots, mas optou-se por não removê-los, pois podem ser características importantes de URLs de phishing.
- A padronização das variáveis foi realizada apenas para o modelo de Regressão Logística, que é sensível à escala.
- Não foi realizada redução de dimensionalidade, pois o número de variáveis (49 após remover 'id') não é considerado alto.

## 4. Seleção e Modelagem com Algoritmos de Mineração de Dados

O problema foi definido como uma classificação binária. Foram selecionados os seguintes algoritmos:

- Regressão Logística (Logistic Regression)
- Árvore de Decisão (Decision Tree)
- Random Forest (RandomForest)

A configuração dos parâmetros para cada modelo foi realizada utilizando `GridSearchCV` com validação cruzada (cv=5) e métrica de avaliação F1-Score.

Os modelos foram treinados e avaliados, e a importância das variáveis foi analisada para Random Forest, Decision Tree, e Regressão Logística.

## 5. Interpretação e Avaliação dos Resultados

Os modelos foram avaliados e comparados utilizando métricas como Acurácia, Precisão, Recall e F1-Score. A Random Forest apresentou o melhor desempenho geral.

Uma análise da matriz de confusão foi realizada para o melhor modelo (Random Forest com as Top 15 features) para entender os erros de classificação (Falsos Positivos e Falsos Negativos). A distribuição balanceada das classes e a análise das métricas por classe indicaram que o modelo não apresenta viés significativo em relação a uma das classes.

As variáveis consideradas mais importantes pelos modelos foram interpretadas, fornecendo insights sobre as características que mais contribuem para a detecção de phishing.

## 6. Implantação e Monitoramento (Planejamento)

O planejamento de implantação para este modelo de detecção de phishing inclui as seguintes possibilidades:

- **API:** Empacotar o modelo como um serviço web para integração com outras aplicações.
- **Dashboard ou Relatório Interativo:** Apresentar os resultados da classificação e insights em um formato visual e compreensível.
- **Extensão de Navegador:** Desenvolver uma extensão para alertar usuários em tempo real.
- **Integração em Sistemas de Segurança:** Incorporar o modelo em firewalls, proxies, etc.

Mesmo sem implantação direta, os resultados podem ser utilizados para educação, desenvolvimento de regras heurísticas, análise forense e aprimoramento de ferramentas existentes.
