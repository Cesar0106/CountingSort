O algoritmo Couting Sort
======

O Problema
---------

Como já foi visto diversas vezes na disciplina, existem diversos algoritmos de ordenação de vetores, com idéias e eficiências diferentes. Vimos também diversas situações nas quais é preciso saber escolher bem o seu algoritmo de ordenação, considerando diversos fatores. 

Nesse Handout, especificamente, vamos falar sobre o algoritmo Counting Sort.

??? Exercício

Apenas pelo nome do algoritmo, é possível inferir (nem que minimamente) como ele funciona. Você consegue ter uma idéia?

::: Gabarito
É possível inferir que o algoritmo fará alguma espécie de contagem, mais provável ainda que essa contagem seja feita enquanto varre o vetor.
:::

???

O vetor de contagem
---------

Bom, se você respondeu acima que o algoritmo faz uma contagem, você está.... certo!!! Mas talvez não do jeito que imagina. Esse algoritmo, diferentemente dos outros, recebe um *vetor auxiliar*. Isso tudo será explicado mais pra frente. Por ora, saiba que dentro do algoritmo há 2 vetores.

??? Exercício

Qual uma possível desvantagem desse algoritmo dado pelo fato de usar 2 vetores?

::: Gabarito
O Counting Sort possui uma grande desvantagem em questões de memória, devido ao uso de mais de um vetor.
:::

???

Mas como funciona esse *vetor auxiliar* (ou de maneira mais exótica, *vetor de contagem*)? Bom, imagine como uma espécie de "vetor mágico" que faz com que os elementos voltem ao vetor original de maneira ordenada.

```
vetor original
elementos passam pelo vetor auxiliar
voltam ordenados para o original.
```

Passo a passo do algoritmo
---------

O primeiro passo que torna essa "magia" possível é achar o elemento máximo do vetor original. A razão ficará mais clara a partir do próximo passo.

??? Exercício

Tente implementar a idéia acima em C. Lembre-se que a função recebe um vetor de inteiros ```v[]```  e o número de elementos ```n```.
::: Gabarito
``` c
int max = v[0];
  for (int i = 1; i < n; i++) {
    if (v[i] > max)
      max = array[i];
  }
```



Para criar um parágrafo, basta escrever um texto contínuo, sem pular linhas.

Você também pode criar

1. listas;

2. ordenadas,

assim como

* listas;

* não-ordenadas

e imagens. Lembre que todas as imagens devem estar em uma subpasta *img*.

![](logo.png)

Para tabelas, usa-se a [notação do
MultiMarkdown](https://fletcher.github.io/MultiMarkdown-6/syntax/tables.html),
que é muito flexível. Vale a pena abrir esse link para saber todas as
possibilidades.

| coluna a | coluna b |
|----------|----------|
| 1        | 2        |

Ao longo de um texto, você pode usar *itálico*, **negrito**, {red}(vermelho) e
[[tecla]]. Também pode usar uma equação LaTeX: $f(n) \leq g(n)$. Se for muito
grande, você pode isolá-la em um parágrafo.

$$\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} \leq 1$$

Para inserir uma animação, use `md :` seguido do nome de uma pasta onde as
imagens estão. Essa pasta também deve estar em *img*.

:bubble

Você também pode inserir código, inclusive especificando a linguagem.

``` py
def f():
    print('hello world')
```

``` c
void f() {
    printf("hello world\n");
}
```

Se não especificar nenhuma, o código fica com colorização de terminal.

```
hello world
```


!!! Aviso
Este é um exemplo de aviso, entre `md !!!`.
!!!


??? Exercício

Este é um exemplo de exercício, entre `md ???`.

::: Gabarito
Este é um exemplo de gabarito, entre `md :::`.
:::

???
