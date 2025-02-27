# Pandas
## Definição
##### Pandas é uma biblioteca de Python voltada à manipulação e visualização de dados. Sua estrutura é fundamentada em dois pacotes essenciais: 
- **NumPy**: oferece objetos de matriz multidimensional para facilitar a manipulação de dados
- **Matplotlib**: oferece capacidades robustas de visualização de dados

## Importação da biblioteca
`>> import pandas as pd`

## Dataframes
##### Organização dos dados de modo estruturado no formato de tabela.

### Criando um Dataframe
##### Uma das formas mais simples de criar um dataframe é por meio de dicionários e listas.
```
>> #Criando as listas em um dicionário:
>> dados = {
    'Nome': ['Max', 'Bella', 'Rocky', 'Luna'],
    'Raça': ['Labrador', 'Poodle', 'Boxer', 'Golden Retriever'],
    'Cor': ['Amarelo', 'Branco', 'Marrom', 'Dourado'],
    'Peso(kg)': [60, 35, 65, 55],
    'Data de Nascimento': ['01/05/2018', '10/12/2019', '03/08/2017', '12/02/2016']
}

>> #Criando o Dataframe
>> df_cachorros = pd.Dataframe(dados)
```
### Convertendo um arquivo em Dataframe
#### csv
```
>> df_csv = pd.read_csv('arquivo.csv')
```
#### excel
```
>> df_excel = pd.read_excel('arquivo.xlsx', sheet_name='nome_da_planilha')
```
#### json
```
>> df_json = pd.read_json('arquivo.json')
```
#### parquet
```
>> df_parquet = pd.read_parquet('arquivo.parquet')
```
#### SQL
```
>> #sqlalchemy: biblioteca do Python para interagir com banco de dados relacionais; create_engine: função do SQLAlchemy que cria uma conexão com diferentes tipos de banco de dados (SQLite, PostgreSQL, MySQL, etc.)
>> from sqlalchemy import create_enginee 

>> engine = create_engine('sqlite://banco_de_dados.db')
>> query = 'SELECT * FROM tabela'
>> df_sql = pd.read_sql(query,engine)
```
### Componentes de um Dataframe
- **.values**: os valores (dados) de uma tabela;
- **.columns**: as etiquetas (labels) das colunas;
- **.index**: as etiquetas das linhas.

### Métodos do Dataframe
#### df.head()
##### Exibe as primeiras cinco linhas da tabela por padrão, podendo alterar essa quantidade passando o número desejado como argumento.

```
>> df_cachorros.head()
#ou
>> df_cachorros.head(10)
```

#### df.info()
##### Exibe os nomes das colunas, se há linhas vazias e qual o tipo de dados da coluna.
```
>> df.cachorros.info()
```

#### df.shape
##### Exibe a quantidade de linhas e colunas de uma tabela.
```
>> df_cachorros.shape

(10, 6) #a tabela cachorros possui 10 linhas e 6 colunas
```

#### df.describe()
##### Retorna algumas estatísticas descritivas básicas de cada coluna. Entre elas:
- **count**: contagem de elementos não nulos da coluna
- **mean**: média da coluna
- **std**: desvio padrão dos valores da coluna
- **min**: menor valor da coluna
- **25%**: primeiro quartil da coluna
- **50%**: mediana da coluna
- **75%**: terceiro quartil da coluna
- **max**: maior valor da coluna
```
>> df_cachorros.describe()
```

#### df.sort_values()
##### Ordena as linhas da tabela a partir dos valores de uma coluna.
```
>> df_cachorros.sort_values('Altura(cm)') 
```
##### Por padrão, a ordenação é crescente. Para ordenar em ordem descresente, será preciso utilizar o argumento acsending=False
```
>> df_cachorros.sort_values('Altura(cm)', acsending=False) 
```
##### É possível também ordenar a tabela a partir de mais de uma coluna.
 ```
>> df_cachorros.sort_values(['Altura(cm)', 'Peso (kg)']) 
```
##### Para ordenar múltiplas colunas em ordem crescente e decrescente, basta utilizar mais de um argumento em ascending.
 ```
>> df_cachorros.sort_values(['Altura(cm)', 'Peso (kg)'], ascending=[True, False]) 
```
#### .isin
##### Filtra os dados de uma coluna cujo tipo seja uma variável categórica. Para isso, escolhe-se uma lista de valores para filtrar.
```
is_marrom_ou_cinza = df_cachorros['Cor'].isin(['Cinza', 'Marrom'])
df_cachorros[is_marrom_ou_cinza]
```

