---
layout: post
category: graphs
tags: [answer]
tagline: oi?
title: "Resposta: Alô Telefonia e Internet"
---
{% include JB/setup %}

_Quem respondeu: [André Lima](https://twitter.com/andlima)_

Felizmente para a Alô Telefonia e Internet, o problema de conectar todos os
clientes usando o mínimo de cabo pode ser modelado como um problema clássico da
área de grafos.

O problema questiona: dado um grafo (nós e arestas), qual a soma mínima do peso
de arestas que permite ligar todos os nós do grafo?

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/classic-question.png"/>
        <p>Grafo original.</p>
    </div>

    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/classic-answer.png"/>
        <p>Uma possivel solução.</p>
    </div>
</div>

Esse problema é conhecido como [Árvore Geradora Mínima](http://en.wikipedia.org/wiki/Minimum_spanning_tree),
ou MST para os íntimos (de Minimum Spanning Tree).

Como o nome sugere, a primeira coisa que podemos inferir sobre a solução é que 
o grafo resultante é uma árvore, isto é, não poderá conter ciclos. Podemos 
garantir isso porque caso haja qualquer ciclo, a eliminação de uma das arestas 
não iria afetar a conectividade do grafo, e geraria uma resposta com soma de 
pesos menor.

Existem dois algoritmos clássicos para a solução deste problema. Um deles,
conhecido como [algoritmo de Kruskal](http://en.wikipedia.org/wiki/Kruskal's_algorithm)
foi implementado pelo leitor [André Lima](https://twitter.com/#!/andlima). A
[solução dele](https://gist.github.com/2816407) está bem concisa e vale ser estudada.

Irei apresentar aqui o outro algoritmo, conhecido como [algoritmo de Prim](http://en.wikipedia.org/wiki/Prim's_algorithm).

É um algoritmo guloso, que parte de um nó arbitrário e tenta sempre encontrar a
menor aresta que alcance um novo nó, isto é, que não crie ciclos.

O algoritmo começa escolhendo um nó arbitrário.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-1.png"/>
    </div>
</div>

Então escolhemos a menor aresta que liga algum nó já escolhido a algum nó
ainda não escolhido.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-2.png"/>
    </div>
</div>

Mesma coisa para o terceiro nó.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-3.png"/>
    </div>
</div>

E o quarto. Perceba que foi escolhida a menor aresta (3).

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-4.png"/>
    </div>
</div>

Ignoramos a próxima menor aresta (5), pois ela iria introduzir um ciclo se 
adicionada.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-5.png"/>
    </div>
</div>

Então escolhemos a quarta aresta (6) e o algoritmo termina, pois todos os nós
foram alcançados.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/prim-6.png"/>
    </div>
</div>

Esse algoritmo foi desenvolvido por [Robert Prim](http://en.wikipedia.org/wiki/Robert_C._Prim),
e depois por [Edsger Dijkstra](http://en.wikipedia.org/wiki/Edsger_Dijkstra).
É possível perceber grande semelhança entre esse algoritmo e o famoso 
[Dijkstra's Algorithm](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)

O código é relativamente simples:

{% highlight python %}
# -*- coding: utf-8 -*-
from math import sqrt

def distancia(c1, c2):
    return sqrt((c1[1]-c2[1])**2 + (c1[2]-c2[2])**2)
    
def conexoes(clientes):
    #grafo com todas as distâncias possíveis para todos os pares de clientes
    G = [[distancia(a,b) for a in clientes] for b in clientes]
    n = len(clientes)

    visitado = [False] * n
    pai = [0] * n

    #escolhido o nó de índice 0 como nó inicial
    opcoes = G[0]
    visitado[0] = True
    
    for k in range(n-1):
        #encontra a menor opção de aresta (w) e vértice de destino (v)
        w, v = min([(opcoes[i], i) for i in range(n) if not visitado[i]])

        #avisa que um nó foi escolhido definitivamente
        yield (clientes[pai[v]][0], clientes[v][0], w)                

        #marca v como visitado e atualiza as menores opções
        visitado[v] = True
        
        for i in range(n):
            if G[v][i] < opcoes[i]:
                opcoes[i] = G[v][i]
                pai[i] = v
                
def soma_conexoes(clientes):
    return reduce(lambda x,y: x+y[2], conexoes(clientes), 0.0)
{% endhighlight %}



