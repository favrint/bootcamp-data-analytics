# NumPy
### Definição
##### O NumPy é uma biblioteca de código aberto do Python voltada para computação científica. Com ela, é possível:
- Processar matrizes e arrays multidimensionais;
- Realizar análises numéricas e estatísticas;
- Trabalhar com álgebra linear;
- Realizar transformada de Fourier;
- Aplicar funções matemáticas, como cálculo de raiz quadrada, exponencial e desvio padrão;
- Gerar números aleatórios

### Importando o NumPy
`import numpy as np`

### Criando um NumPy array
###### Para criar matrizes no Python que possam ser processadas pelo Numpy, utilizamos a estrutura de *arrays*. Para criar um array do zero, podemos utilizar os seguintes comandos:
- **np.zeros()**: retorna uma tupla com valores zero
```
>> np.zeros((3, 2)) #np.zeros((linhas, colunas))

array([[0, 0],
[0, 0],
[0, 0]])
```
- **np.arange()**: retorna um intervalo solicitado
```
>> np.arange(1, 11) #np.arange(início, fim)

array([1,2,3,4,5,6,7,8,9,10])
```
- **np.random.random()**: retorna uma tupla com valores aleatórios
    - **np.random.randint()**: retorna uma tupla com valores inteiros aleatórios 
```
>> np.random.random((3, 3)) #np.random.random((linhas, colunas))

array ([[0.15475415, 0.25418748, 0.15474878],
[0.98412658, 0.67259635, 0.78415692,
[0.32168975, 0.69823541, 0.74589631]]])
```
```
>> np.random.randint(10, 31, size=(1, 3,2)) #np.random.randint (valor mínimo, valor máximo, size=(quantidade, linhas, colunas))

array([[10, 15],
[14, 30],
[21, 26]])
``` 
### Por que usar NumPy ao invés de listas?
- Enquanto arrays convencionais aceitam apenas um tipo de dados, Arrays NumPy aceitam elementos de diferentes tipos;
    - No entanto, em análise de dados, utilizamos sempre apenas um tipo dentro de um mesmo array
- Arrays NumPy ocupam menos espaço na memória;
- Arrays NumPy são estrturas multidimensionais e as listas convencionais são unidimensionais;
- Arrays permitem alocação estática e um comprimento fixo;
- Tipos de dados primitivos podem ser armazenados diretamente em arrays, mas não em listas.

### Array 3D
##### Um array 3D em Python é uma estrutura de dados que armazena elementos em três dimensões. É composto por um array de arrays 2D. Um array 3D pode ser visualizado como várias tabelas com linhas e colunas ligadas, como um cubo.
```
>> arr1_2d = np.array([[1, 2], [3, 4]])
>> arr2_2d = np.array([[5, 6], [7, 8]])
>> arr3_2d = np.array([[9, 10], [11, 12]])

>> arr_3d = np.array([arr1_2d, arr2_2d, arr3_2d])
>> arr_3d

array([[[1, 2],
[3, 4]],

[[5, 6],
[7, 8]],

[[9, 10],
[11, 12]]])
```

### Atributos do array
- **.shape()**: informa quantas linhas e colunas determinado array possui

### Métodos do array
- **.flatten()**: transforma um array multidimensional (com linhas e colunas) em um array unidimensional (apenas uma linha)
- **.reshape()**: transforma o formato de uma coluna, redistribuindo suas linhas e colunas conforme os valores definidos. No entanto, o array precisa ter a mesma quantidade de elementos antes e depois para que o método seja eficaz.
- **.astype()**: converte o tipo de dado de um array

### Index 
###### Em Python, o index é uma função que retorna o índice de um elemento em uma lista. Vale ressaltar que o Python conta a posição de um array a partir do zero, não do 1. É possível selecionar os valores que deseja encontrar em uma lista de diversos modos por meio do index, como nos exemplos abaixo.
- Index em um array de uma dimensão (1D)
```
>> arr_1d = np.array([1,5,7,8])
>> arr_1d[2] #localiza o valor contido na posição 2 do array

7
```

- Index em um array de duas dimensões (2D)
##### Valor único
```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> arr_2d[1, 0] #localiza o valor contido na linha 0 e coluna 1 do array

14
```
##### Linha completa
```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> arr_2d[0] #localiza todos os valores contidos na linha 0

array([10, 15, 71, 41])
```
##### Coluna completa
```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> arr_2d[:, 2] #localiza todos os valores contidos na coluna 2

array([71, 58, 69])
```

- Fatiar (slicing) um array de uma dimensão (1D)
```
>> arr_1d = np.array([1, 5, 7, 8])
>> arr_1d[1:3] #seleciona o intervalo de um array entre as posições 1 e 3 (o último valor antes da posição 3)

array([5, 7])
```

