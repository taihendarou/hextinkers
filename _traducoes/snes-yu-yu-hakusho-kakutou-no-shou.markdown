---
layout: traducao
title:  "Yu Yu Hakusho 2: Kakuto no Sho"
console: "SNES"
status: "Finalizado"
download: "https://mega.nz/file/83FngIhD#oc3z9280J06qqfuejgA0WcuczfrJtoQv5MTX2eEWdmk"
---

Yu Yu Hakusho 2: Kakutou no Sho é um jogo de luta em estilo 1x1 baseado no clássico anime Yu Yu Hakusho, famoso no Brasil nos anos 90 e início dos anos 2000. O jogo segue a narrativa do anime até o fim do Torneio das Trevas, com lutas um contra um entre os principais personagens da série.

Possui também um modo arcade (MODO TORNEIO) e um multiplayer. O jogo foi relativamente conhecido no Brasil pois estava disponível em várias locadoras na época.

![Yu Yu Hakusho - Kakutou no Shou - Capa](/img/projeto_yyh2/yyh2_capa.jpeg){:class="centered"}

## Ficha técnica
- **Título original**: Yu Yu Hakusho 2: Kakutou no Sho (幽☆遊☆白書2 格闘の章)
- **Título traduzido**: Yu Yu Hakusho 2: The Fighing Chapter
- **Plataforma**: Super Famicom / Super NES
- **Desenvolvedora**: TOSE
- **Publicadora**: Namco
- **Gênero**: Luta / Ação
- **Lançamento**: 10 de junho de 1994

## Sobre a tradução

Todos os textos, menus e gráficos estão traduzidos para o português, com todos os acentos necessários. O jogo foi traduzido diretamente do japonês e agora é possível acompanhar os acontecimentos do MODO HISTÓRIA, além de navegar tranquilamente por todas as opções disponíveis. A escolha de termos e das falas foi, na medida do possível, baseada na dublagem brasileira do anime. As falas do personagem buscaram homenagear esta icônica dublagem brasileira.

Versão: 1.0

Projeto iniciado em 26/11/2023 e finalizado em 15/02/2024.

![Yu Yu Hakusho - Kakutou no Shou em Português 1](/img/projeto_yyh2/yyh2_jp_000_04_01.png){:class="centered"}

# História da Tradução e Detalhes Técnicos

Minha vontade de traduzir este jogo existe desde que comecei a mexer com ROM Hacking, por ser um jogo relativamente conhecido no Brasil, de um anime muito cultuado e que curiosamente não havia ainda tradução nem para o inglês. Assim, enquanto trabalhava em outros projetos, sempre fui sondando e coletando as informações que precisaria para um dia fazer esta tradução.

Ainda antes de iniciar, comecei a ajudar o Dindo em questões técnicas de alguns de seus projetos e com isso aprendi a base que precisava para então iniciar meu primeiro projeto completo de SNES. E claro, este jogo foi o escolhido!

O primeiro desafio foi em relação a fonte. Na fonte original do jogo, nem temos o alfabeto romano além de algumas letras avulsas como A, X, Y e Z. Além disso, a fonte japonesa é 16x16, dimensão que fica horrível para fontes latinas. O lado bom é que a fonte japonesa tem mais de 500 caracteres, o que me deixou com muito espaço livre na ROM, já que o espaço de todos estes tiles foi liberado.

![Yu Yu Hakusho - Kakutou no Shou em Português 1](/img/projeto_yyh2/yyh2_jp_000_04_02.png){:class="centered"}

Então as rotinas de texto do jogo foram reprogramadas para agora exibir uma fonte em tamanho 8x16. Além disso, originalmente o jogo usa uma tabela de 16 bits. Como não precisamos de tudo isso, reprogramei também as rotinas necessárias para que agora a tabela de caracteres seja de 8 bits. O resultado disso é o dobro de espaço disponível na memória para texto. Dessa forma, a ROM não precisou ser expandida e tivemos espaço para alocar absolutamente tudo o que precisávamos.

Como o jogo é inédito em inglês, comecei a compartilhar sobre o projeto no Discord do romhacking.net e assim conheci vervalkon, o qual teve uma contribuição crucial para a velocidade da evolução deste projeto! Ele se mostrou disponível para fazer a logo e outros gráficos, mas além do trabalho artístico, contribuiu com toda a inserção desses elementos.

![Yu Yu Hakusho - Kakutou no Shou em Português 2](/img/projeto_yyh2/yyh2_jp_000_04_07.png){:class="centered"}