### Subconjunto
#### Colunas
##### Para exibir colunas selecionadas, basta chamar a tabela especificando quais colunas deseja visualizar.
```
>> df.cachorros['Nome']
```
```
>> df.cachorros[['Nome', 'Altura (cm)']]
```
#### Linhas
##### A seleção de linhas pode atender aos critérios condicionais que deseja visualizar, por meio da filtração de dados. Para exibir linhas selecionadas, basta chamar a tabela especificando as codicionais.
```
>> df_cachorros['Altura (cm)'] > 40
```
##### O comando acima retorna valores booleanos para cada linha da tabela. Para exibir o subconjunto de linhas que atendam à condicional, deve-se inserir a condição lógica dentro do colchetes de uma tabela.
```
>> df_cachorros[df_cachorros['Altura (cm)'] > 40]
```
```
>> df_cachorros[df_cachorros['Raça'] == 'Boxer']
```
```
#Para datas, utilizar o formato MM/DD/AAAA
>> df_cachorros[df_cachorros['Data de Nascimento'] < '12/05/2017']
```
```
>> df_cachorros[df_cachorros['Raça'] == 'Boxer']
```
##### É possível também criar um subconjunto dos dados utilizando múltiplas condições. Para facilitar na escrita do cógigo, pode-se atribuir cada condicional a uma variável e utilizá-la ao chamar a tabela.
```
>> is_husky = df_cachorros['Raça'] == 'Husky'
>> is_preto = df_cachorros['Cor'] == 'Cinza'
>> df_cachorros[is_husky & is_preto]
```

### Manipulação de dados
#### Adicionar novas colunas
```
>> df_cachorros['Altura (m)'] = df_cachorros['Altura (cm)'] / 100
>> df_cachorros
```
## Agregação de dados
### Extração estatísticas
##### Números que resumem e fornecem informações sobre o conjunto de dados.
- **.median()**: calcula a mediana de um conjunto de dados, indicando o valor central quando os dados estão ordenados;
- **.mode()**: identifica o(s) valor(es) mais frequente(s) de um conjunto de dados;
- **.min()**: identifica o valor mínimo de um conjunto de dados;
- **.max()**: identifica o valor máximo de um conjunto de dados;
- **.var()**: calcula a variância, uma medida da dispersão dos dados;
- **.std()**: calcula o desvio padrão, indicando a dispersão média dos dados em relação à média;
- **.sum()**: calcula a soma de todos os valores de um conjunto de dados;
- **.quantile()**: calcula um percentil específico de um conjunto de dados, indicando o valor abaixo do qual uma determinada porcentagem dos dados está.
##### Exemplos:
```
>> df_cachorros['Altura'].min()
5

>> df_cachorros['Altura'].max()
45

>> df_cachorros['Nome'].max() #Exibe a última letra do alfabeto
'Zoe'
```

### Métodos de agregação 
#### .agg()
##### Permite a utilização de cálculos estatísticos personalizados atribuídos a uma variável.
```
>> def pct50(coluna):
    return coluna.quantile(0.50)

>> df_cachorros['Altura (cm)'].agg(pct50)
23.0

>> df_cachorros[['Altura (cm)', 'Peso (kg)']].agg(pct50)
Altura (cm)     23.0
Peso (kg)       47.5
dtype: float64
```
```
>> def max_min(coluna):
    return coluna.max(), coluna.min()

>> df_cachorros[['Altura (cm)', 'Peso (kg)']].agg(max_min)
    Altura (cm)     Peso (kg)
0           45            65
1            5            25
```
#### .cumsum()
##### Retorna a soma acumulada linha a linha de uma tabela.
```
>> df_cachorros['Peso (kg)']
0   60
1   35
2   65
3   55
4   40
5   33
6   25
7   28
8   60
9   63
Name: Peso (kg), dtype: int64

>> df_cachorros['Peso (kg)'].cumsum()
0   60
1   95
2   160
3   215
4   255
5   288
6   313
7   341
8   401
9   464
Name: Peso (kg), dtype: int64
```
##### O pandas também possui outros métodos para estatísticas cumulativas, como:
- **.cummax()**: calcula o máximo cumulativo, retornando uma série de valores máximos à medida em que percorre um conjunto de dados.
```
>> df_cachorros['Peso (kg)'].cumsum()
0   60
1   60
2   65
3   65
4   65
5   65
6   65
7   65
8   65
9   65
Name: Peso (kg), dtype: int64
```
- **.cummin()**: calcula o mínimo cumulativo, retornando uma série de valores mínimos à medida em que percorre um conjunto de dados.
```
>> df_cachorros['Peso (kg)'].cumsum()
0   60
1   35
2   35
3   35
4   35
5   35
6   25
7   25
8   25
9   25
Name: Peso (kg), dtype: int64
```
- **.cumprod()**: calcula o produto cumulativo, retornando uma série de valores multiplicados cumulatativamente à medida em que percorre um conjunto de dados.

