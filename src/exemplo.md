O algoritmo Couting Sort
======

O Problema
---------

Como já foi visto diversas vezes na disciplina, existem diversos algoritmos de ordenação de vetores, com idéias e eficiências diferentes. Vimos também diversas situações nas quais é preciso saber escolher bem o seu algoritmo de ordenação, considerando diversos fatores. 

Nesse Handout, especificamente, vamos falar sobre o algoritmo Counting Sort.

!!! Aviso
Nesse Handout, todas implementações de código serão feitas na linguagem C.
!!!

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
:::
???

Até agora, esse Handout nos trouxe muitas informações sem nexo. Chegou a hora delas se conectarem. 

Lembram do tal do *vetor auxiliar*? Então, vamos conhecê-lo agora. Ele será definido no código da seguinte maneira:
``` c
int count[max+1];
```
Sim, esse ```max``` é referente ao valor máximo, achado anteriormente! O motivo disso é que, dentro desse vetor será feita uma contagem com relação aos índices e elementos do original. Ficou confuso? Vamos com calma.

??? Exercício
Implemente um código para inicializar todos valores do vetor ```count``` como 0.
::: Gabarito
``` c
for(int i = 0; i <= max; i++){
    count[i] = 0;
}
???

Excelente. Feito isso, temos agora 2 vetores: o original (que precisa ser ordenado) e o auxiliar (irá ajudar na ordenação). 

```c
para j <- 0 até n
    encontra a contagem total de cada elemento e guarda
    essa contagem no índice j do vetor de contagem.
```

??? Exercício
Simule o pseudocódigo acima para o vetor ```{4,2,4,3,1,4}```.
:::Gabarito
O elemento máximo desse vetor é 4. Por isso, sabemos que o vetor de contagem se iniciará
```c
{0,0,0,0,0} //tamanho do vetor é 5
```
Armazenando a contagem no vetor, é possível perceber que:
```c
0 aparece nenhuma vez
1 aparece uma vez
2 aparece uma vez
3 aparece uma vez
4 aparece três vezes
```
Sendo assim, o vetor de contagem ficará:
```c
{0,1,1,1,3}
```
:::
???

Vamos continuar implementando o nosso código!

???Exercício
Transforme o pseudocódigo lá de cima para um código em C.
:::Gabarito
```c
for (int i = 0; i < n; i++) {
    count[v[i]]++;
  }
```
:::
???

!!!Aviso
Tente entender bem essa sessão. Ela é importante para o resto do Handout.
!!!

Se você entendeu bem a tarefa anterior, a próxima não será muito complexa. Já ouviu falar de [soma cumulativa](https://www.cimm.com.br/portal/verbetes/exibir/1769-soma-cumulativa#:~:text=Defini%C3%A7%C3%A3o%20%2D%20O%20que%20%C3%A9%20Soma,c%C3%A1lculo%2C%20tanto%20positivo%20quanto%20negativo.)? Se sim, excelente, pois é exatamente o que faremos agora.

Caso você não saiba, tudo bem também. Dentro do vetor ```count```, iremos somar todos elementos com a soma de seus anteriores. Sim, parece complexo, mas na verdade é bem simples.

```c
para i <= até max
    encontra a soma cumulativa dos elementos e guarda no 
    próprio vetor.
```

???Exercício
Simule esse passo para o vetor de contagem achado anteriormente.
:::Gabarito
Os nossos 2 vetores até agora são:
```c
v[] = {4,2,4,3,1,4}
count[] = {0,1,1,1,3}
```

Vamos implementar a soma cumulativa para o ```count[]```. 

```
soma do primeiro elemento: 0
soma do segundo elemento: 1
soma do terceiro elemento: 2
soma do quarto elemento: 3
soma do quinto elemento: 6
```

Logo, os vetores ficariam da seguinte maneira:
```c
v[] = {4,2,4,3,1,4}
count[] = {0,1,2,3,6}
```
:::
???

???Exercício
Implemente o pseudocódigo acima em C.
:::Gabarito
```c
for(int i=0; i <= max;i++){
    count[i] += count[i-1];
}
```
:::
???

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