- Fatiar (slicing) um array de duas dimensões (2D)
```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> arr_2d[1:3, 0:2] #seleciona o subconjunto que vai da linha 1 à linha 3 (exclusivo) e da coluna 0 à coluna 2 (exclusivo). Basicamente, isso significa selecionar as linhas 1 e 2 (a segunda e a terceira linhas) e as duas primeiras colunas.

array([[14, 30], 
        [21, 26]])
```

- Ordenar (sorting) um array de duas dimensões (2D)
    - **axis = 0**: ordena os valores de um array *verticalmente*
    - **axis = 1**: ordena os valores de um array *horizontalmente*
```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> np.sort(arr_2d, axis=0)

array([[10, 15, 58, 41],
        [14, 26, 69, 51],
        [21, 30, 71, 63]])
```

```
>> arr_2d = np.array([[10, 15, 71, 41],
                        [14, 30, 58, 63],
                        [21, 26, 69, 51]])
>> np.sort(arr_2d, axis=1)

array([[10, 15, 41, 71],
        [14, 26, 58, 63],
        [21, 26, 51, 69]])
```

- Indexação sofisticada (fancy indexing) e máscara (mask) em arrays de duas dimensões (2D)
```
>> pessoas_id_idade = np.array([[1,22],[2,21], [3,27], [4,26]])
>> pessoas_id_idade[:,1] % 2 == 0 #Questiona se há valores pares nos elementos de todas as linhas da segunda coluna e retorna valores booleanos

array([True, False, False, True])
```
##### Boolean mask
###### Retorna um array de valores booleanos
```
>> arr1 = np.array([1, 2, 3, 4, 5])
>> mask = arr1 % 2 == 0 #Insere a seleção de busca em uma variável própria
>> mask

array([False, True, False, True, False])
```

##### Fancy indexing
###### Ao chamar a variável do array com a máscara criada como argumento, os valores do array que atendem ao comando recebido pela máscara será retornado.
```
>> arr[mask]

array([2, 4])
```
##### np.where()
###### Retorna um array de índices aonde estão localizados os valores correspondentes à condição estipulada.
```
>> cartela_bingo = np.array([[16, 10, 3, 15],
[14, 23, 17, 27],
[6, 19, 3, 1],
[10, 4, 18, 19]])
>> np.where(cartela_bingo % 3 == 0)

(array([0, 0, 1, 2, 2, 3]), array([2, 3, 3, 0, 2, 2]))
```
```
>> pessoas_id_idade = np.array([[1,22],[2,21], [3,27], [4,26]])
>> np.where(pessoas_id_idade[:, 1] % 2 == 0)

(array([0, 3]),)
```
##### Buscar e substituir
```
>> np.where(cartela_bingo % 3 == 0, "", cartela_bingo) #Caso encontre valores que atendam à condição (ser divisível por três), substitua por vazio (""); senão, mantenha como está.

array([['16', '10', '', ''],
['14', '23', '17', ''],
['', '19', '', '1'],
['10', '4', '', '19']], dtype='<U21')
```
##### Concatenação
- Concatenação de linhas
```
>> arrv1 = np.random.randint(10, size=(3, 2))
>> arrv1

array([[7, 6],
        [4, 1],
        [1, 1]])

>> arrv2 = np.array([["Peras", "Morango"]])
>> arrv2

array([['Peras', 'Morango']], dtype='<U7')

>> np.concatenate((arrv1, arrv2)) #Concatena linhas de diferentes arrays de mesma dimensão

array([[7, 6],
        [4, 1],
        [1, 1],
        ['Peras', 'Morango']], dtype='<U21')
```
- Concatenação de colunas
```
>> arrv1

array([[7, 6],
        [4, 1],
        [1, 1]])

>> arro1 = np.array(["Uva", "Abacaxi", "Laranja"]).reshape((3, 1)) #Necessário transformar a matriz em uma dimensão compatível à da matriz que será concatenada
>> arro1

array([['Uva'],
        ['Abacaxi'],
        ['Laranja']], dtype= '<U7')

>> np.concatenate((arrv1, arro1), axis=1) #Concatena os arrays no sentido das colunas (axis=1)

array([['7', '6', 'Uva'],
        ['4', '1', 'Abacaxi'],
        ['1', '1', 'Laranja']], dtype='<U21')
```

##### Deletar com np.delete()
- Exclusão de linhas
```
>> arrv1

array([[7, 6],
        [4, 1],
        [1, 1]])

>> np.delete(arrv1, 1, axis=0) #np.delete(Array, Index da linha que será excluída, Orientação)

array([[7, 6],
        [1, 1]])
```
- Exclusão de colunas
```
>> arrv1

array([[7, 6],
        [4, 1],
        [1, 1]])

>> np.delete(arrv1, 1, axis=1)
array([[7],
        [4],
        [1]])

```

##### Cálculos com Array
###### Tenha como base para os próximos cálculos o seguinte array:
```
>> acidentes

array ([[1, 3, 2],
        [0, 1, 0],
        [2, 1, 4],
        [0, 0, 0],
        [1, 1, 0]])

```
- Somar linhas
```
>> acidentes.sum(axis=0) #Soma todos os valores no sentido vertical
array([4, 6, 6])
```

