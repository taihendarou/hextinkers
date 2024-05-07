---
layout: page
title: "Traduções de Jogos de Videogames para Português"
---

Lista de projetos concluidos (e em andamento) de tradução de jogos de consoles antigos para o português. Você verá detalhes sobre cada projeto, inclusive alguns detalhes técnicos, além do acesso ao patch de tradução para aplicar e jogar, caso já esteja disponível.

A lista a seguir engloba projetos de iniciativa própria ou com uma participação muito ativa na equipe.

<table class="tabela">
	<tr>
	  <th>Jogo</th>
	  <th>Plataforma</th>
	  <th>Status</th>
	</tr>
	{% for traducao in site.traducoes %}
	<tr>
	  <td>
		<a href="{{ traducao.url }}">{{ traducao.title }}</a>
	  </td>
	  <td>{{ traducao.console }}</td>
	  <td>{{ traducao.status }}</td>
	</tr>
	{% endfor %}
</table>

## Colaborações

Colaborações são projetos que pude contribuir em uma ou mais áreas, mas com uma participação mais coadjuvante no todo. Projetos que foram majoritariamente conduzidos por colegas e amigos. Todos os links acima direcionam para postagens externas.

<table class="tabela">
  <tr>
    <th>Jogo</th>
    <th>Plataforma</th>
    <th>Contribuição</th>
  </tr>
  <tr>
    <td><a href="https://patryckpo.com/traducoes/nes/adventure-island-iv/" target="_blank">Adventure Island IV</a></td>
    <td>NES</td>
    <td>Assembly para acentuação</td>
  </tr>
  <tr>
    <td><a href="https://simpleskans.github.io/traducoes/tetsudou_ou.html" target="_blank">Tetsudou Ou: Famicom Boardgame / Rei da Ferrovia</a></td>
    <td>NES</td>
    <td>Assembly e suporte</td>
  </tr>
  <tr>
    <td><a href="https://www.romhacking.net.br/index.php?topic=2701.0" target="_blank">Open Season / O Bicho Vai Pegar</a></td>
    <td>Game Boy Advance</td>
    <td>Gráficos</td>
  </tr>
</table>