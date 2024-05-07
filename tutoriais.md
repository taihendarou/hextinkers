---
layout: page
title: "Tutoriais de ROM Hacking e Tradução de Jogos"
---

Tutoriais para ajudá-lo a aprender a traduzir jogos de consoles para o português. Trago aqui tutoriais ensinando a base teórica necessária para entrar no mundo do ROM Hacking, além de uma série de tutoriais fazendo pequenas modificações no jogo Super Mario Bros.

**Base teórica para ROM Hacking**

{% assign sorted_tutoriais = site.tutoriais | sort:'order' %}{% for tutorial in sorted_tutoriais %}{% if tutorial.path contains 'base-teorica' %}
- [{{ tutorial.title }}]({{ tutorial.url }}){% endif %}{% endfor %}

**Aprenda ROM Hacking com Super Mario Bros. de NES**

{% assign sorted_tutoriais = site.tutoriais | sort:'order' %}{% for tutorial in sorted_tutoriais %}{% if tutorial.path contains 'super-mario-bros' %}
- [{{ tutorial.title }}]({{ tutorial.url }}){% endif %}{% endfor %}

**Tutoriais diversos de ROM Hacking e tradução de jogos**

{% assign sorted_tutoriais = site.tutoriais | sort:'order' %}{% for tutorial in sorted_tutoriais %}{% if tutorial.path contains 'diversos' %}
- [{{ tutorial.title }}]({{ tutorial.url }}){% endif %}{% endfor %}