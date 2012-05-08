---
layout: post
category: math
tags: [project-euler, challenge]
solution: *
tagline: não é tão fácil
title: Project Euler &#35;1 (revisado)
---
{% include JB/setup %}

O [Project Euler](http://projecteuler.net/) ganhou muita importância ultimamente.
É possível encontrar centenas (se não milhares) de posts em blogs e repositórios
do github com soluções.

Aparentemente o problema mais famoso é o [primeiro](http://projecteuler.net/problem=1), 
que pede a soma de todos os números divisíveis por 3 ou 5 menores que 1000. Uma 
solução simples (e eficaz) em python pareceria com:

{% highlight python %}
def euler1(limit):
    answer=0
    for i in range(limit):
        if i%3==0 or i%5==0:
            answer+=i
    return answer

print euler1(1000)
{% endhighlight %}

Essa é uma solução válida para esse problema. Funciona muito bem até 1000. O 
problema é que ela não escala tão bem. Executar ```euler1(1000000000)``` 
demoraria tempo suficiente para desistir. 

Esse é o problema. Desenvolva uma solução que rode em tempo satisfatório para 
valores bem maiores que 1000. Não há limite esperado. Qual o máximo que a sua
solução resolveria em, digamos, menos de 1 minuto?

Seguem alguns casos de teste com alguns valores grandes:

{% highlight python %}
assert euler1(1000) == 233168
assert euler1(1234) == 354858
assert euler1(1000000000) == 233333333166666668
assert euler1(123456789123456789) == 3556368382157191567225525788624704
{% endhighlight %}

_**Resposta será publicada em 14/maio/2012.**_

