---
layout: page
title: 2016?
tagline: O que tem 2016?
---
{% include JB/setup %}

## O que é?

Isso é um experimento baseado nesse [post do Dan Shipper](http://danshipper.com/124690091).

O objetivo é postar desafios de programação com **impecável irregularidade**, cuja 
solução envolva alguma disciplina clássica de algoritmos, matemática e outras 
coisas insuportáveis da computação.

## O que não é?

* Um blog
* Em inglês

## Desafios

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

