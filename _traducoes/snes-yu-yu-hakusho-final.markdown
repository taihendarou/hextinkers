---
layout: traducao
title:  "Yu Yu Hakusho Final: Makai Saikyo Retsuden"
console: "SNES"
status: "Em andamento"
download: "https://www.romhacking.net.br/index.php?topic=3436.0"
---

Yu Yu Hakusho Final: Makai Saikyo Retsuden, também conhecido simplesmente como Yu Yu Hakusho Final, é um jogo de luta desenvolvido pela TOSE para o Super Famicom. Lançado em 1995, o jogo é uma sequência de Yu Yu Hakusho 2: Kakutou no Sho e cobre os dois últimos arcos do mangá original.

Como o próprio nome sugere, este foi o último jogo de Yu Yu Hakusho desenvolvido pela TOSE para consoles Nintendo. O título continua ativo entre jogadores competitivos até hoje e possui mecânicas de luta consideradas avançadas para a época e para o Super Nintendo.

![Yu Yu Hakusho Final em português](/img/projeto_yyh-final/yyh-final-projeto.png){:class="centered custom-width-600"}

## Ficha técnica

- **Título original**: Yu Yu Hakusho Final: Makai Saikyo Retsuden
- **Tradução literal**: Yu Yu Hakusho Final: Crônicas dos Mais Fortes do Mundo dos Demônios
- **Título adaptado provisório**: Yu Yu Hakusho Final: Crônicas do Mundo das Trevas
- **Plataforma**: Super Famicom
- **Desenvolvedora**: TOSE
- **Gênero**: Luta
- **Lançamento**: 24 de março de 1995

## Sobre o projeto

Após o lançamento da tradução de [Yu Yu Hakusho 2: Kakutou no Sho](/traducoes/snes-yu-yu-hakusho-kakutou-no-shou.html), este era o caminho natural para a equipe.

O projeto começou em 28 de agosto de 2025 com o disassembly dos principais dados que precisariam ser editados, o desenvolvimento de uma ferramenta de compressão e a extração dos textos. Durante esse trabalho, conhecemos os jogadores do Makai Toshi Brasil, comunidade competitiva que conhece o jogo de cabo a rabo e está dando suporte ao projeto.

- **Início do projeto**: 28 de agosto de 2025
- **Previsão de lançamento**: março de 2027

Essa data é apenas uma previsão: a tradução pode ser lançada antes ou depois, conforme o andamento do trabalho. Por isso, não responderemos perguntas sobre quanto tempo falta para o lançamento.

## Andamento

Atualização de 4 de agosto de 2026:

- **Tradução dos textos**: 100%
- **Revisão dos textos**: 0%
- **ROM hacking**: 60%
- **Gráficos**: 30%
- **Revisão geral e correção de bugs**: 0%

Os percentuais acima são uma forma simplificada de representar o progresso. A conclusão da tradução dos textos não significa que eles já estejam inseridos, revisados e funcionando corretamente em todas as telas do jogo.

## Desafios técnicos

O jogo é inteiramente em japonês e não possui uma fonte ocidental. Além disso, todos os caracteres originais usam tiles de 16 × 16 pixels, uma dimensão inadequada para textos em português. Por isso, a engine de textos está sendo refeita para trabalhar com uma fonte de 8 × 16 pixels.

Essa mudança afeta todas as telas que exibem texto e exige um longo processo de ajuste dos respectivos tilemaps.

Originalmente, cada caractere também ocupa 2 bytes. As rotinas estão sendo reconstruídas para utilizar apenas 1 byte por caractere, liberando espaço suficiente para armazenar todo o texto traduzido sem expandir a ROM. Como essa alteração modifica uma parte fundamental do funcionamento do jogo, diversas telas também precisam ser adaptadas e testadas novamente.

## Equipe

- **Taihen**: ROM hacking, programação
- **Sliter**: Gráficos
- **Kuroi**: Tradução de textos
- **Skeleto**: Tradução de textos

## Acompanhe o projeto

O patch ainda não está disponível. As novidades e futuras atualizações serão publicadas nos canais abaixo:

- [Tópico do projeto no FURT]({{ page.download }}){:target="_blank"}
- [Canal do projeto no Discord](https://discord.com/channels/1421216277858615464/1421229673320546374){:target="_blank"}
