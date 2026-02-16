# 📊 Previsão de Aprovação de Empréstimos com Machine Learning

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-green.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Data_Visualization-lightblue.svg)

## 📝 Sobre o Projeto
Este projeto tem como objetivo desenvolver um modelo preditivo de Machine Learning capaz de classificar se um cliente terá ou não um empréstimo liberado. Trata-se de um problema de **Classificação Binária** (`SIM` ou `NÃO`), utilizando dados socioeconômicos e de histórico financeiro dos clientes.

O algoritmo principal escolhido para a modelagem foi o **Random Forest (Floresta Aleatória)**, otimizado através de validação cruzada (`GridSearchCV`).

## 📁 Dicionário de Dados
O modelo foi treinado utilizando uma base de dados (`dados_credito.xlsx`) contendo as seguintes variáveis explicativas:
* `UF`: Estado de residência do cliente.
* `IDADE`: Idade do cliente.
* `ESCOLARIDADE`: Nível de formação acadêmica.
* `ESTADO_CIVIL`: Estado civil do cliente.
* `QT_FILHOS`: Quantidade de filhos.
* `CASA_PROPRIA`: Indicador se possui casa própria (Sim/Não).
* `QT_IMOVEIS`: Quantidade de imóveis em nome do cliente.
* `VL_IMOVEIS`: Valor total dos imóveis.
* `OUTRA_RENDA_VALOR`: Valor de rendas extras.
* `TEMPO_ULTIMO_EMPREGO_MESES`: Tempo no último emprego (em meses).
* `TRABALHANDO_ATUALMENTE`: Indicador de emprego atual (Sim/Não).
* `ULTIMO_SALARIO`: Valor do último salário recebido.
* `QT_CARROS`: Quantidade de carros no nome do cliente.
* `VALOR_TABELA_CARROS`: Valor dos veículos na tabela Fipe.
* `SCORE_CREDITO`: Pontuação de crédito do cliente.
* **`EMPRESTIMO` (Variável Alvo)**: Indicador de aprovação do empréstimo (SIM/NAO).

*(Obs: A coluna `CODIGO_CLIENTE` foi removida por não possuir valor preditivo).*

## 🛠️ Tecnologias e Bibliotecas Utilizadas
* **Python 3**
* **Pandas & NumPy:** Manipulação e tratamento de dados.
* **Matplotlib & Seaborn:** Análise exploratória e visualização de dados (Boxplots e Countplots).
* **Scikit-Learn:** Machine Learning (Pré-processamento, Treinamento, Tuning e Avaliação).

## ⚙️ Etapas do Projeto
1. **Análise Exploratória de Dados (EDA):** Verificação da distribuição das variáveis numéricas e categóricas através de gráficos para identificar padrões e possíveis *outliers*.
2. **Pré-processamento:**
   * Tratamento de valores nulos.
   * Conversão de variáveis categóricas em numéricas utilizando `LabelEncoder`.
   * Separação de dados de Treino (70%) e Teste (30%).
   * Normalização das features utilizando `MinMaxScaler` para colocar os dados na mesma escala.
3. **Modelagem e Otimização:** * Definição do modelo `RandomForestClassifier`.
   * Realização de Tuning de Hiperparâmetros utilizando `GridSearchCV` para encontrar a melhor combinação de árvores, profundidade, critério de divisão, etc.
4. **Avaliação do Modelo:** Análise da acurácia e da importância de cada variável (*Feature Importance*) para a tomada de decisão do modelo.

## 🚀 Resultados Obtidos

Após a otimização com o `GridSearchCV`, os melhores hiperparâmetros encontrados foram:
* `bootstrap`: True
* `criterion`: 'gini'
* `max_depth`: 20
* `max_features`: 'log2'
* `min_samples_leaf`: 1
* `min_samples_split`: 2
* `n_estimators`: 150

**Métricas de Acurácia:**
* 🎯 Acurácia em Treinamento: **87.35%**
* 🎯 Acurácia em Teste: **81.91%**

**Feature Importance:**
O modelo revelou que as variáveis que mais influenciam na aprovação do crédito são, respectivamente:
1. `SCORE_CREDITO` (~33.8%)
2. `IDADE` (~23.1%)
3. `UF` (~9.8%)
4. `QT_FILHOS` (~7.1%)

## 💻 Como executar este projeto

1. Clone este repositório:
```bash
git clone https://github.com/mm-dantas/credit-score-predictor.git
