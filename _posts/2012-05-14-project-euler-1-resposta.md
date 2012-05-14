---
layout: post
category: math
tags: [project-euler, answer]
tagline: viu?
title: "Resposta: Project Euler &#35;1 (revisado)"
---
{% include JB/setup %}

_Quem respondeu: [Daniel Presser](https://twitter.com/danielpresser),
                [Victor Arias](http://twitter.com/ariassp) e
                [Rodrigo Vidal](http://twitter.com/rodrigovidal)_

Viu como não era tão fácil?

O problema da solução original é que ela precisava verificar cada número entre
o início e o fim do intervalo executando divisões entre eles. Para 1000 números
o tempo de execução era até razoável, mas quando passava da casa das centenas de
milhões, era preciso encontrar um algoritmo melhor.

A sacada do algoritmo era perceber que a soma dos números divisíveis por 3 tem a 
forma:

```
3 + 6 + 9 + 12 + 15 + ... + 999
```

Que podem se escritos como:

```
3 * (1 + 2 + 3 + 4 + 5 + ... + 333)
```

Isso é a fórmula de uma [PA](http://en.wikipedia.org/wiki/Arithmetic_progression). 
Como o [Victor Arias](http://twitter.com/ariassp) apontou, essa soma tem a forma:

```
3 * 333 * 334 / 2
```

Generalizando:

```
3 * n * (n+1) / 2
```

Perceba que o somatório acontece entre 1 e 333, pois 999/3 = 333. Para o divisor
5, o valor de "n" deverá ser 999/5 = 199. Assim, definimos S como sendo "a soma
de todos os múltiplos de k entre 1 e x"

{% highlight python %}
def S(k, x):
    n = x/k
    return k*n*(n+1)/2

assert S(3, 999) == 166833
assert S(5, 999) == 99500
assert S(3, 999)+S(5, 999) == 266333
{% endhighlight %}

Perceba que se somarmos os múltiplos de 3 e 5 até 999, o valor não é o esperado 
(233168). Isso acontece porque números divisíveis por 3 e 5 ao mesmo tempo são
contados tanto como divisores de 3 como de 5, e seu valor acaba se repedindo na
soma. Para evitar esse problema, basta definir a função ```euler1(limit)``` como:

{% highlight python %}
def euler1(limit):
    return S(3, limit-1) + S(5, limit-1) - S(15, limit-1)

assert euler1(1000) == 233168
assert euler1(1234) == 354858
assert euler1(1000000000) == 233333333166666668
assert euler1(123456789123456789) == 3556368382157191567225525788624704
{% endhighlight %}

Assim, removemos as duplicidades por excluir uma vez da soma os números que são
divisíveis por 3 e 5, i.e., os divisíveis por 15.

