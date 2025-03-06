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

### Caso o código dê erro
Alguns erros comuns são 
`ParseError: Error tokenizing data. C error: Expected 1 fields`
, ou ainda
`UnicodeDecode Error: 'utf-8' codec can`t decode byte 0xcd...`.
Isso pode indicar que contém caractéres incompatíveis com a codificação **utf-8**

Para resolver isso você pode usar:
```python
dataframe_with_csv = pd.read_csv(file_path, encoding='iso-8859-1', delimiter=';')
```

Explicação: criamos uma variável chamada "dataframe_with_csv", e nela chamamos o método
`read_csv()``
que lê o arquivo csv e cria em um dataframe. Dataframes são estruturas semelhantes a planilhas, e **organizar os dados nessa forma será útil para as operações futuras**.