Enquanto eu estudava a compressão do jogo, ele rapidamente programou uma tool de decompressão e mapeou a localização de todos os assets (gráficos e tilemaps) do jogo. Isso acelerou muito o meu entendimento da compressão e logo então consegui programar um recompressor. Ele fez uma belíssima logo, editou a abertura do jogo, elementos da tela título e fez as alterações na HUD de batalha para que os nomes dos personagens fiquem romanizados. Agradecimento gigante a vervalkon por toda ajuda e compartilhamento de conhecimento! Agora, vamos trabalhar juntos na versão em inglês deste jogo.

E para finalizar, este projeto me levou a reassistir ao anime, ao menos as partes relevantes, para assim deixar as falas e terminologias dentro do que o público brasileiro está acostumado. Me doeu um pouco na alma escrever "leigan" ao invés de "reigan", mas optei por agir como se estivesse realizando um trabalho oficial e tivesse que seguir o material que já existe no Brasil.

![Yu Yu Hakusho - Kakutou no Shou em Português 3](/img/projeto_yyh2/yyh2_jp_000_04_06.png){:class="centered"}

Muito obrigado a todos dos servidores do Discord que acompanharam, apoiaram, deram sugestões e ajudaram a execução deste projeto ser mais divertida. Obrigado a Jv132 por um ajuste no anti-aliasing da fonte, Denim por ter ajudado a encontrar a tabela de propriedades do scroll do tilemap do menu principal, Joapper por sugestões de fonte e a todos que apoiaram: Dindo, patryckpo, Mumm-Ra, Hyd~, ajkmetiuk, Satty, badnest, Arara, honmaru (que fará versão em espanhol!), Sora Leon e GameRulez. Além da equipe oficial do projeto: vervalkon e Sliter!

## Equipe

- **Taihen**: Tradução e ROM Hacking
- **vervalkon**: Gráficos e ROM Hacking
- **Sliter**: Gráficos

## Informações da ROM para aplicar o patch

- **Nome**: Yu Yu Hakusho 2 - Kakutou no Shou (Japan)
- **Database**: No-Intro: Super Nintendo Entertainment System (v. 20210222-050638)
- **File/ROM SHA-1**: 54198529C9D989B7DBAF767D5185E9557F178292
- **File/ROM CRC32**: EEF45A93

Caso precise de ajuda para entender o que é o patch e como aplicá-lo, clique aqui e leia este tutorial.

## Imagens da Tradução

![Yu Yu Hakusho - Kakutou no Shou em Português 4](/img/projeto_yyh2/yyh2_jp_000_04_03.png){:class="centered"}

![Yu Yu Hakusho - Kakutou no Shou em Português 5](/img/projeto_yyh2/yyh2_jp_000_04_04.png){:class="centered"}

![Yu Yu Hakusho - Kakutou no Shou em Português 6](/img/projeto_yyh2/yyh2_jp_000_04_05.png){:class="centered"}

![Yu Yu Hakusho - Kakutou no Shou em Português 7](/img/projeto_yyh2/yyh2_jp_000_04_08.png){:class="centered"}

## Gameplay completa

<center><iframe src="https://www.youtube.com/embed/xhd3RX5aksQ?si=ppoE0gZR4j2loJD0" width="560" height="315" frameborder="0" class="centered" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></center>

## Download do patch

- **Formato do Patch**: IPS
- **Download do Patch**: [Link do Mega]({{ page.download }}){:target="_blank"} (v1.1)

Versão 1.0 lançada em 14/02/2024
Versão 1.1 lançada em 29/09/2024

Lembre-se que nós disponibilizamos apenas o patch de tradução. Você deverá aplicá-lo em sua ROM, baixada ou adquirida em outro lugar. Clique aqui para saber mais sobre este processo.

## Outros Links

- [Publicação da tradução no FURT](https://www.romhacking.net.br/index.php?topic=2671.0){:target="_blank"}
- [Publicação da tradução no RomHacking.net](https://www.romhacking.net/translations/7223/){:target="_blank"}
- [Publicação da tradução no Fórum Elite dos Quatro](https://e4t.com.br/forum/viewtopic.php?t=53){:target="_blank"}
- [Tópico sobre o projeto no Discord (Servidor SatY Traduções)](https://discord.com/channels/890734572919222352/1178346010876071997){:target="_blank"}
- [Gamefaqs do jogo](https://gamefaqs.gamespot.com/snes/564285-yuu-yuu-hakusho-2-kakutou-no-sho){:target="_blank"}
