---
layout: page
title: "Ferramentas para ROM Hacking e Tradução de Jogos"
---

Aqui disponibilizo ferramentas desenvolvidas por mim para suprir demandas que foram surgindo durante os projetos, ou para auxiliar outros colegas ROM hackers. Use à vontade em seus projetos.

<table class="tabela">
	<tr>
	  <th>Ferramenta</th>
	  <th>Descrição</th>
	</tr>
	{% for ferramenta in site.ferramentas %}
	<tr>
	  <td>
		<a href="{{ ferramenta.url }}">{{ ferramenta.title }}</a>
	  </td>
	  <td>{{ ferramenta.description }}</td>
	</tr>
	{% endfor %}
</table>