- Somar colunas
```
>> acidentes.sum(axis=1) #Soma todos os valores no sentido horizontal
array([6, 1, 7, 0, 2])
```

- Mínimos
```
>> acidentes.min() #Encontra o menor valor da matriz, independente da orientação
0
```
```
>> acidentes.min(axis=0) #Encontra o menor valor de cada coluna
array([0, 0, 0])
```

- Máximos
```
>> acidentes.max() #Encontra o maior valor da matriz, independente da orientação
4
```
```
>> acidentes.max(axis=0) #Encontra o maior valor de cada coluna
array([2, 3, 4])
```

- Média
```
>> acidentes.mean() #Encontra a média da matriz
1.0666666666666667
```
```
>> acidentes.mean(axis=1) #Encontra a média de cada linha
array([2., 0.33333333, 2.33333333, 0., 0.66666667])
```
```
>> acidentes.mean(axis=1, keepdims=True) #O método keepdims mantém a dimensão da matriz original
array([[2.], 
        [0.33333333], 
        [2.33333333], 
        [0.], 
        [0.66666667]])
```

- Soma cumulativa
```
>> acidentes.cumsum(axis=0) #Soma o elemento atual com o anterior no sentido vertical
array([[1, 3, 2],
        [1, 4, 2],
        [3, 5, 6],
        [3, 5, 6],
        [4, 6, 6]])
```
```
>> acidentes.cumsum(axis=1) #Soma o elemento atual com o anterior no sentido horizontal
array([[1, 4, 6],
        [0, 1, 1],
        [2, 3, 7],
        [0, 0, 0],
        [1, 2, 2]])
```

##### Operações com vetorização
- Cálculos em todos os elementos de um único array
```
>> arr = np.array([[1, 2], [4, 5]])
>> arr += 3 #Soma 3 a cada elemento da matriz
>> arr

array([[4, 5],
        [7, 8]])
```
```
>> arr2 = np.array([[1, 2], [4, 5]])
>> arr2 * 5 #Multiplica cada elemento da matriz por 5

array([[5, 10],
        [20, 25]])
```
- Calcular dois ou mais arrays distintos
```
>> a = np.array([[1, 2, 3], [4, 5, 6]])
>> b = np.array([[2, 2, 2], [0, 0, 1]])
>> a + b

array([[3, 4, 5],
        [4, 5, 7]])
```
```
>> a = np.array([[1, 2, 3], [4, 5, 6]])
>> b = np.array([[2, 2, 2], [0, 0, 1]])
>> a * b

array([[2, 4, 6],
        [0, 0, 6]])
```
```
>> a = np.array([[1, 2, 3], [4, 5, 6]])
>> a > 3

array([[False, False, False],
        [True, True, True]])
```

##### Vetorizando código (np.vectorize)
###### Transforma as funções regulares do Python em funções vetorizadas, aptas a serem aplicadas em arrays.
```
>> arr = np.array(["Hello", "meininas", "coders"])
>> len(arr) > 5
False 
``` 
###### No exemplo acima, a função *len* não está retornando quais elementos do array possuem mais que 5 caracteres pois tal função não foi vetorizada. Assim, na realidade, a função está retornando falso pois não há mais que 5 elementos na lista. Para analisar cada elemento da lista por meio das funções regulares de Python, será necessário vetorizá-las do seguinte modo:
```
>> vetorizar_len = np.vectorize(len)
>> vetorizar_len(arr) > 5

array([False, True, True])
```

##### Broadcasting (transmissão)
###### Funcionalidade do NumPy de realizar operações entre arrays de dimensões diferentes entre si.
```
>> arr_3x2 = np.array([[1, 2], 
                    [4, 5],
                    [7, 8]])
>> arr_3x1 = np.array([1, 0, -1]).reshape((3, 1))
>> arr_3x1

array([[1],
        [0],
        [-1]])

>> arr_3x2 + arr_3x1 #Neste caso, para cada uma das colunas do primeiro array, foram somados os valores do segundo array (coluna única)

array([[2, 3],
        [4, 5],
        [6, 7]])
```
```
>> arr10 = np.arange(10).reshape((2, 5))
>> arr5 = np.array([0, 1, 2, 3, 4])
>> arr10.shape, arr5.shape

((2, 5), (5,))

>> arr10 + arr5 #Neste caso, para cada uma das linhas do primeiro array, foram somados os valores do segundo array (linha única)
array([[0, 2, 4, 6, 8],
        [5, 7, 9, 11, 13]])
```

### Para saber mais
##### [Material-base das aulas gravadas](https://colab.research.google.com/drive/1By8vdCZ7MeGrLqJfJK3l03iuN-pXM7Xe?usp=sharing)
##### [Material-base da aula de revisão](https://colab.research.google.com/drive/1YjETH6p5u_CDfOOJl9o5Y5ncTV7nbUVi#scrollTo=q_h7b0p0z7Jt)