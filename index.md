---
layout: page
title: 2016?
tagline: O que é?
---
{% include JB/setup %}

Esse site é um experimento baseado no [post do Dan Shipper](http://danshipper.com/124690091).

O objetivo é postar desafios de programação com **impecável irregularidade**, cuja 
solução envolva alguma disciplina clássica de algoritmos, matemática e outras 
coisas insuportáveis da computação.

### O que não é?

* um blog
* (totalmente) em inglês

### Desafios

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

