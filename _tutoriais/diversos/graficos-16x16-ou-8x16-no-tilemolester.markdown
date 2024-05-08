---
layout: page
title:  "Visualização de gráficos 16x16 (ou 8x16) no TileMolester"
---

Frequentemente, ao trabalhar com gráficos de jogos, nos deparamos com a exibição desordenada desses tiles na VRAM e nos editores de tiles, como TileMolester (foco deste tutorial). Isto porque muitas vezes os gráficos foram projetados para serem visualizados em blocos maiores, de 16x16 ou 8x16 pixels. Acompanhe o guia abaixo para ver como visualizar em 16x16 (ou 8x16) no TileMolester.

Imagine que temos a seguinte tela do jogo para trabalhar:

![Image](/img/tutorial_tilemolester16x16/tm16x16_01.png){:class="custom-width-300 centered"}

Ao visualizar a VRAM, os tiles estão bagunçados conforme abaixo:

![Image](/img/tutorial_tilemolester16x16/tm16x16_02.png){:class="custom-width-300 centered"}

Sabendo que a maior parte das imagens são 16x16, podemos usar uma opção do emulador para visualizar de forma mais amigável. Se estiver no MESEN, vá em Tile Layout e escolha 16x16 (Same Line).

![Image](/img/tutorial_tilemolester16x16/tm16x16_03.png){:class="custom-width-600 centered"}

Ficou melhor, né? Agora, após extrair este tileset para um arquivo binário isolado e abri-lo no TileMolester, estará tudo bagunçado:

![Image](/img/tutorial_tilemolester16x16/tm16x16_04.png){:class="custom-width-300 centered"}

E agora? O Tilemolester não tem uma opção de visuazação 16x16 fácil de achar igual ao emulador. Mas precisamos dele para editar os gráficos. O que fazer?

Clique no ícone 'Decrease Width' várias vezes até a imagem ficar com 1 ou 2 colunas, o que for necessário para visualizar bem as imagens em forma de coluna.

Veja como ficou:

![Image](/img/tutorial_tilemolester16x16/tm16x16_05.png){:class="centered"}

Só isso já ajudaria muito. Se for uma fonte, por exemplo, dá para editar na vertical, mesmo que seja um pouco desconfortável.

Mas dá para melhorar!

Acesse 'View' -> 'Block Sizes' e desmarque a opção 'Full Canvas'. Agora, segure Shift apertado e pressione a tecla da seta direcional para a direita várias vezes até a imagem se abrir por completo. Veja a sequência completa no gif a seguir:

![Image](/img/tutorial_tilemolester16x16/tm16x16.gif){:class="custom-width-600 centered"}

O mesmo procedimento pode ser feito para visualizar gráficos (normalmente encontrará isso em fontes) que sejam 8x16.