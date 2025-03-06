# Primeiros modelos
Anteriormente vimos o uso do **Pandas** para uma análise exploratória básica. A seguir nós veremos a utilidade disso na criação dos nossos primeiros modelos de machine learning.

Para a criação do modelo nós usaremos a biblioteca 
`sklearn` 
(Scikit-learn), do Python. Ela oferece uma gama de ferramentas para ML, tanto para coisas mais simples quanto para modelos mais robustos. 

## Escolhendo modelo
Para os exemplos a seguir, usaremos o modelo 
`DecisionTreeRegressor`
. Uma implementação de árvore de decisão para tarefas de regressão, disponível no sklearn. Em termos simples, uma árvore de decisão é como um conjunto de perguntas encadeadas (ou nós), onde cada pergunta divide os dados em diferentes grupos com base em características específicas. Esse processo continua até que os grupos formados sejam o mais homogêneos possível.
![](tree.png)

Nas tarefas de regressão (como a nossa), as "perguntas" feitas para separar os dados são baseadas em um critério chamado variância. A cada divisão o modelo tenta reduzir a variância dentro dos grupos, ou seja, ele busca separar os dados de maneira que os valores nas diferentes ramificações da árvore sejam mais próximos entre si. Esse processo de divisão continua até que a variância seja baixa o bastante, formando grupos mais homogêneos. No futuro posso criar um repositório dedicado a árvores de decisão, explicando esses conceitos com maior profundidade. 

Com sklearn nós usamos esse modelo da seguinte forma:

```python
# caso você não tenha instalado use: 
# pip install scikit-learn
from sklearn.tree import DecisionTreeRegressor
model = DecisionTreeRegressor(random_state=1)
```

O modelo foi criado e definimos também um 
`random_state=1`.
 **O random_state serve pra garantir a reprodutibilidade dos resultados do modelo**, ou seja, com a mesma base de dados e o mesmo código, teremos os mesmos resultados. É como se ele "controlasse" a aleatoriedade do modelo.

 ## Nosso intuito com o modelo
 Nosso intuito é usar um modelo de machine para prever os valores de casas a partir de dados do arquivo [train.csv](https://github.com/Marcozz-716/machine-learning-intro/tree/main/02_intro_sklearn/data)

 ![](train%20photo.png)

 Para isso, usaremos informações como o número de cômodos, localização e etc, e por isso nós precisamos separar os dados em **variáveis independentes** e **variáveis dependentes**.
  
 As **variáveis independentes**, ou features, são aquelas que acreditamos que têm influência sobre o valor que estamos tentando prever. Nesse caso, as features escolhidas serão:

**LotArea:** Tamanho do terreno.

**1stFlrSF:** Pés quadrados do primeiro andar.

**2ndFlrSF:** Pés quadrados do segundo andar.

**YearBuilt:** Ano de construção do imóvel.

**FullBath:** Quantidade de banheiros completos.

**BedroomAbvGr:** Número de quartos acima do nível do solo.

**TotRmsAbvGrd:** Total de cômodos acima do nível do solo.
<br>
<br>
A **variável dependente**, no nosso caso, é a coluna
`SalePrice`
, já que é o valor que queremos prever.

```python
import pandas as pd
file = 'data/train.csv'
var_independentes = ['LotArea','YearBuilt','1stFlrSF','2ndFlrSF','FullBath','BedroomAbvGr','TotRmsAbvGrd']
df = pd.read_csv(file)
X = df[var_independentes] # independentes
y = df.SalePrice # dependente
```
### Observações
Em alguns casos o conjunto de dados pode conter valores faltantes, e o Pandas oferece algumas alternativas pra contornar isso, como por exemplo apagar as linhas com valores faltantes. 

```python
df = df.dropna(axis=0) # remove qualquer linha que tenha valores vazios
```

Caso queira ser menos drástico, pode definir um número tolerável de valores faltantes. 

```python
df = df.dropna(thresh=2) # remove qualquer linha que tenha mais de 2 valores vazios
```