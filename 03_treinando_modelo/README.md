# Treinando o modelo
É aqui que as coisas começam a fazer ainda mais sentido! Nesse capítulo aprenderemos como, de fato, "mostrar" nosso conjunto de dados para o modelo.

Apenas recapitulando, [anteriormente](https://github.com/Marcozz-716/machine-learning-intro/tree/main/02_intro_sklearn) nós criamos o modelo e separamos as variáveis independentes das variáveis dependentes.

```python
import pandas as pd
from sklearn.tree import DecisionTreeRegressor

model = DecisionTreeRegressor(random_state=1)

file = 'data/train.csv'
var_independentes = ['LotArea','YearBuilt','1stFlrSF','2ndFlrSF','FullBath','BedroomAbvGr','TotRmsAbvGrd']
df = pd.read_csv(file)
X = df[var_independentes] # independentes
y = df.SalePrice # dependente
```

Portanto, para treinar nosso modelo basta usar uma função chamada 
`fit()` 
que recebe como argumento as variáveis **X** e **y**.

```python
model.fit(X, y)
```