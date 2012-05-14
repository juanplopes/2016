---
layout: post
category: string-matching
tags: [challenge]
solution: *
tagline: não é tão fácil
title: Plágio Literário
---
{% include JB/setup %}

A cena literária em 2016 cresceu assustadoramente. Os livros técnicos sobre programação
são os mais vendidos. Provavelmente reflexo do estouro da bolha de tecnologia, 
que deixou muitos programadores desempregados.

Com o crescimento da venda de livros, cresceram também os casos de plágio. Muitos
autores sofriam com seus livros sendo copiados e revendidos como novos livros.

Os plagiadores eram espertos e, para tentar evitar as denúncias de plágio, modificavam
um pouco o texto original, adicionando, removendo e trocando algumas palvras.
Por exemplo, uma frase que originalmente era:

```
Para seguir um modelo em cascata, o progresso de uma fase para a próxima se dá 
de uma forma puramente sequencial.
```

pode tornar-se

```
Para obedecer um modelo em cascata, a mudança de uma fase para outra se dá de 
forma completamente sequencial.
```

Basta modificar 5 palavras (seguir -> obedecer, o -> a, progresso -> mudança, 
próxima -> outra, puramente -> completamente) e remover 2 (a, uma). Então, de
21 palavras originais, com 7 mudanças é possível transformar um texto no outro.

Para esse problema, define-se "palavra" qualquer sequencia contígua de letras do
alfabeto.

Então, dados dois trechos de texto, é preciso verificar o menor número de edições
(inserções, remoções e alterações de palavras) para transformar um texto no outro.

Exemplos:

{% highlight python %}
assert plagio(u"""
Para seguir   um modelo em cascata, o progresso de uma fase para a próxima se dá 
de uma forma puramente     sequencial.
""", u"""
Para obedecer um modelo em cascata, a mudança   de uma fase para   outra   se dá 
de     forma completamente sequencial.
""") == 7

assert plagio(u"""
Para seguir   um modelo em cascata, o progresso de uma fase para a próxima se dá 
de uma forma puramente     sequencial.
""", u"""
Bata as claras em neve, misture as gemas e o açúcar e torne a bater.
Depois, misture a farinha e o suco de laranja. Por último acrescente o fermento.
""") == 26
{% endhighlight %}

_**Resposta será publicada em 21/maio/2012.**_

