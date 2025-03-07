# Overfitting e Underfitting
Quando estamos aprendendo sobre machine learning dois dos conceitos mais temidos são o **overfitting** e o **underfitting**. Ambos são opostos um do outro, mas representam problemas relacionados a forma como o modelo lida com os dados. A seguir será explicada a diferença entre esses conceitos.

## Overfitting
O **Overfitting** se refere a adaptação excessiva de um modelo aos dados de treino, o que provoca uma queda de desempenho em dados que ele não viu. Um modelo em overfitting não tem uma boa capacidade de generalização, pois acaba "decorando" padrões e ruídos muito específicos do conjunto de dados usado em seu treinamento, o que o impede de ter boa performance em novos dados.

![overfitting](https://pbs.twimg.com/media/FSAM8FpWUAISGyd.jpg)

## Underfitting
O **Underfitting**, por outro lado, se refere a falta de desempenho de um modelo tanto nos dados de treino quanto nos de teste. Isso geralmente acontece quando o modelo é muito simples e incapaz de capturar padrões, ou quando o conjunto de dados é muito pequeno, ou então quando são escolhidas features com pouca relevância.

## Nosso contexto
No nosso contexto, onde escolhemos usar a 
`DecisionTreeRegressor`
, isso pode se manifestar na relação entre os **parâmetros** do modelo, como a profundidade da árvore, e as características do nosso conjunto de dados, como quantidade e qualidade das features. 

Para identificar se nosso modelo está em underfitting ou overfitting podemos analisar alguns padrões que aparecem no **Erro Médio Absoluto** e na complexidade do modelo.

![](over_under.png)

Se nosso modelo é simples e está tendo um MAE alto tanto no treino quanto no teste podemos dizer que ele está em **underfitting**. Se a complexidade do modelo aumenta e ele tem bom desempenho no treino mas um desempenho ruim no teste podemos dizer que ele está em **overfitting**.

## Otimização de hiperparâmetros
