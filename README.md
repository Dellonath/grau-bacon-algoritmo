## Algoritmo para encontrar o Grau de Bacon

<p align="center">
  <img src="https://user-images.githubusercontent.com/56659549/159389816-ff02d5db-9ce8-4756-826c-09d88adc8c8c.png" width=500>
</p>

## Descrição

O [Grau de Bacon](https://en.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon#:~:text=The%20game's%20name%20is%20a,Last%20Degree%20of%20Kevin%20Bacon.) entre dois artistas indica a "distância" de atuações entre um ator/atriz fornecido e o ator Kevin Bacon. De forma resumida, Grau de Bacon 1 indica que o ator atuou diretamente com Kevin Bacon, já grau 2 indica que o ator atuou com alguém que atuou com Kevin Bacon, e assim sucessivamente...

## Objetivo

O objetivo é tentar encontrar um algoritmo determinístico capaz de solucionar o problema descrito acima de uma forma suficientemente otimizada. Além disso, após a implementação do algoritmo, tentar descrevê-lo utilizando definições e o rigor matemático (checar no notebook). 

O intuito é demonstrar a habilidade de **abstração**, **compreensão** e **modelagem** do problema através de conjuntos e grafos, assim como demonstrar a utilização de conhecimentos no campo da matemática para traduzir o funcionamento do algoritmo.

## Resumo do algoritmo

Podemos modelar o problema utilizando conjuntos e grafos. O algoritmo, implementado em Python, tenta explorar destes conceitos, utilizando também um conjunto de dados em formato CSV (Comma Separated Values), onde podemos encontrar os dados de artistas, filmes e o eleco das produções cinematográficas. No momento, o algoritmo retorna apenas o Grau de Bacon, uma próxima atualização seria indicar melhor quais os filmes que relacionam os atores e atrizes para chegarem ao Kevin Bacon. Vale ressaltar que o Grau de Bacon retornado está diminuído de uma unidade, ou seja, atores que atuaram junto com Kevin Bacon têm "distância" 0 e não 1 (como descrito na seção anterior). Um detalhe importante é que não precisa ser obrigatoriamente o Kevin Bacon, é possível calcular esta distância entre dois artistas quaisquer. 

De forma resumida, o algoritmo recebe dois atores, ```x``` e ```y``` e verifica se ```y``` já está no conjunto de atores que atuaram com ```x```, se não estiver, é feita uma iteração nos atores que atuaram com ```x``` e adicionados os atores que atuaram com cada elemento do conjunto de ```x```, então é feita novamente a checagem da presença de ```y```.

Abaixo temos o pseudocódigo do algoritmo implementado:

```
Algoritmo gb(x, y):
  Se x = y: 
    retorna 0

  # definindo N-K e N_(k-1)
  N0 = A[x]
  N1 = A[x]

  Para k em 0, 1, 2, ...:
    Se y em N1:
      retorna k
    Para i em N0:
      N1 = N1 + A[i]
    N0 = N1

  retorna 'Não encontrado'
```
