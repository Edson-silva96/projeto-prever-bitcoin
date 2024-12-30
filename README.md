# projeto-prever-bitcoin
## Introdução

O mercado financeiro tem demonstrado grande volatilidade, especialmente no contexto de criptomoedas como o Bitcoin. Este projeto de Ciência de Dados busca aplicar técnicas de Machine Learning para prever os valores futuros da coluna **Close** a partir de dados históricos do Bitcoin. A coluna **Close** reflete o preço de fechamento diário, sendo um indicador crucial para traders e analistas financeiros.

Para alcançar esse objetivo, o conjunto de dados utilizado contém informações históricas detalhadas, como data, preços de abertura e fechamento, volume negociado e os maiores e menores preços diários. Inicialmente, serão realizadas etapas de limpeza e exploração dos dados para garantir consistência e integridade, seguidas pela aplicação de modelos preditivos avançados. O modelo será avaliado com base em métricas de erro preditivo, permitindo uma análise quantitativa de sua precisão.

Este trabalho não apenas contribui para a área de modelagem preditiva no mercado financeiro, mas também oferece insights valiosos para a tomada de decisão em um mercado de alta complexidade e dinamismo.

# interpretaçao inicial

## Analisando o Código e o Gráfico do Bitcoin
O código em Python, utilizando a biblioteca yfinance, extrai dados históricos do preço do Bitcoin em um intervalo de datas específico. Esses dados são então visualizados em um gráfico de linha, onde o eixo x representa o tempo e o eixo y representa o preço em dólares americanos. O código customiza o gráfico com título, rótulos nos eixos e ajusta o tamanho da figura para melhor visualização.

### Interpretando o Gráfico
O gráfico gerado pelo código mostra a variação do preço de fechamento do Bitcoin em dólares americanos ao longo do período de janeiro de 2022 a dezembro de 2024. É possível observar:

