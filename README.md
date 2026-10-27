# Classificação de Websites de Phishing usando Deep Learning

Este projeto foi desenvolvido como parte da disciplina de Deep Learning da Universidade Federal do Pampa (UNIPAMPA). O objetivo é construir um modelo de rede neural capaz de identificar se um site é fraudulento (Phishing) ou seguro (Legítimo) baseado em características da página e da URL.

## Base de Dados
A base de dados utilizada foi a **Phishing Websites**, obtida no [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/327/phishing+websites).
* **Instâncias (amostras):** 11.055
* **Características (colunas):** 30 atributos (ex: Tamanho da URL, Uso de IP, Favicon, Redirecionamentos, etc.)
* **Classes:** 2 (Problema de Classificação Binária)
  * `0`: Phishing
  * `1`: Legítimo

## Pré-processamento
Para garantir o melhor desempenho da rede neural, os dados passaram pelos seguintes tratamentos:
1. **Normalização:** Utilização do `MinMaxScaler` do Scikit-Learn para colocar todas as 30 características na mesma escala (entre 0 e 1).
2. **Ajuste de Labels:** A variável alvo (Target) foi mapeada de `-1 e 1` para `0 e 1` para adequação à função Sigmoid.
3. **Divisão dos Dados:** Divisão da base em **70% para treinamento** (7.738 amostras) e **30% para teste** (3.317 amostras).

## Arquitetura do Modelo
O modelo utiliza uma arquitetura *Multi-Layer Perceptron (MLP)* enxuta e eficiente, desenhada especificamente para não utilizar processamento excessivo em um problema estruturado simples, evitando assim o risco de *overfitting*.

* **Camada de Entrada:** 30 features
* **Camada Oculta:** 1 camada com 32 neurônios (Função de Ativação: `ReLU`)
* **Camada de Saída:** 1 neurônio (Função de Ativação: `Sigmoid`)
* **Função de Perda:** `binary_crossentropy`
* **Otimizador:** O padrão do Keras/TensorFlow para MLP.
* **Treinamento:** 50 épocas.

## Resultados
O modelo atingiu uma excelente generalização nos dados nunca antes vistos pela rede durante o treinamento.

* **Acurácia no Conjunto de Teste:** ~93.4%
* A matriz de confusão demonstrou uma baixa taxa de falsos positivos (90) e falsos negativos (128), provando que uma única camada oculta bem dimensionada é o suficiente para resolver este problema sem a necessidade de camadas profundas ou técnicas extras (como Dropout).

## Autor
* **Gabriel Torres Machado** - [GitHub](https://github.com/gabrieltm-sudo)
* Engenharia de Computação - UNIPAMPA

