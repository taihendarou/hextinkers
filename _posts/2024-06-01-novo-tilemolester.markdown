---
layout: post
title:  "Nova versão do Tile Molester"
date:   2024-05-26 00:00:00 -0300
---

É isso aí! Saiu uma nova versão do Tile Molester, o clássico editor de tiles feito em Java e que comporta muitas plataformas, inclusive possibilitando a criação de novos codecs gráficos.

Para mim, essa versão é especialmente importante por melhorar aspectos para macOS, meu principal sistema operacional.

Veja a lista de implementações neste release:

- Novos temas. Sistema antigo personalizado removido
- Suporte a escala fracionária
- Suporte a macOS (Barra de Menus movida para o topo, Tema nativo do Ícone do Dock, etc.)
- Novo ícone de aplicação
- Melhorias na UX
- Alternância para modo escuro adicionada
- Edição de cor implementada
- Várias correções e mudanças
- Uso do Maven para construção (PR por devnewton)

Veja como a interface está mais bonita e mais fluida:

{:.text-align-center}
![Novo Tile Molester](/img/misc/molesteiro-de-tiles-.21.png){:custom-width-600}

[Segue link do release para download da versão 0.21](https://github.com/toruzz/TileMolester/releases/tag/v0.21){:target="_blank"}

Lembrando que é um programa anti-usuário leigo para rodar. Precisa dar linha de comando para executar. Faça o seguinte (no macOS):

1- Abra o terminal (cmd + space: Digite `cmd`)

2- Navegue até a pasta do novo Tile Molester com `cd`. No meu caso, acesso com `cd ~/Documents/ROM\ HACKING/-TOOLS/tilemolester-0.21`. Troque de acordo com o seu caminho local.

3- Dentro dessa pasta, temos o tilemolester.jar. Não adianta dar dois cliques para executar. Precisa de linha de comando. Rode: `java -jar tilemolester.jar`

Se quiser mais facilidade, faça o seguinte:

1- Crie um arquivo Tilemolester.sh, com o editor de texto.

2- Dentro dele, coloque os comandos a seguir, atualizando para seus caminhos locais:

<pre>
#!/bin/bash
cd ~/Documents/ROM\ HACKING/-TOOLS/tilemolester-0.21
java -jar tilemolester.jar</pre>

3- Salve as mudanças e deixa aí.

4- Abra a ferramenta própria do macOS chamada Automator. Alique em `Arquivo` -> `Novo`.Selecione `Executar AppleScript`.

5- Na barra de comando que surgiri, digite:
<pre>do shell script "\"/Users/seunomedeusuario/Documents/ROM HACKING/-TOOLS/tilemolester-0.21/TileMolester.sh\""</pre>

Salve dentro da plasta de Aplications / Application.

Pronto, poderá executá-lo digitando Tilemolester no Spotlight.

Não é difícil. É mais trabalhoso do que clicar em ícones que já vem pronto, mas veja isto como o treino para se tornar pica da computação!

Aproveite que o programa ficou bom.

Agora vamos ao **Alcahest**!

Lançado patch 1.2, graças a um texto obscuro, nunca encontrado por nnhum outro grupo de tradução de nenhum idioma. Mas nosso grande colega Kauan Paulo, encontrou e teve a gentileza de avisar!

Muito obrigado, meu brother. Espero que esteja aproveitando os jogos.

Obrigado também a um usuário do fórum romhacking.net.br que encontrou um typo na palavra "Guardões", que deveria ser "Guardões". Agora está correto!

Eu espero não ter uma versão 1.3. Mas se surgirem novos erros, estaremos prontos para corrigir.

[Faça o download aqui na página do projeto do Alcahest](/traducoes/snes-alcahest.html)

É isso aí. Fique agora com um b-side do Iron Maiden para subir o nível da sua mente e de seu ambiente. Acabei de sair um programa social onde rolou karaoke com sertanejo. Tenho que desinfectar minha mente.

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/T5WpPLRrhac?si=zMzyH_cEyUcIeWtN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

{:.text-align-center}
![Iron Maien Dance Skull](/img/misc/iron-maiden-scull-dance.gif)![Iron Maien Dance Skull](/img/misc/iron-maiden-scull-dance.gif)![Iron Maien Dance Skull](/img/misc/iron-maiden-scull-dance.gif)