#### .groupby()
##### Agrupa uma ou mais colunas, permitindo a aplicação de operações em grupos.
```
>> df_cachorros.groupby('Cor')['Peso (kg)'].mean()
Cor
Amarelo     60.0
Branco      35.0
Cinza       42.5
Dourado     43.5
...
```

### .pivot_tables()
##### Permite a criação de tabelas dinâmicas, que calculam estatísticas resumidas e agrupadas.
```
>> df_cachorros.pivot_table(values='Peso (kg)', index='Cor')
```
##### Por padrão, o método calcula a média dos valores por agrupamento. Para realizar uma estatística resumida diferente, basta usar o argumento **aggfunc** para definir uma função.
```
>> df_cachorros.pivot_table(values='Peso (kg)', index='Cor', aggfunc=np.median) #Utiliza a mediana de NumPy
```
##### Para agrupar mais de uma variável, acrescenta-se o argumento **columns**.
```
>> df_cachorros.pivot_table(values='Peso (kg)', index='Cor', columns='Raça')
```
##### Para substituir os valores inexistentes NaN (Not a Number) por 0, utiliza-se o argumento **fill_value**.
```
>> df_cachorros.pivot_table(values='Peso (kg)', index='Cor', columns='Raça', fill_value=0)
```
### Métodos de manipulação de índex
#### .set_index()
##### Transforma uma das colunas em índice.
```
>> df_cachorros.set_index('Nome')
```

#### .reset_index()
##### Desfaz e remove o índice criado com .set_index().
```
>> df_cachorros.reset_index()
```
##### Pode-se utilizar o argumento **drop=True** para descartar um índice.
```
>> df_cachorros.reset_index(drop=True)
```

#### loc[]
##### Seleciona um pedaço do dataframe, como o isin.
```
>> df_cachorros[df_cachorros['Nome'],isin(['Max', 'Zoe'])]

#utilizando loc[]
>> df_cachorros.loc[['Max', 'Zoe']]
```
#### .sort_index
##### Ordena os valores dos índexes. 
```
>> df_cachorros.sort_index(level=['Cor', 'Raça'], ascending=True, False)
```
#### obs: slices
##### Após ordenar seus índexes, pode-se utilizar a técnica slicing, que seleciona um intervalo de elementos consecutivos de um dataframe.
```
df_cachorros['Amarelo':'Marrom']
```
##### É possível, ainda, fazer slicing de colunas.
```
df_cachorros[:, 'Nome':'Peso (kg)'] #Os dois pontos selecionam todas as linhas, enquanto o segundo argumento corresponde ao intervalo de colunas a serem selecionadas.
```

## Limpeza de dados
### Métodos de limpeza de dados
#### .drop_duplicates()
##### Remove as linhas duplicadas em um dataframe, criando um novo dataframe sem repetições com base em um ou mais critérios especificados. O argumento **subset** determina a coluna de referência.
```
>> df_cachorros.drop_duplicates(subset='Nome')
```
```
>> sub_raca_nome = df_cachorros.drop_duplicates(subset=['Nome', 'Raça'])
```
#### .value_counts()
##### Exibe uma contagem de valores únicos em uma coluna, retornando a frequência de cada valor. Além de possibilitar compreender a distribuição dos dados, também é possível identificar valores duplicados (além da contagem esperada).
```
>> sub_raca_nome['Raça'].value_counts()
Labrador    2
Beagle      2
Poodle      1
Boxer       1
...
```
##### É possível, ainda, utilizar como argumento **sort=True** para ordenar os valores ou **normalize=True** para retornar a contagem em relação ao total ao invés de números absolutos.
```
>> sub_raca_nome['Raça'].value_counts()
Labrador    0.166667
Beagle      0.166667
Poodle      0.833333
Boxer       0.833333
...
```
##### Além disso, também é possível agrupar os dados por várias colunas e calcular as estatísticas resumidas.
```
>> df_cachorros.groupby(['Cor', 'Raça'])['Peso (kg)'].mean
Cor         Raça
Amarelo     Labrador            60
Branco      Poodle              35
Cinza       Husky               60 
            Shih Tzu            25
Dourado     Golden Retriever    43.5
...
```
