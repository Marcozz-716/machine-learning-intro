# Introdução à análise exploratória
A análise exploratória é essencial no contexto do machine learning. Antes de construir o modelo em si, é sempre bom examinar o conjunto de dados em que estamos trabalhando. Na linguagem Python existem muitas bibliotecas usadas nessa etapa de manipulação de dados, mas nesse capítulo falarei do **Pandas**: um poderoso aliado do aprendizado de máquina.

## Importação e uso
Para usar a biblioteca no seu código você pode usar:

```python
import pandas as pd # para usar o pandas pela abreviação "pd"
```

Agora já estamos prontos para ver um exemplo do uso do Pandas na manipulação de um arquivo **csv***, muito comum no contexto de ciência de dados. 

```python
file_path = '/caminho/arquivo.csv'
dataframe_with_csv = pd.read_csv(file_path)
```

Explicação: criamos uma variável chamada "dataframe_with_csv", e nela chamamos o método
`read_csv()``
que lê o arquivo csv e cria em um dataframe. Dataframes são estruturas semelhantes a planilhas, e **organizar os dados nessa forma será útil para as operações futuras**.

### Caso o código dê erro
Alguns erros comuns são 
`ParseError: Error tokenizing data. C error: Expected 1 fields`
, ou ainda
`UnicodeDecode Error: 'utf-8' codec can't decode byte 0xcd...`.
Isso pode indicar que contém caractéres incompatíveis com a codificação **utf-8**

Para resolver isso você pode usar alguns argumentos no método read_csv():
```python
dataframe_with_csv = pd.read_csv(file_path, encoding='iso-8859-1', delimiter=';')
```

## Métodos básicos com dataframes
Agora que vimos como criar um dataframe a partir de um csv podemos ver algumas operações básicas. Uma delas é a visualização com o método 
`describe()`
que mostra alguns valores interessantes sobre nosso conjunto de dados: 

```python
file_path = '/data/california_housing_train.csv' 
dataframe_with_csv = pd.read_csv(file_path)
dataframe_with_csv.describe()
```
**output:**
![Output](output_describe.png)

As colunas no sentido horizontal (longitude, latitude, etc...) são as colunas do próprio csv, e as colunas no sentido vertical são cálculos feitos pelo próprio Pandas. Essas colunas verticais são importantes para termos uma visão geral dos nossos dados e a seguir explicarei o que cada um representa:

**- count:** Representa o número de valores não nulos em uma coluna.

**- mean:** A média dos valores em uma coluna. Ele soma os valores não nulos da coluna e divide pela quantidade de valores não nulos.

**-std:** É o desvio padrão que indica o quão afastados os valores estão da média. Um desvio padrão alto indica que há uma maior variação nos dados, já um desvio padrão baixo indica que os dados estão próximos da média.




