---
layout: page
title: "Arquivo de Atualizações"
---

Confira aqui todas as notícias já publicas no site.

<ul>
{%- assign date_format = site.minima.date_format | default: "%d/%m/%Y" -%}	
{% for post in site.posts %}
<li><a href="{{ post.url }}">{{ post.date | date: date_format }} - {{ post.title }}</a></li>
{% endfor %}
</ul>
<a href="/"><img src="{{ "/img/misc/voltar_para_noticias.png" | relative_url }}" alt="Voltar aos tutoriais" class="centered"/></a>
