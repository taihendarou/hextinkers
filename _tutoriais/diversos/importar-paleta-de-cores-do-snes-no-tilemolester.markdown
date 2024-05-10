---
layout: tutorial
title:  "Importar paleta do SNES para o TileMolester"
---

Neste tutorial, você aprenderá a importar para o TileMolester a mesma paleta de cores que está sendo usada pelo jogo no gráfico que você deseja editar. Para isso, você deverá usar o emulador Mesen.

Usaremos como exemplo o jogo Super Adventure Island II, no qual podemos encontrar estes gráficos referente as placas que nomeiam as ilhas do jogo. Estes gráficos estão no endereço $08a000 e podem ser visualizados com o codec "4bpp planar composite".

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette1.png){:class="custom-width-600 centered"}

Queremos carregar a mesma paleta de cores a qual visualizamos este gráfico no jogo, conforme imagem abaixo.

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette2.png){:class="centered"}

Com o jogo aberto em uma área em que o gráfico aparece, vá em Debug -> Tile Viewer e encontre os tiles do gráfico em questão. Certifique-se de procurar em todas as camadas e testar as várias codificações (2bpp, 4bpp etc), até encontrá-lo.

Navegue pelas paletas na coluna da esquerda até encontrar a paleta que está sendo utilizada no gráfico. Conforme vídeo abaixo, sabemos que estas placas utilizam a ante-penúltima paleta.

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette1.gif){:class="centered"}

Agora, vá em Debug -> Memory Viewer para abrir o editor hexadecimal do emulador. Em Memory Type, escolha CG RAM (Palette). Assim, você visualizará os valores referentes a todas aquelas paletas que visualizamos na tela anterior.

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette3.png){:class="centered"}

Agora, selecione todos estes valores e copie com Ctrl + C. Abra seu editor hexadecimal favorito (aqui no exemplo, utilizei o HxD), crie um novo arquivo e cole estes valores. Salve o arquivo com qualquer nome, com a extensão .smc. No exemplo abaixo, salvei como sai2_paleta.smc.

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette4.png){:class="custom-width-600 centered"}

Com o arquivo criado, volte ao TileMolester. Acesse o menu **Palette -> Import from -> Another file** e escolha o arquivo que salvamos.

Pronto! Todas aquelas paletas estão carregadas no TileMolester. Navegue por elas clicando nas setas ao lado das cores na barra inferior até chegar ao conjunto de cores desejados, o qual já sabemos que é o anti-penúltimo da lista.

![Image](/img/tutorial_tilemolester_paleta_snes/tilemolester_palette2.gif){:class="centered"}