* **Tendência Geral:** O preço do Bitcoin apresentou uma tendência de alta durante o período analisado, com algumas oscilações significativas.
* **Volatilidade:** O gráfico mostra que o preço do Bitcoin é bastante volátil, com grandes oscilações de um dia para o outro. Essa volatilidade é característica do mercado de criptomoedas.
* **Períodos de Alta e Baixa:** É possível identificar períodos de alta e baixa no preço do Bitcoin, o que é comum em mercados financeiros.
![bit0](https://github.com/user-attachments/assets/770813ea-f008-4392-bb7e-3c48a23539f2)


##Os Dados gerados do codigo anterior

A saída apresentada mostra uma parte do DataFrame "dados" após a execução do código. Podemos observar as seguintes colunas:

* **Ticker:** Provavelmente indica o par de moedas sendo analisado, neste caso, "BTC-USD" (Bitcoin em relação ao Dólar Americano).
* **Date:** A data de cada registro.
* **Price:** O preço do Bitcoin naquela data.
* **Adj Close:** O preço de fechamento ajustado, que leva em consideração eventos como dividendos e split de ações.
* **Close:** O preço de fechamento.
* **High:** O preço mais alto atingido no dia.
* **Low:** O preço mais baixo atingido no dia.
* **Volume:** O volume de negociação do Bitcoin naquele dia.

**O que o Código Faz:**

Em resumo, o código lê um arquivo CSV contendo dados históricos do Bitcoin e prepara esses dados para análise. Ao remover as linhas com valores faltantes, garante-se que os cálculos e visualizações subsequentes sejam feitos com dados consistentes. 
![bit1](https://github.com/user-attachments/assets/2e3c4bb4-3f23-449d-a3c5-eef1d460fdb2)

## tratado e convertendo os dados
A saída do dados.info() fornece um panorama geral da estrutura e do conteúdo do DataFrame dados, que contém dados históricos do Bitcoin. A conversão dos tipos de dados prepara os dados para análises mais complexas e eficientes.
![bit2](https://github.com/user-attachments/assets/ec60f8f6-bcec-4c0c-8eff-d8e3f0a431c8)

## Analisando a Saída de `dados.describe()`

**Vamos analisar cada uma das estatísticas apresentadas:**

* **count:** Indica o número de valores não nulos (ou seja, sem valores faltantes) em cada coluna. Neste caso, todas as colunas possuem 1074 valores, o que significa que não há dados faltantes para as métricas analisadas.
* **mean:** Representa a média aritmética dos valores de cada coluna. Por exemplo, o preço médio de fechamento ajustado do Bitcoin no período analisado é de aproximadamente 39856.60.
* **std:** Sigla para desvio padrão, que mede a dispersão dos dados em relação à média. Um desvio padrão alto indica que os dados estão mais espalhados, enquanto um desvio padrão baixo indica que os dados estão mais concentrados em torno da média.
* **min:** Representa o menor valor encontrado em cada coluna.
* **25%:** Corresponde ao primeiro quartil, ou seja, 25% dos valores da coluna são menores ou iguais a esse valor.
* **50%:** Corresponde à mediana, que é o valor que divide os dados em duas partes iguais.
* **75%:** Corresponde ao terceiro quartil, ou seja, 75% dos valores da coluna são menores ou iguais a esse valor.
* **max:** Representa o maior valor encontrado em cada coluna.

**Interpretação Geral:**

Essas estatísticas fornecem um resumo rápido e conciso sobre a distribuição dos dados do Bitcoin. Por exemplo:

* **Preço:** O preço do Bitcoin variou entre um mínimo de aproximadamente 15787 e um máximo de 101236 durante o período analisado. O preço médio foi de cerca de 39856.
* **Volatilidade:** O alto desvio padrão do preço indica que o preço do Bitcoin é bastante volátil, ou seja, os preços oscilam significativamente ao longo do tempo.
* **Distribuição:** Os quartis (25%, 50% e 75%) podem ser usados para entender a distribuição dos dados. Por exemplo, se a diferença entre o primeiro e o terceiro quartil for grande, isso indica que há uma grande dispersão nos dados.

* ![bit3](https://github.com/user-attachments/assets/d3cfa95b-b19d-4c69-b058-1f424e75df54)

* ## Analisando o Gráfico de Boxplot e o Código

### O Gráfico de Boxplot

O gráfico de boxplot é uma ferramenta visual útil para entender a distribuição dos dados. Ele mostra a mediana, os quartis (25º e 75º percentis) e os outliers de um conjunto de dados.

**Elementos do Boxplot:**

* **Caixa:** Representa a caixa central, que contém 50% dos dados. A linha horizontal dentro da caixa indica a mediana.
* **Bigodes:** As linhas verticais que se estendem da caixa são os bigodes. Eles indicam o intervalo interquartil (IQR), que é a diferença entre o terceiro e o primeiro quartil.
* **Outliers:** Os pontos individuais fora dos bigodes são considerados outliers.

**Interpretação do Gráfico:**

O gráfico apresentado mostra os boxplots para as colunas 'High', 'Low' e 'Open' dos dados do Bitcoin. Podemos observar que:

* **Distribuição:** As caixas são relativamente simétricas para as três colunas, indicando uma distribuição aproximadamente simétrica dos dados.
* **Variabilidade:** A altura das caixas e a extensão dos bigodes nos dão uma ideia da variabilidade dos dados. Por exemplo, a coluna 'High' parece ter uma variabilidade um pouco maior do que as outras duas.
* **Outliers:** Não há outliers visíveis no gráfico, o que sugere que os dados estão relativamente concentrados em torno da mediana.

**Conclusões:**

* Os preços de abertura, máximo e mínimo do Bitcoin apresentam uma distribuição relativamente similar, com uma leve tendência para os preços mais altos serem mais dispersos.
* A ausência de outliers sugere que os dados estão relativamente limpos e não há valores extremos que possam distorcer a análise.

* ![bit4](https://github.com/user-attachments/assets/e1e1c13f-e5aa-454c-847b-133b964ea93e)

* ## Analisando o Gráfico e o Código

**O que o código faz:**

* **Seleção das colunas:** O código seleciona as colunas 'Price' (preço) e 'Close' (preço de fechamento) do DataFrame 'dados'.
* **Criação do gráfico de linha:** A função `plot()` cria um gráfico de linha, onde o eixo x representa o preço e o eixo y representa o preço de fechamento.
* **Personalização do gráfico:** Os argumentos `figsize=(12, 6)` definem o tamanho da figura em polegadas e `title="Evolução do Fechamento"` define o título do gráfico.
* **Exibição do gráfico:** O comando `plt.show()` exibe o gráfico na tela.

### O Gráfico
O gráfico gerado mostra a evolução do preço de fechamento do Bitcoin ao longo do tempo. Cada ponto no gráfico representa um par ordenado (preço, preço de fechamento). A linha que conecta esses pontos mostra como o preço de fechamento variou ao longo do período analisado.

**Interpretação do Gráfico:**
* **Tendência:** O gráfico mostra uma tendência geral de alta do preço do Bitcoin durante o período analisado.
* **Volatilidade:** O gráfico também mostra uma alta volatilidade, com grandes oscilações de preço em períodos curtos.
* **Padrões:** É possível identificar alguns padrões no gráfico, como períodos de alta e baixa volatilidade, bem como possíveis tendências de curto prazo.

* ![bit5](https://github.com/user-attachments/assets/d0b14e2b-a9ea-45e6-b859-08c12c0212f2)

* ## Análise do Código e Sugestões

### Entendendo o Código
O código fornecido realiza uma análise de regressão para prever o preço de fechamento do Bitcoin com base em outras características, como preço máximo, mínimo, abertura e volume.

**Passo a Passo:**

1. **Seleção das colunas:** As colunas relevantes para a análise são selecionadas do DataFrame `dados`.
2. **Preparação dos dados:**
   * A coluna 'Close' (preço de fechamento) é removida e armazenada em `y` como a variável alvo a ser prevista.
   * As demais colunas são armazenadas em `X` como as características (features) que serão utilizadas para fazer a previsão.
   * A coluna 'Price' é transformada utilizando `LabelEncoder`, provavelmente para converter valores categóricos em numéricos.
3. **Divisão dos dados:** Os dados são divididos em conjuntos de treinamento e teste para avaliar o desempenho dos modelos.
4. **Definição da função de avaliação:** Uma função é definida para avaliar os modelos, calculando o erro absoluto médio (MAE) e o coeficiente de determinação (R²).
5. **Treinamento e avaliação de modelos:** Vários modelos de regressão são treinados e avaliados utilizando os conjuntos de treinamento e teste.

### Analisando os Resultados
Os resultados mostram que todos os modelos testados (Regressão Linear, Árvore de Decisão, Random Forest e Gradient Boosting) obtiveram um R² de 1.00, o que indica que os modelos conseguem explicar 100% da variância dos dados.

O erro absoluto médio (MAE) varia entre os modelos, sendo a Regressão Linear a que apresenta o menor MAE.

### Qual Modelo é o Mais Indicado?

* **Interpretabilidade:** A Regressão Linear é um modelo mais simples e interpretável, o que pode ser uma vantagem em algumas situações.

![bit6](https://github.com/user-attachments/assets/f26876c4-4e9c-4bfa-ae43-f2bdd30a0049)

## Analisando o Gráfico e o Código
### Interpretando o Gráfico
O gráfico apresentado mostra a comparação entre os valores reais e as previsões de um modelo de regressão linear (aparentemente denominado "Linear_prime").

* **Eixo X:** Representa o índice dos dados, ou seja, a posição de cada ponto de dados no conjunto de teste.
* **Eixo Y:** Representa o valor da variável dependente, tanto os valores reais quanto as previsões do modelo.
* **Linhas e marcadores:** Os valores reais são representados por pontos amarelos e as previsões do modelo por marcadores verdes em forma de "x".
* **Tendência:** A linha verde que conecta os marcadores verdes indica a tendência geral das previsões do modelo.

### Analisando o Desempenho do Modelo
A qualidade do modelo pode ser avaliada visualmente observando a proximidade entre os pontos amarelos (valores reais) e os marcadores verdes (previsões).

* **Boa aderência:** Se os marcadores verdes estiverem próximos dos pontos amarelos, significa que o modelo está fazendo previsões precisas.
* **Desvio:** Se os marcadores verdes estiverem distantes dos pontos amarelos, indica que o modelo não está capturando bem a variabilidade dos dados e as previsões podem estar enviesadas.
* **Padrões:** Observe se há algum padrão nos erros de previsão, como o modelo subestimando ou superestimando valores em determinadas regiões.

**Em resumo:**

O gráfico apresentado fornece uma visualização rápida e intuitiva do desempenho do modelo de regressão linear. Ao analisar a proximidade entre os valores reais e as previsões, é possível avaliar a qualidade do modelo e identificar possíveis áreas de melhoria. 

![bit7](https://github.com/user-attachments/assets/b0c711c0-59be-4d70-a947-543e649e75ea)

### O que o código faz?
O código Python apresentado busca realizar uma previsão do preço do Bitcoin utilizando um modelo de regressão linear. Vamos decompor as etapas:

1. **Definição do Ticker:** O código define o ticker do Bitcoin como "BTC-USD", que é o código utilizado para representar o Bitcoin em plataformas financeiras.
2. **Download dos Dados:** A biblioteca `yfinance` é utilizada para baixar os dados históricos do Bitcoin em um determinado período.
3. **Pré-processamento dos Dados:** Os dados baixados são convertidos para o tipo inteiro, possivelmente para simplificar os cálculos ou por alguma restrição do modelo.
4. **Criação do Modelo:** Um modelo de regressão linear é criado e treinado com os dados históricos.
5. **Previsões:** O modelo treinado é utilizado para fazer previsões em novos dados (representados por `x`).
6. **Visualização:** O resultado das previsões é plotado em um gráfico, permitindo visualizar a tendência prevista pelo modelo.

### Interpretação do Gráfico
O gráfico gerado mostra a evolução do preço previsto do Bitcoin ao longo do tempo. A linha representa as previsões do modelo de regressão linear.
    * **Tendência:** A inclinação da linha indica a tendência geral do preço previsto. Se a linha estiver inclinada para cima, o modelo prevê um aumento no preço. Se estiver inclinada para baixo, o modelo prevê uma queda.
    * **Volatilidade:** A amplitude das oscilações da linha indica a volatilidade das previsões. Quanto maior a amplitude, maior a incerteza nas previsões.
    * **Ajuste aos Dados:** A proximidade da linha aos dados reais (caso fossem plotados no mesmo gráfico) indicaria a qualidade do ajuste do modelo.

**Em resumo:**

O código apresentado realiza uma previsão simples do preço do Bitcoin utilizando um modelo de regressão linear. O gráfico gerado permite visualizar a tendência prevista pelo modelo. No entanto, é importante ter em mente as limitações desse tipo de modelo e considerar outras abordagens para obter previsões mais precisas e robustas.

![bit8](https://github.com/user-attachments/assets/ea798902-edb4-4f52-abd4-e17eeaf75ee7)


















