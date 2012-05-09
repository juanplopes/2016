---
layout: post
category: graphs
tags: [challenge, draft]
solution: *
tagline: simples assim
title: Alô Telefonia e Internet
---
{% include JB/setup %}

Em 2016, a internet no Brasil ainda é ruim.

No final de 2015, a Anatel baixou uma portaria que permite a cada cliente 
insatisfeito sublocar e operar uma parte da malha de telecomunicações no seu estado.
Com isso, os programadores, maiores afetados pela incompetência das operadoras
da época, fundaram operadoras próprias, que rapidamente ganharam o gosto popular.

João também resolveu abrir sua própria operadora: Alô Telefonia e Internet, que
presta serviços de internet para empresas da sua região.

Rapidamente ele percebeu que o recurso mais caro para operação são os cabos, 
que permitem conectar sua rede às dos seus clientes.

Para diminuir custos, a operadora de João não mantém um cabo entre a sua rede e 
cada um dos seus clientes, o que poderia custar caro demais para manter. Na verdade, 
quando possível, ele tenta reaproveitar o caminho já percorrido até um cliente
para chegar a outro resultando numa distância total menor.

<div class="center">
    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/bad.png"/>
        <p>Assim é ruim.</p>
    </div>

    <div class="pic inline">
        <img src="{{ BASE_PATH }}/imgs/alo-internet/good.png"/>
        <p>Assim é melhor.</p>
    </div>
</div>

Com isso, surgiu o problema de decidir quais clientes a Alô irá conectar
para permitir que todos tenham internet, porém utilizando a menor extensão de 
cabo possível. João é um bom programador, e prefere escrever um programa que 
faça isso. Como ele nunca estudou muito sobre algoritmos, ele pediu a sua ajuda.

A única informação que você tem disponível é o nome e posição geográfica de cada
cliente. O objetivo é diminuir a soma total do comprimento dos cabos usados para
conectar esses clientes.

Por exemplo, suponha que você tenha a seguinte lista de clientes e suas posições
geográficas. Para fins práticos, você pode considerar os clientes como pontos
em um plano cartesiano:

{% highlight python %}
clientes = (
    ("Alô", 0.0, 1.0), 
    ("C1",  0.0, 0.0), 
    ("C2",  1.0, 0.0)
)
{% endhighlight %}

Espera-se que a solução seja capaz de retornar uma lista exibindo as conexões
que devem ser feitas entre a Alô e seus clientes, bem como o comprimento do cabo
a ser utilizado em cada conexão. E.g.:

{% highlight python %}
assert conexoes(clientes) == set(
    ("Alô", "C1", 1.0), 
    ("C1",  "C2", 1.0), 
)
{% endhighlight %}

Perceba que pode existir mais de uma solução válida. Para João qualquer uma 
serve, desde que minimize o comprimento total.

_**Resposta será publicada em 16/maio/2012.**_

