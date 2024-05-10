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

### Assemblers compilados para uso no MacOS

<table class="tabela">
      <tbody><tr>
        <th>Nome</th>
        <th>Descrição</th>
      </tr>
      <tr>
        <td><a href="https://mega.nz/file/NvFx2KDR#WnrjyzFsgHwvu-ZLntAEDEAdqX2tpnC8aTf4ApHKnDY" target="_blank">Bass for MacOS</a></td>
        <td>Assembler Bass compilado para ser utilizado no MacOS</td>
      </tr>
      <tr>
        <td><a href="https://mega.nz/file/tydgQABb#i-YtLuJeBUgeioiW0nk0SQLQsvS1Kp-nwLwcbmeCpJM" target="_blank">Armips for MacOS Arm64</a></td>
        <td>Assembler Armips compilado para ser utilizado no MacOS com processadores Apple M1 e M2</td>
      </tr>
    </tbody>
</table>