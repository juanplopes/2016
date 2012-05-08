---
layout: page
title: 2016?
tagline: Como assim?
---
{% include JB/setup %}

Esse site é um experimento baseado no [post homônimo do Dan Shipper](http://danshipper.com/124690091). 
Se você ainda não leu, corre lá.

O objetivo aqui é postar desafios de programação com **impecável irregularidade**, 
cuja solução envolva alguma disciplina clássica de algoritmos, matemática e outras 
coisas insuportáveis da computação.

### Propositalmente, isso não é:

* um blog
* (totalmente) em inglês

***

### Não respondidos:

<ul class="posts">
  {% for post in site.tags['challenge'] %}
    {% if post.solution and post.solution == '*' %}
        <li><strong><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></strong></li>
    {% endif %}
  {% endfor %}
</ul>


***

### Todos:

<ul class="posts">
  {% for post in site.tags['challenge'] %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

