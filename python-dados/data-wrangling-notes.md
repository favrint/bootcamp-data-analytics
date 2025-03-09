# Data Wrangling no Python
[Colab](https://colab.research.google.com/drive/1NtKs9Wm7dH3QAIAS7WphVLKky09pv9g0?usp=sharing)
## Definição
##### Processo de transformação de dados brutos em dados possíveis de serem analisados mais facilmente.
##### São as aplicações mais comuns de limpeza de dados:
- Remover colunas e linhas de um DataFrame
- Mudar um índice
- Remover dados duplicados
##### São estratégias possíveis para lidar com dados ausentes
- Identificar os dados ausentes
    - .isna()
- Remover os dados ausentes, se a quantidade for pequena e não comprometer a análise
- Preencher os dados ausentes com informações que sejam relevantes à análise ("Dado desconhecido","Não informado" etc)
    - .fillna()
- Utilizar imputação estatística, preenchendo valores ausentes com base em modelos estatísticos

## Transformação de dados
1. Tratamento de valores ausentes
2. Codificação de variáveis categóricas
3. Normalização ou padronização dos dados
4. Conversão do tipo dos dados
5. Remoção de dados duplicados
6. Agregação de dados
7. Criação de novas variáveis (feature engineering)
8. Divisão de dados
9. Renomeação de colunas
10. Mudança do formato do DataFrame