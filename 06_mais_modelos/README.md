# Testando mais modelos

Até aqui nós usamos o 
`DecisionTreeRegressor`
 , do sklearn, e agora poderemos experimentar um novo modelo: O 
`RandomForestRegressor`
. Esse modelo também se baseia em árvores de decisão, porém ele se destaca porque usa um conjunto dessas árvores para prever os valores. No caso de um problema de regressão (como o de prever o preço de imóveis) o **Random Forest** nos retorna a média das previsões das árvores, já em um problema de classificação (como por exemplo uma situação onde é preciso determinar se um e-mail é spam ou não) o **Random Forest** nos retorna a classe mais votada entre as árvores.

!()[random-forest-algorithm-random-forest.webp]

Para que o Random Forest faça boas previsões é necessário que o modelo consiga absorver os diferentes aspectos do dataset, caso contrário, se as previsões de todas as árvores forem iguais a ideia de usar um conjunto delas deixaria de ser um diferencial. Por isso o **sklearn** deve garantir que cada árvore consiga captar um aspecto diferente do dataset, e algumas das principais técnicas são:

### 1. Amostragem aleatória: 
O Random Forest utiliza o método de **Bootstrap**, onde cada árvore é treinada com um fragmento aleatório do dataset possibilitando que um mesmo dado seja "escolhido" no treinamento mais de uma vez (o que é chamado de "**reposição**")

### 2. Seleção de variáveis:
Aqui são as variáveis independentes que são separadas entre as árvores, fazendo com que cada árvore tenha variáveis diferentes pra lidar

A variação das amostras ajuda a reduzir o overfitting e a tornar o modelo mais sensível a diferentes aspectos dos dados. Com o sklearn o Random Forest é usado da seguinte maneira:

```python
from sklearn.ensemble import RandomForestRegressor
rf_model = RandomForestRegressor(random_state=0)
rf_model.fit(train_x, train_y)
predict = rf_model.predict(val_x)
# é possível calcular o MAE também
```

## Hiperparâmetros